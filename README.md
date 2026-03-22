# Ansible Role: Dotfiles

[![CI](https://github.com/geerlingguy/ansible-role-dotfiles/actions/workflows/ci.yml/badge.svg)](https://github.com/geerlingguy/ansible-role-dotfiles/actions/workflows/ci.yml)

Installs a set of dotfiles from a given Git repository. By default, it will install my (geerlingguy's) [dotfiles](https://github.com/geerlingguy/dotfiles), but you can use any set of dotfiles you'd like, as long as they follow a conventional format.

## Requirements

Requires `git` and `community.general` collection on the managed machine.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    dotfiles_repo: "https://github.com/ceso/dotfiles.git"
    dotfiles_repo_version: master

The git repository and branch/tag/commit hash to use for retrieving dotfiles.

    dotfiles_repo_accept_hostkey: true

Add the hostkey for the repo url if not already added.

    dotfiles_repo_local_destination: "~/Projects/repos/dotfiles"

The local path where the `dotfiles_repo` will be cloned.

    dotfiles_home: "~"

The home directory where dotfiles will be linked.

    dotfiles_files:
      - .config/bat
      - .config/eza
      - .config/fish
      - .config/ghostty
      - .config/git
      - .config/nvim
      - .config/zellij
      - .homebrew
      - .ssh

Entries to symlink into the home directory. Parent directories are created automatically.

    dotfiles_bin_dir: bin

Directory whose contents are individually symlinked to `~/.local/bin/`.

If any dotfiles directory contains a `GNUmakefile`, it is executed before symlinking.

## Dependencies

- `community.general`

## Example Playbook

    - hosts: localhost
      roles:
        - { role: geerlingguy.dotfiles }

## License

MIT / BSD

## Author Information

This role was created in 2015 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
