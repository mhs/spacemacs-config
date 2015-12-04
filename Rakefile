require 'rake'
require 'pathname'

namespace :spacemacs do

  HOME = Pathname.new('~').expand_path
  CONFIG_ROOT = Pathname.new(__FILE__).expand_path.dirname

  master_checkout = CONFIG_ROOT.join('spacemacs_master')
  dot_emacs = HOME.join('.emacs.d')
  dot_spacemacs = HOME.join('.spacemacs')
  dot_spacemacs_d = HOME.join('.spacemacs.d')
  dot_custom = CONFIG_ROOT.join("spacemacs.d/spacemacs.custom")

  spacemacs_d = CONFIG_ROOT.join('spacemacs.d')
  machine_config = CONFIG_ROOT.join('machine-local.el')

  directory master_checkout do
    puts "cloning spacemacs_master"
    puts `git clone https://github.com/syl20bnr/spacemacs spacemacs_master`
  end

  def make_date_versioned s
    "#{s}.#{Time.new.strftime('%Y%m%d')}"
  end

  task :backup_dot_emacs do
    if File.exists?(dot_emacs)
      unless
        File.ftype(dot_emacs) == 'link' &&
          File.readlink(dot_emacs) != master_checkout
        mv(dot_emacs,make_date_versioned(dot_emacs))
      end
    end
  end

  directory dot_emacs do
    puts "Symlinking ~/.emacs.d -> spacemacs_master"
    ln_s(master_checkout, dot_emacs)
  end

  directory dot_spacemacs_d do
    puts "Symlinking ~/.spacemacs.d -> spacemacs.d"
    ln_s(spacemacs_d, dot_spacemacs_d)
  end

  file dot_custom do
    touch dot_custom
  end

  file machine_config do
    touch machine_config
  end

  task :backup_dot_spacemacs do
    if File.exists?(dot_spacemacs)
      puts "Backing up existing ~/.spacemacs"
      mv(dot_spacemacs,make_date_versioned(dot_spacemacs))
    end
  end

  task :touch => [dot_custom, machine_config]
  task :link => [:touch, master_checkout, :backup_dot_spacemacs,
                 :backup_dot_emacs, dot_emacs, dot_spacemacs_d]

  task :check do
    if `which emacs`.empty?
      raise "Install the latest version of Emacs before continuing."
    end
  end

end

task :default => ['spacemacs:check', 'spacemacs:link']
