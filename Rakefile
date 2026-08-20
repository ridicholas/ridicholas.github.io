# From: https://github.com/ainc/awesomeinc2013/blob/master/Rakefile 

require "rubygems"
require "tmpdir"

require "bundler/setup"
require "jekyll"

ENV["JEKYLL_ENV"] = "production"

desc "Generate blog files"
task :generate do
  Jekyll::Site.new(Jekyll.configuration({
    "source"      => ".",
    "destination" => "_site"
  })).process
end


desc "Generate and publish blog to gh-pages"
task :publish => [:generate] do
  # Ensure we're operating within the `_site` directory
  Dir.chdir "_site" do
    # Check if the .git directory exists; if not, initialize it
    unless File.exist?(".git")
      system "git init"
      system "git checkout -b source"
      system "git remote add origin https://github.com/ridicholas/ridicholas.github.io.git"
    end

    # Configure Git to handle large files if necessary
    system "git config http.postBuffer 524288000"

    # Add, commit, and push changes
    system "git add ."
    message = "Site updated at #{Time.now.utc}"
    system "git commit -m #{message.inspect}"
    system "git push origin source --force"
  end
end

