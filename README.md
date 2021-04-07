# IMPLEMENTED PARTIALLY BY [archinstall](https://github.com/archlinux/archinstall). ARCHIVED UNTIL FURTHER NOTICE

# arch-installer [![Build Status](https://travis-ci.com/kgizdov/arch-installer.svg?branch=master)](https://travis-ci.com/kgizdov/arch-installer)
An installer for Arch Linux

Create an awesome interactive installer for Arch Linux and package it into a comfortably sized live CD `*.iso` image.

## Requirements

 * Use [Archiso](https://wiki.archlinux.org/index.php/Archiso) to produce an new type of live CD image containing a Graphical User Interface (GUI) interactive installer for Arch Linux
 * Produce a minimal install by default, mimicking the current Arch Linux ISO philosophy, that can be customized by the user
 * Support both `mkinitcpio` and `dracut` initramfs tools
 * Support a variety of bootloaders (systemd-boot and GRUB2 at a minimum)
 * Should not be much larger that a current Arch Linux ISO, ideally `<1GB`
 * Anyone should be able to recreate/customize the ISO
 * Automated build (e.g. Travis CI)

**Bonus Achivements** (refer to [section Side Effects](#side-effects)):
 * Improve upon the available Arch Linux installation processes in terms of accessibility
 * Unattended (automated) installs
 * *to-be-determined*

## Considerations
  * These are a few of the major currently available frameworks to do this(&ast;):
    - [Anaconda](https://fedoraproject.org/wiki/Anaconda)
      - more heavy, but feature-rich framework
      - enables fully automated installations natively
      - needs to be fully packaged for Arch Linux
      - relies on python stack
      - accessible install using Orca
    - [Calamares](https://calamares.io/)
      - most of the work is there
      - can be made lightweight with reducing Qt extensions
      - does not currently support error handling/recovery
      - accessible install using Orca
    - [ncurses](https://www.gnu.org/software/ncurses/)
      - much more customizable
      - has to be mostly done from scratch
      - more work for accessibility

(&ast;) This is by no means an exhaustive list and should only encourage rather than discourage.

# Footnotes

## Side Effects
By simplifying the installation procedure the project will also inadvertently
lower the skill requirement for entry into the Arch Linux ecosystem.
For a distribution with a strong set of [principles](https://wiki.archlinux.org/index.php/Arch_Linux#Principles),
reflecting "an explicit expectation of self-sufficiency and willingness to learn"
from its community, that development might seem undesirable at first glance.
However, Arch Linux has also become a major Linux distribution and
one of the most popular choices for Linux newcomers, because of its
simplicity, modernity and versatility.
As such the resultant installer must aim to preserve these principles and
educate new users. Moreover, a successful project must strive to improve
the current state by giving the skilled and knowledgeable user
the ability and choice, all the while removing the overhead.

Furthermore, depending on the exact implementation, several, if not all, points of the following might be fulfilled:
 * provide simplified accessibility installs:
   - add further *choice* to options already provided in [Arch Linux Accessibility](https://wiki.archlinux.org/index.php/Accessibility)
   - alternative to [Arch Linux for the blind](https://wiki.archlinux.org/index.php/TalkingArch)
 * unattended (automated) installs with hassle-free configuration, minimal hardware and software overhead
   - treat a system install as code, tweak/test until satisfied *Ansible style*
 * *to-be-determined*

**DISCLAIMER**: This project is not meant to encourage, enable or otherwise proliferate
ignorance about ones system, its configuration and usage. A good solutions to the problem
will make sure a user does understand each and every part of installation procedure.
