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