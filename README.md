# Embedded Systems Machine Template

This repository contains a packer template for building a Vagrant box for use 
in CS120B and CS122A at [UCR](www.ucr.edu). I created this template to allow for
people to easily get started with an environment with all of the tools and
scripts necessary to get started in those courses. It also allows people to
forward their internet connection to a Raspberry Pi Zero W (v1.1+) for labs that
require that device.

### Caveats
This VM was designed with macOS in mind. The process here could be modified to
support other operating systems, but I use a Mac and don't have access to other
OSes so I can only offer a solution for a Mac environment. If you would like to
contribute support for other operating systems, please feel free to submit a PR
with your changes.

## Getting Started
I'll assume you have the repository cloned to your machine already.

1. First, you need to install VirtualBox, Packer, Vagrant, and Ansible.
```bash
$ brew install vagrant packer
$ brew cask install virtualbox
$ pip install --user ansible
```
2. Run the packer script. This may take some time so grab a coffee or a snack
   while you wait.
```bash
$ cd /location/of/embedded-systems-machine-template
$ packer build machine.json
```
3. `cd` into the output directory and run the VM.
```bash
$ cd output-vagrant/
$ vagrant up
```

_Note:_ if you get any network interface errors, edit the `Vagrantfile` in your
output directory and edit the end of line 34 (the one beginning with
`output.vm.network`). Either comment the line out, or if you have your Raspberry
Pi connected to your Mac, edit the last string of text with `enX: RNDIS/Ethernet
Gadget` where `X` is the physical network interface that your Pi is connected
to. You can get this number by running the command `networksetup
-listhardwareports`.

## Todos:
- Implement script to autoselect Raspberry Pi network port.
- Add support for Windows.
