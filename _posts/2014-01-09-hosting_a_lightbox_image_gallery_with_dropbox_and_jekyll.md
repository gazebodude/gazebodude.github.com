---
layout: post
title: Hosting a Lightbox image gallery with Dropbox and Jekyll
date: 2014-01-09 21:44:00
---

If you look at [my recent post](/2014/01/09/trip_to_the_roma_street_parklands.html) you will see a gallery of image thumbnails, and if you click on any one it brings up a Lightbox gallery of full size images (actually greatly reduced from the RAW images I shoot, but nevertheless...) which are hosted in the cloud by Dropbox. How does this work?

If you search the web you'll find dozens of tutorials on how to use Dropbox's native image gallery feature to share photos. It is an ideal platform for sharing photos simply. You just save your image files in a Dropbox folder, right click (or use the web interface) and click "Share Dropbox link" and follow directions. You're given a link to give friends & family and, by following it, they are taken to a gallery of your images. Easy. Plus Dropbox is a more reliable content distribution network than any other thing you are likely to cobble together.

That is all well and good if you are happy with going to another site to look at the images. What if you want to have the gallery on your own page, like in the post I talked about earlier? Then you need the URLs Dropbox creates for your full size images. Unfortunately I haven't found any slick way of getting these since Dropbox hides them behind a few layers of javascript and redirection. The easiest thing I've found is to go to the Dropbox gallery, click an image thumbnail to go to its full size display page (still not the actual image), then right click on the image, right click on the context menu item "View original..." and select "Copy link location". This will give you something like:

`https://dl.dropboxusercontent.com/sh/4rvhm5ibn32tv26/zaySx7hDtN/Garden_14.JPG?token_hash=<a bunch of junk>`

The "?token_hash=`<a bunch of junk>`" is unneeded. Delete it. The URL up to the image file format (in this case ".JPG") is all you need. CASE MATTERS too! If you repeat this procedure for every image in your gallery (sorry - I said I don't know a better way. Please tell me if you do!) you'll find that the URL has the general form

`https://dl.dropboxusercontent.com/sh/<mangled folder name>/<mangled file name>/<file name of image that you uploaded>?token_hash=<a bunch of junk>`

Dropbox not only mangles the folder name, but every file name individually within the folder (presumably to prevent automated downloading with a utility like `curl`). We have to get these URLs into a useful bit of markup of the kind that Lightbox expects, something like this:

{% highlight html %}
<div>
  <a href="full size image URL"
     data-lightbox="gallery name"
     title="description">
    <img src="thumbnail URL" alt="image name"/>
  </a>
</div>
{% endhighlight %}

Of course, we give all the elements semantic classes for CSS markup. Let's give the div a class of `gallery-thumbnail-container` and the img tags the class `gallery-thumbnail` with styles something like this (forgive me for this awfulness):

{% highlight css %}
img.gallery-thumbnail {
  width: 100px;
  float: left;
}
div.gallery-thumbnail-container {
  width: 100px;
  height: 150px;
  float: left;
  color: #ffffff;
  margin: 3px;
}
{% endhighlight %}

Lightbox uses the data-lightbox and title attributes to render the nice javascript gallery. You need to make sure you have Lightbox installed and have edited the filepaths in the CSS to refer to the right places.

We could hard code all of the markup by copying and pasting, but that is horrible and error prone. We need a nice DRY (="don't repeat yourself") programmatic way of generating the markup. Since we are using Jekyll, which uses the Liquid templating engine (unfortunately not full Ruby), this is straightforwad. First we add some useful variables to the YAML frontmatter:

{% highlight yaml %}
gallery-word: Garden
dropbox-folder-url: <dropbox url>/4rvhm5ibn32tv26
thumbnail-folder-url: /images/garden_gallery_thumbs
image-urls:
  "01": {url: buEsnzqEgN, desc: "" }
  "02": {url: 41bJcuPdZd, desc: "(Taken by my wife)" }
      .
      .
      .
     etc.
{% endhighlight %}

These variables are accessible via `page.gallery-word` etc. The `image-urls` hash has the image number (as a string) as the key, and a hash containing the mangled file name and a description string (which can be blank) as the value. We use these in the body of the post to fill out the markup. The resulting code is a little messy looking, but it can be used quite easily in other posts. 

{% gist 8334629 %}

All we need to do is set up the right folders and YAML front matter. This can even be put into a partial `_includes\gallery.html` and simply include it in the post with {% raw %}`{% include gallery.html %}`{% endraw %}. All of the hard work is getting the file URLs into the YAML.

See [the source for the gallery post](https://github.com/gazebodude/gazebodude.github.com/blob/master/_posts/2014-01-09-trip_to_the_roma_street_parklands.md) for a complete example and [the gallery partial](https://github.com/gazebodude/gazebodude.github.com/blob/master/_includes/gallery.html) for the guts.
