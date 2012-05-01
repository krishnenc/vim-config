require 'fileutils'

desc "Performs base installation"
task :base do
  # In stead of using standard snipmate repository I have my own custom sinpmate where
  # I have added a few extra goodies. Lookat readme at https://github.com/neerajdotname/snipmate.vim
  # to see the shortcuts I have added
  system("git clone git://github.com/neerajdotname/snipmate.vim.git bundle/snipmate")
  #system("git clone git://github.com/msanders/snipmate.vim.git bundle/snipmate")


  system("git clone git://github.com/scrooloose/nerdtree.git bundle/nerdtree")
  system("git clone git://github.com/scrooloose/nerdcommenter.git bundle/nerdcommenter")

  system("git clone git://github.com/vim-scripts/Color-Sampler-Pack.git bundle/color-sampler-pack")

  # I need only JavaScript validation. Even in that case I need the ability to turn it on and off dynamically
  # I will have my customized solution.
  #system("git clone git://github.com/scrooloose/syntastic.git bundle/syntastic")
  #
  system("git clone git://github.com/henrik/vim-ruby-runner.git bundle/vim-ruby-runner")
  system("git clone git://github.com/tpope/vim-endwise.git bundle/endwise")
  system("git clone git://github.com/tpope/vim-surround.git bundle/surround")
  system("git clone git://github.com/tpope/vim-unimpaired.git bundle/unimpaired")
  system("git clone git://github.com/tpope/vim-abolish.git bundle/abolish")
  system("git clone git://github.com/tpope/vim-repeat.git bundle/repeat")
  system("git clone git://github.com/tpope/vim-vividchalk.git bundle/vividchalk")
  system("git clone git://github.com/mileszs/ack.vim.git bundle/ack")
  system("git clone git://github.com/edsono/vim-matchit.git bundle/matchid")
  system("git clone git://github.com/tpope/vim-markdown.git bundle/markdown")
  system("git clone git://github.com/kchmck/vim-coffee-script.git bundle/coffee-script")
  system("git clone git://github.com/tpope/vim-bundler.git bundle/vim-bundler")

  # http://vimcasts.org/episodes/aligning-text-with-tabular-vim/
  system("git clone git://github.com/godlygeek/tabular.git bundle/tabular")
end

desc "Performs git plugins installation"
task :git do
  system("git clone git://github.com/tpope/vim-git.git bundle/vim-git")
  system("git clone git://github.com/tpope/vim-fugitive.git bundle/fugitive")
end

desc "Installs plugins for rails development"
task :rails do
  system("git clone git://github.com/tpope/vim-ragtag.git bundle/ragtag")
  system("git clone git://github.com/vim-ruby/vim-ruby.git bundle/vim-ruby")
  system("git clone git://github.com/tpope/vim-rails.git bundle/vim-rails")
  system("git clone git://github.com/tpope/vim-cucumber.git bundle/vim-cucumber")
  system("git clone git://github.com/tpope/vim-haml.git bundle/vim-haml")
end


desc "Performs bundle cleanup (delete plugins installed from git source)"
task :cleanup do
  path = File.join(File.dirname(__FILE__), 'bundle')
  Dir.foreach(path) do |entry|
    if File.exist?(File.join(path, entry, ".git"))
      FileUtils.rm_rf(File.join(path, entry))
    end unless entry =~ /\.+/
  end
end

desc "Performs plugins update"
task :update do
  path = File.join(File.dirname(__FILE__), 'bundle')
  Dir.foreach(path) do |entry|
    bundle = File.join(path, entry)
    if File.exist?(File.join(bundle, ".git"))
      print "Updating #{entry}: "
      system("cd #{bundle} && git pull")
      system("cd #{bundle} && git submodule update") unless `cd #{bundle} && git submodule`.empty?
    end unless entry =~ /\.+/
  end
end

desc "=> base"
task :default => [:base, :git, :rails]
