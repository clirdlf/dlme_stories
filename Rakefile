require 'colorize'
require 'fileutils'
require 'html-proofer'

task default: %w(convert:all)

task :test do
  sh "bundle exec jekyll build"
  options = { :assume_extension => true }
  HTMLProofer.check_directory("./_site", options).run
end

namespace :convert do

  @sizes = {
    cover: "1200x800",
    landing: "480x360",
    large_square: "480x480",
    exhibit_long: "965x350",
    exhibit_image: "845"
  }

  desc 'Generate deravative images'
  task :all => [:rename, :all_sizes]

  task :all_sizes do

    puts "Generating deravative images".green
    Dir.glob('originals/*').each do |image|
      @sizes.each do |name, size|
        basename = File.basename(image, ".*")
        fname = "#{basename}-#{name}-#{size}#{File.extname(image)}"
        puts "\tGenerating #{fname}".yellow
        `convert #{image} -resize #{size} images/#{fname}`
      end
    end

    puts "Running image minification".green
    `gulp imagemin`
  end

  desc 'Remove spaces from filenames'
  task :rename do
    Dir.glob('originals/*').each do |image|
      name = File.basename(image, '.*').squeeze.downcase.tr(" ", "_").tr(',.[]', '')
      ext = File.extname(image)
      File.rename(image, 'originals/' + name + ext)
    end
  end

  def resize(image, size)
    basename = File.basename(image, '.*')
    "convert #{image} -resize #{size} images/#{basename}-#{size}#{File.extname(image)}"
  end

  desc 'Generate cover images'
  task :cover do
    size = '1200x800'
    Dir.glob('originals/*').each do |image|
      puts resize(image, size)
    end
  end

  desc 'Generate landing page images'
  task :landing do
    size = '1200x800'
    Dir.glob('originals/*').each do |image|
      puts resize(image, size)
    end
  end
end
