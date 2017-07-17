#!/usr/bin/env rake

desc 'Initial setup'
task :bootstrap do
  puts 'Installing Bundle...'
  puts `bundle install --without distribution`
end

desc 'Builds the site locally'
task :build do
  puts 'Building site.'
  sh 'PRODUCTION="YES" jekyll build -d _gh-pages'
end

namespace :podcast do
  desc 'Adds a new '
  task :new_episode do
    require 'mp3info'
    require 'pathname'

    mp3_path = ARGV.last

    abort 'Please specify a path to the MP3.' if mp3_path.nil?

    duration = ''
    Mp3Info.open(mp3_path) do |mp3|
      duration = Time.at(mp3.length).utc.strftime("%H:%M:%S")
    end
    filesize = File.stat(mp3_path).size

    output = <<-EOS
   - title:
     date:
     description:
     podcast_url:
     file_byte_length: #{filesize}
     duration: #{duration}
EOS

    File.open('_config.yml', 'a') do |file|
      file.write(output)
    end

    puts 'Updated _config.yml with new episode. Please configure.'
    sh 'open _config.yml'
  end
end

# Deprecated, but leaving shortcut in because I'm sure Orta, at least, has this
# in his muscle-memory.
task :init => :bootstrap

namespace :serve do
  desc 'Runs a local server *with* draft posts and watches for changes'
  task :drafts do
    puts 'Starting the server locally on http://localhost:4000'
    sh 'PRODUCTION="NO" jekyll serve --watch --drafts --port 4000'
  end

  desc 'Runs a local server *without* draft posts and watches for changes'
  task :published do
    puts 'Starting the server locally on http://localhost:4000'
    sh 'PRODUCTION="NO" jekyll serve --watch --port 4000'
  end
end

desc 'Runs a local server with draft posts and watches for changes'
task :serve => 'serve:drafts'

desc 'Deploy the site to the gh_pages branch and push'
task :deploy do
  FileUtils.rm_rf '_gh-pages'
  puts 'Cloning master branch...'
  puts `git clone https://github.com/artsy/artsy.github.io.git _gh-pages`
  Dir.chdir('_gh-pages') do
    puts `git checkout master`
  end

  Dir.chdir('_gh-pages') do
    puts 'Pulling changes from server.'
    puts `git reset --hard`
    puts `git clean -xdf`
    puts `git checkout master`
    puts `git pull origin master`
  end

  Rake::Task['build'].invoke

  Dir.chdir('_gh-pages') do
    puts 'Pulling changes from server.'
    puts `git checkout master`
    puts `git pull origin master`

    puts 'Creating a commit for the deploy.'

    puts `git ls-files --deleted -z | xargs -0 git rm;`
    puts `git add .`
    puts `git commit -m "Deploy"`

    puts 'Pushing to github.'
    puts `git push --quiet > /dev/null 2>&1`
  end
end

namespace :deploy do

  namespace :travis do
    task :checks do
      branch = ENV['TRAVIS_BRANCH'] # Ensure this command is only run on Travis.
      abort 'Must be run on Travis.' unless branch
      abort "Skipping deploy for non-source branch #{branch}." if branch != 'source'

      pull_request = ENV['TRAVIS_PULL_REQUEST'] #Ensure this command is only not run on pull requests
      abort 'Skipping deploy from pull request.' if pull_request != 'false'
    end

    task :github_setup do
      puts `git config --global user.email #{ENV['GIT_EMAIL']}`
      puts `git config --global user.name #{ENV['GIT_NAME']}`
      File.open("#{ENV['HOME']}/.netrc", 'w') { |f| f.write("machine github.com login #{ENV['GH_TOKEN']}") }
      puts `chmod 600 ~/.netrc`
    end
  end

  desc 'Run on Travis only; deploys the site when built on the source branch'
  task :travis => ['deploy:travis:checks', 'deploy:travis:github_setup', :deploy]
end

desc 'Defaults to serve:drafts'
task :default => 'serve:drafts'
