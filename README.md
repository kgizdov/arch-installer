# arch-installer
An installer for Arch Linux

Create an awesome interactive installer for Arch Linux and package it into a comfortably sized live CD `*.iso` image.

# Google Summer of Code

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

(&ast;) This is by no means exhaustive list and should only encourage rather than discourage. Applicants are free
to bring forth their own solution to the task at hand.

## Test

This describes an exercise to evaluate those students interested in applying for
the *arch-installer* project,
included in the Google Summer of Code (GSoC) program and offered by Arch Linux GSoC.

For any questions, please don't hesitate to contact us: arch@kge.pw

## Exercise for Candidate Students

In order to demonstrate some of the required skills for the project,
students will need to perform a small task designed to test basic Arch Linux
knowledge, in addition to basic packaging principles.
The overall task is split in two smaller tasks, with one extra more advanced exmple,
which is optional, but illustrates more widely the project.

### Task 1: *Build an AUR package yourself*

As a start, students are asked to build an Arch User Repository package.
The package is very simple, but is chosen to test your understanding.
If you do not have a running Arch Linux system on hand, you can skip this task
for now and return to it after task 2.

Basically:
  * Clone the repo of the `python-memoizedb` package
  * build the package with `makepkg`

Bonus points - change the packager info to your name and GPG key, build
the package with `devtools` and produce a package signature.

After this, make sure to save your work and you can add this to the rest of the required
as described in [section Submitting results](#submitting-results).

### Task 2: *Install Arch Linux in a virtual machine*

In order to do well in this project you will require knowlege about
installing Arch Linux and most probably a virtual machine with it.

For this task to be completed:
  * Select a virtual machine manager that you feel comfortable with (e.g. VirtualBox)
  * Download the official [Arch Linux ISO](https://www.archlinux.org/download/)
  * Follow the [Arch Linux Installation guide](https://wiki.archlinux.org/index.php/Installation_guide)
  * Boot into your virtual machine
  * Install `archey3` and run it

**NOTE**: If you did not have an Arch Linux system on hand for task 1, you could
use this virtual machine to go back and complete it now.

After this, make sure to save your work and you can add this to the rest of the required
as described in [section Submitting results](#submitting-results).

### Task 3 (Optional, Advanced): *Reproduce an available package*

In this task we will try and reproduce the an Arch Linux official package.
Try an do this in your newly created virtual machine and not on your system.

In preparation for this task, students would need some Arch Linux specific tooling:

  * Install `archlinux-repro`
  * Download the `archlinux-repro` package file from Arch Linux's repo - [here](https://www.archlinux.org/packages/community/any/archlinux-repro/download/)
  * Try and reproduce the package - `repro archlinux-repro-*-1-any.pkg.tar.zst`

**NOTE**: You will need to produce a `*.zst` package file. For this purpose,
you will need to create a file `~/.config/pacman/makepkg.conf` with the following
string in it `PKGEXT='.pkg.tar.zst'`. (Do not do this on your main system!)

After being executed and saved, you can add this to the rest of the required
as described in [section Submitting results](#submitting-results).

### Evaluation


# Submitting results

Those wishing to submit test results should create a new merge request
which contains a new folder in the GSoC directory (with the name of the folder
as the initials of the applicant).
This folder should contain a `python-memoizedb` package file (and optionally a signature
file with it too) and a screenshot of their running Arch Linux virtual machine clearly displaying
the output from `archey3`.
If the optional taks is attempted, then include the two package files for `archlinux-repro` with name suffixes `.download` and `.repo` for the downloaded and reproduced version respectively.

Once you complete any of the tasks of this exercise, please send and e-mail to: arch@kge.pw

## Side Effects
By simplifying the installation procedure the project will also inadvertently
lower the skill requirement for entry into the Arch Linux ecosystem.
For a distribution with a strong set of [principles](https://wiki.archlinux.org/index.php/Arch_Linux#Principles),
reflecting "an explicit expectation of self-sufficiency and willingness to learn"
from its community, that development might seem undesirable at first glance.
However, Arch Linux has also become a major Linux distributions and
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
