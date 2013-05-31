task :default => :buildsite
task :clean => [:cleanstyles, :cleanbuild]

task :cleanstyles do
  puts "Cleaning up styles"
  sh "compass clean"
end

task :styles do
  puts "Compiling styles"
  sh "compass compile"
end

task :cleanbuild do
  puts "Cleaning build directory"
  sh "rm -rf _site/\*"
end

task :buildsite => :styles do
  puts "Building site"
  sh "jekyll build"
end