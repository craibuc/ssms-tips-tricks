namespace :documentation do

  desc 'build documentation'
  task :build do

    puts "Converting to HTML..."
    `bundle exec asciidoctor SSMS2012.adoc`
    puts " -- HTML output at SSMS2012.html"

    puts "Converting to PDF... (this one takes a while)"
    `bundle exec asciidoctor-pdf SSMS2012.adoc 2>/dev/null`
    puts " -- PDF  output at SSMS2012.pdf"

  end
end

  # http://stackoverflow.com/questions/15501149/how-can-i-include-a-version-file-in-a-commit
  # Read config/version.rb file containing
  #   a.b.c
  # Overwrite config/version.rb file to contain:
  #   a.b.c+1
  task :bump do
    desc "increment build number in config/version.rb"
    file = "./version.rb"
    unless (File.exist?(file))
      $stderr.puts("cannot locate version file #{file}")
    else
      s = File.open(file) {|f| f.read}
      if (s =~ /(\d+)\D+(\d+)\D+(\d+)/)
        # s1 = "VERSION = [#{$1}, #{$2}, #{$3.to_i + 1}]"
        s1 = "#{$1}.#{$2}.#{$3.to_i + 1}"
        $stderr.puts(s1)
        File.open(file, "w") {|f| f.puts(s1) }
      else
        $stderr.puts("cannot parse version file")
      end
    end
  end

task :default => "documentation:build"