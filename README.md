# Mutually Human Spacemacs Config

This is a common set of base functionality shared by us Humans. It isn't meant
to be the _best_ config for everyone, but a _good enough_ config for us to
share. When it comes to text editor configuration, perfect is the enemy of good.
It is more valuable to be shared among everyone than it is to be everyone's
absolute favorite. Too many per-user customizations and it makes it difficult to
sit down an pair together. It tries to allow for some local customizations, but
ideally everyone will submit PRs back to this config (or to Spacemacs itself!)
so we can all get a better shared config.

It is generally configured with good defaults for the web development modes, or
other languages that have caught our eye recently. If you decide to update
something, please consider opening a PR to see if everyone else is interested in
your customization. If it is really as great as you think it is, I'm sure we'll
be really impressed by your work and merge it in. It is probably good enough for
Spacemacs itself.

# Installation

1. Install Emacs. If you're looking for guidance, the main Spacemacs repo has a
[good set of instructions](https://github.com/syl20bnr/spacemacs/blob/master/README.md#emacs)
for installing Emacs.

1. Clone this repo:

    ```bash
    $ git clone git@github.com:mhs/spacemacs-config.git
    ```

1. Backup your local Emacs configuration files. This may not be
   necessary if you don't have any existing Emacs settings.

    ```bash
    $ mv ~/.emacs ~/.emacs.bak
    $ mv ~/.emacs.d ~/.emacs.bak.d
    ```

1. Run the Rake task to install and symlink the shared configuration.

    ```bash
    $ rake
    ```

1. Launch Emacs!

1. Read some
   [Spacemacs Documenation](https://github.com/syl20bnr/spacemacs/blob/master/doc/DOCUMENTATION.org)!
   Remember, Spacemacs is neither Emacs nor Vim, it is a new editor that takes
   advantage of the best parts of both.

# Layout

```bash
$ tree -L 1
.
├── LICENSE
├── README.md
├── Rakefile
├── spacemacs.el
├── machine-local.el
└── spacemacs_master
```

You're currently in the `README.md`. This is a great place to start
contributing. It could really use some copyediting.

The `Rakefile` sets up all the required symlinks for everything to work as
expected. This process allows us to check the `.spacemacs`/`spacemacs.el` file
into git and share it easily without messing up the way that Spacemacs handles
self-updates.

`spacemacs.el` is the main configuration file. This is where all the shared
settings, layer configuration, and package installation happens. If you want to
make a PR to update our Spacemacs config, it probably happens here.

If you really aren't sure you want to contribute your change, you can add it to
the `machine-local.el`. It isn't tracked in git, so you can edit it to your
heart's content. Work on a large monitor and want to bump the default font size?
That belongs here.

To simplify installation of Spacemacs, as well as allowing it to update itself
easily, the setup task will clone the upstream Spacemacs repo into
`spacemacs_master`. You won't want to modify this directory, but it puts it in a
convenient place to do a little research. You need not be scared of core
Spacemacs.


# Contributing

1. Fork it ( http://github.com/mhs/spacemacs-config/fork )
1. Create your feature branch (`git checkout -b feature/enhance-your-editor`)
1. Commit your changes (`git commit`)
1. Push to the branch (`git push origin feature/enhance-your-editor`)
1. Create new Pull Request
