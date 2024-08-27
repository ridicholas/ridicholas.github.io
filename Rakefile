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
  Dir.mktmpdir do |tmp|
    cp_r "_site/.", tmp

    pwd = Dir.pwd
    Dir.chdir tmp

    system "git init"
    system "git checkout -b source" # Explicitly create the source branch
    system "git add ."
    message = "Site updated at #{Time.now.utc}"
    system "git commit -m #{message.inspect}"
    system "git remote add origin https://github.com/ridicholas/ridicholas.github.io"
    system "git push origin source --force"

    Dir.chdir pwd
  end
end
