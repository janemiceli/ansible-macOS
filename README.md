# Laptop

Laptop is a playbook to set up an OS X laptop (for Site Reliability Engineering).

It installs and configures most of the software janemiceli uses on our Macs for work and play. 

It can be run multiple times on the same machine safely. It installs, upgrades, or skips packages based on what is already installed on the machine.


## Requirements

I've tested it on:

* OS X Big Sur


## Installation

### Fast Install

If you'd like to start with my default list of tools and apps (see Included Apps/Config below), then simply install with;

    sh -c "$(curl -fsSL https://raw.githubusercontent.com/janemiceli/laptop/master/install.sh)"


You can always customize the install after-the-fact (see below), and re-run the playbook. It will skip over any installed apps.

### Custom Install

If you want to add/remove to the list of apps/utils installed, its pretty straightforward.

As above, download and bootstrap the script. But stop it before it starts ansible, and edit the playbook as desired, before re-running ansible.

1. Grab and start the bootstrap script. Let it install the prereqs and clone the full `siyelo/laptop` repo locally...

      sh -c "$(curl -fsSL https://raw.githubusercontent.com/janemiceli/laptop/master/install.sh)"


1. Stop the script (Ctrl+C) when ansible asks for the a 'sudo' password. 

        ```
        Changing to laptop repo dir ...

        Running ansible playbook ...
        SUDO password:  ^c

        ```

1. Change into the cloned repo dir

        cd laptop

1. Edit playbook.yml and add/remove the apps/utils you want. 

        vi playbook.yml

1. Kick off ansible manually

        ansible-playbook playbook.yml -i hosts --ask-sudo-pass -vvvv 

You can do this as many times as you like and re-run the `ansible-playbook` command. Ansible is smart enough to skip installed apps, so subsequent runs are super fast.


## Included Applications / Configuration

### Applications

Apps installed with Homebrew Cask:

  - 1password
  - google-chrome
  - sublime-text3 # (experimental cask) | http://www.sublimetext.com/
  - vagrant # | https://www.vagrantup.com/downloads.html
  - vagrant-manager # 
  - virtualbox # | https://www.virtualbox.org/
  - vlc 

There are several more common cask apps listed in the playbook.yml - simply uncomment them to include them in your install. 


### Packages/Utilities 
 
Things installed with Homebrew:

  - brew-cask
  - coreutils # Install GNU core utilities (those that come with OS X are outdated)
  - docker # | https://docs.docker.com/installation/mac/
  - findutils  # Install GNU `find`, `locate`, `updatedb`, and `xargs`, g-prefixed
  - git


There are several more utils listed in the playbook.yml - simply uncomment them to include them in your install. 


## Development

You shouldn't wipe your entire workstation and start from scratch just to test changes to the playbook. 

### Approach

We've tested it using an OSX Big Sur for developing & testing the Ansible scripts.

### Whats included?

Nada. Well not much. The whole point is to test the process of getting our OSX dev machines from zero to hero. 


## Author

[Jane Miceli](http://janemiceli.com), 2021. 
