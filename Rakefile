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
  posttype = ask('Type? [b]log,[e]ssay,[p]roject,[a]rt: ')

  #Create new a post
  desc "Default 'rake' command creates a new post"
  task :default do
    filename = "#{Time.now.strftime('%Y-%m-%d')}-#{title.gsub(/\s/, '_').downcase}.md"
    path = File.join("_posts", filename)
    if File.exist? path; raise RuntimeError.new("File exists #{path}"); end
    File.open(path, 'w') do |file|
    if posttype == 'b'
      file.write <<-EOS
---
layout: post
title: #{title}
categories: blog #{Time.now.strftime('%Y')} #{Time.now.strftime('%m')}
---


      EOS
    elsif posttype == 'e'
      file.write <<-EOS
---
layout: post
title: #{title}
---


      EOS
    elsif posttype == 'a'
      file.write <<-EOS
---
layout: art
title: #{title}
thumb: /assets/img/addimage.png
fullimg: /assets/img/addimage-full.png
---


      EOS
    elsif posttype == 'p'
      file.write <<-EOS
---
layout: project
title: #{title}
thumb: /assets/img/addprojectimg.png
---


      EOS
    else
      puts "Will create default blog post type"
      file.write <<-EOS
---
layout: post
title: #{title}
---


      EOS
    end
    end

  # invoke Sublime Text 2 to edit file
  sh "subl #{path}"
  
  end