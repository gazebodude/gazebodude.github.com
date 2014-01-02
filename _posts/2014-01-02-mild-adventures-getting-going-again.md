---
layout: post
title: Mild Adventures Getting Going Again
date: 2014-01-02 23:53:00
---

So it wasn't entirely straightforward getting this blog back up. I'm building this site using [Jekyll](http://jekyllrb.com/) and hosting using [Github pages](http://pages.github.com/) which provides quite a nice platform for what I want to do. But it has been a couple of months since I touched this thing. So I finished a lot of my fiddling, building all the time on my local machine using the old setup, and when I was happy with the design of the site I did a push and merge and hey presto - Github emails me and tells me Jekyll cannot build the site (though it doesn't give the actual error messages in the email; Github guys: that would be a nice feature!).

Right. I probably need to update. `gem update` Nope... nothing to update. Actually that seems weird, but I go with it. Make sure everything goes through:

{% highlight bash %}
 rake clean
 rake
 jekyll build --safe --trace
 jekyll serve
{% endhighlight %}

All clean. No errors, no problems with the pages. Okie doke. Check out the troubleshooting doc. Ah, Github says to use their new github-pages gem instead of the old style roll-your-own Gemfile. No problem. [Update my Gemfile and push](https://github.com/gazebodude/gazebodude.github.com/commit/e7f55dfe450ef85197708573bdb4a9231b74c6db). Another abstruse error email from Github. Okay. Try rebuilding locally again...

{% highlight bash %}
 bundle install
{% endhighlight %}

Wait, what? I don't have bundler? I swear to God I remember using it on this very machine that I've been using for years. Shit.

{% highlight bash %}
 gem install bundler
{% endhighlight %}

... times out ...

{% highlight bash %}
 gem install github-pages
{% endhighlight %}

gives me:

{% highlight bash %}
Unable to download data from https://rubygems.org/
- SSL_connect returned=1 errno=0 state=SSLv3 read 
server certificate B: certificate verify failed 
{% endhighlight %}

Okay, it's worse than I thought. Just to check... yes, rubygems.org pings ok. Ummm....

So as it turns out this is an old bug in rubygems v2.0.x that has to do with the certificate signing, and as a result it always tells you that there are no updates to install when in fact you are several versions behind! That means for one you can't use rubygems to update itself to a working version! So I clone the rubygems repo and install manually, then run the updater and whoah there are a lot of updates to download...

After waiting a *while* for the updates and bundler to install I do:

{% highlight bash %}
 bundle install
{% endhighlight %}

{% highlight bash %}
ERROR:  Could not find a valid gem
'githup-pages' (>= 0) in any repository
{% endhighlight %}

What, another bug?! Oh wait no, just a typo, my bad. Fix that, run bundler, then rebuild the site and hopefully see what were the error messages that Github should have been telling me already...

{% highlight bash %}
maruku/input/parse_doc.rb:8:in 'sub':
incompatible encoding regexp match
(UTF-8 regexp with CP850 string)
(Encoding::CompatibilityError)
Generating...
Maruku#to_s is deprecated and will be removed
or changed in a near-future version of Maruku.
{% endhighlight %}

Not terribly helpful. As it turns out some unusual code page characters snuck in when I copied and pasted ages ago for one of my gospel of Matthew posts, and one of the updates to Maruku must have made it choke on that whereas it worked fine before. Okay... [Fix all that](https://github.com/gazebodude/gazebodude.github.com/commit/b196c3806a17cfb7e06f5d6070ef115eb26f9721) and woohoo! It builds just fine. Wait, no... there is no CSS. Dammit!

Is this a file path issue? Cause I had something similar earlier when I was trying to test things earlier without `jekyll serve`. Check how the CSS files are getting served up... nope it goes to the 404 page.

Ohh, right! Jekyll doesn't automatically build the SASS, it just does the templating, but I haven't added the stylesheets to the repo (I try not to track build targets, only sources). Derp. You see, I set up the rake tasks to do the builds months ago and I've been using `rake` to build the site ever since for testing. In the intervening time *I forgot how the software actually worked*. Pro tip: don't do that. So okie dokie: [fixed that stupid mistake](https://github.com/gazebodude/gazebodude.github.com/commit/76a385cd54e6bba51ca10aed39c2e1539727737a) and **now** it works.

It took me three commits to master *after* merging the already tested dev branch in order to get the site to render properly.

Yet I'm still quite happy the Ruby-Jekyll-SASS-Compass-Coffeescript framework. *When it's working* it's a dream!

By the way, I made this blog in [VIM](http://www.vim.org/).
