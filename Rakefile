require "rubygems"
require "bundler/setup"
require "jekyll"

ENV["JEKYLL_ENV"] = "production"

desc "Generate blog files"
task :generate do
  # Generate the site files into the _site directory
  Jekyll::Site.new(Jekyll.configuration({
    "source"      => ".",
    "destination" => "_site"
  })).process
end

desc "Generate and publish blog to GitHub Pages"
task :publish => [:generate] do
  # Ensure that all changes in the main project directory are committed and pushed
  system "git add ."
  message = "Site updated at #{Time.now.utc}"
  system "git commit -m #{message.inspect}"

  # Push the changes to the source branch on GitHub
  system "git push origin source"
end
