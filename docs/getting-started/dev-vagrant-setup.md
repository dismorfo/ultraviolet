---
layout: default
title: Dev Mode Setup (Vagrant)
parent: Getting Started
nav_order: 3
---
# WiP :: {{ page.title }}

## Prerequisites
- **VirtualBox**
  + [Installation instructions](https://www.virtualbox.org/wiki/Downloads)
- **Vagrant**
  + [Installation instructions](https://www.vagrantup.com/downloads)


## Steps
1. Get the local copy of the UltraViolet source code:
  ```sh
  git clone https://github.com/nyudlts/ultraviolet.git && cd ultraviolet
  ```
2. Set up Vagrant CentOS box:
  ```sh
  vagrant up
  ```

3. SSH into the box and move into the project directory:
  ```
  vagrant ssh
  cd ultraviolet
  ```

You can exit the box with `exit`. This will leave the box running in the background. If you would like to stop it, run `vagrant halt`. If you would like to destroy the box, run `vagrant destroy`.
