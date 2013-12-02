# Sources:
  # http://jasonseifer.com/2010/04/06/rake-tutorial
  # http://elia.wordpress.com/2008/11/07/get-input-in-rake-tasks/
  # http://www.layouts-the.me/rake/2011/04/23/rake_tasks_for_jekyll/
  # http://olidin.com/rake_for_jekyll/
  # memememe

  # Asking for title
  def ask message
  print message
  STDIN.gets.chomp
  end
  title = ask('Title: ')
  
  # Asking for type
  def ask message
  print message
  STDIN.gets.chomp
  end
  posttype = ask('Type? [b]log,[e]ssay,[p]roject: ')

  #Create new a post
  desc "Default 'rake' command creates a new post"
  task :default do
    filename = "#{Time.now.strftime('%Y-%m-%d')}-#{title.gsub(/\s/, '_').downcase}.md"
    path = File.join("_posts", filename)
    if File.exist? path; raise RuntimeError.new("File exists #{path}"); end
    File.open(path, 'w') do |file|
    if posttype == 'e'
      file.write <<-EOS
---
layout: post
title: #{title}
headline: ADDLONGHEADLINE
category: essays
permalink: /essays/#{title.gsub(/\s/, '_').downcase}
---


      EOS
    elsif posttype == 'p'
      file.write <<-EOS
---
layout: project
title: #{title}
category: projects
permalink: /projects/#{title.gsub(/\s/, '_').downcase}
thumb: /assets/img/ADDFILE
external: http://ADDURL
---


      EOS
    else
      puts "Will create default blog post type"
      file.write <<-EOS
---
layout: post
title: #{title}
category: blog
---


      EOS
    end
    end


  # open to edit file
  yesopen = ask('Open now? [yes,no] ')
  if yesopen == 'yes'
    sh "open -a Mou #{path}"
  else
    puts "Done!"
  end

  end