require 'rake'
require 'pathname'

namespace :spacemacs do

  HOME = Pathname.new('~').expand_path
  CONFIG_ROOT = Pathname.new(__FILE__).expand_path.dirname

  master_checkout = CONFIG_ROOT.join('spacemacs_master')
  dot_emacs = HOME.join('.emacs.d')
  dot_spacemacs = HOME.join('.spacemacs')
  dot_custom = HOME.join('.spacemacs.custom')
  dot_spacemacs_d = HOME.join('.spacemacs.d')

  spacemacs_config = CONFIG_ROOT.join('spacemacs.el')
  machine_config = CONFIG_ROOT.join('machine-local.el')

  directory master_checkout do
    puts "cloning spacemacs_master"
    puts `git clone https://github.com/syl20bnr/spacemacs spacemacs_master`
  end

  directory dot_emacs do
    puts "Symlinking ~/.emacs.d -> spacemacs_master"
    ln_s(master_checkout, dot_emacs)
  end

  file dot_spacemacs do
    puts "Symlinking ~/.spacemacs -> spacemacs.el"
    ln_s(spacemacs_config, dot_spacemacs)
  end

  file dot_custom do
    touch dot_custom
  end

  file machine_config do
    touch machine_config
  end

  task :touch => [dot_custom, machine_config]
  task :link => [:touch, master_checkout, dot_emacs, dot_spacemacs]

  task :check do
    if `which emacs`.empty?
      raise "Install the latest version of Emacs before continuing."
    end
  end

end

task :default => ['spacemacs:check', 'spacemacs:link']
