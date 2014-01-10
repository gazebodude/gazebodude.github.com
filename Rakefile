require 'yaml'

desc "Build site (same as rake buildsite)"
task :default => :buildsite

desc "Clean styles and site build directory"
task :clean => [:cleanstyles, :cleanbuild]

desc "Remove stylesheets and Sass caches"
task :cleanstyles do
  puts "Cleaning up styles"
  sh "compass clean"
end

desc "Compile Sass styles to CSS"
task :styles do
  puts "Compiling styles"
  sh "compass compile"
end

desc "Clear site build directory"
task :cleanbuild do
  puts "Cleaning build directory"
  sh "rm -rf _site/\*"
end

desc "Build site"
task :buildsite => :styles do
  puts "Building site"
  sh "jekyll build"
end

desc "Create a draft"
task :createdraft, [:title] do | t, args |
  file_prefix = '_drafts'
  if /[[:word:]]/ =~ args.title
    puts "Attempting to create draft titled `#{args.title}`."

    file_name = args.title
    file_name = File.join(file_prefix,
                  file_name.gsub(/[^[:word:]]/, '_').downcase + ".md")
    puts "The file name is `#{file_name}`."

    if File.exists?(file_name)
      puts "#{file_name} already exists! Aborting."
      exit(-1)
    end

    front_matter = { 'layout' => 'post',
                     'title'  => args.title,
                   }
    front_matter_str = front_matter.to_yaml + "---\n"

    File.open(file_name, 'w') do |file|
      file.write front_matter_str
    end
  else
    puts "Call with a string argument as the post title, i.e."
    puts
    puts "$ rake createdraft['my post title']"
    puts
    puts "The title must have at least one word character in it."
  end
end
