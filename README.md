# My Altcoin test environment
Corresponding blog post:
https://medium.com/tales-from-the-crypt-o/bitcoin-altcoin-test-environment-c041508cfd02

In the crazy world of crypto, there is always a new project or wallet to look into. Many of these projects are open source and can be compiled from source to try out new features. Some are binary-only and should be evaluated carefully.

If this is something you do on a regular basis, you can probably make use of this short article.

The end result will always be a Ubuntu VM that runs your code in a clean way that is also (at least a bit) more secure than running it directly. No matter if you are on Windows, OSX or Linux. That's the true beauty of this.

## Tools
My preferred setup to test and develop altcoins is (as almost always) designed around Vagrant. Vagrant is an open source tool from the DevOps world that is often used to provision development environments automatically. 

You need the following set of tools to start:  

* VirtualBox (newest version from the [VirtualBox-Homepage])
* Vagrant (newest version from the [Vagrant-Homepage])
* **Only on Windows**: Git for Windows (newest version from the [Git-Homepage])

## Start of the Environment
The `Vagrantfile` in this repository contains the complete configuration of the environment. This means the definition of the Linux distribution, the networking parameter, packages to install and many things more. Check the Vagrant documentation for pointers whats possible.

> Since the configuration of Vagrant and the environment to create is all part of the source (git) repository, the environment can easily be destroyed and re-created within a couple of minutes.

### Clone the repo
Exactly like with any other development workflow,  the initialisation of this environment is created by checking out this source code repository.
```sh
$ git clone https://github.com/marsmensch/altcoin-testenv.git
```

### One command to rule them all
In a console (for Windows use `Git-Bash`) open the cloned directory `altcoin-testenv` and execute the **one and only required command to create the environment**:

```sh
$ vagrant up
```

No kidding, that's it!

What happens now is a bit of DevOps magic. After a couple of minutes, the following things happened:

* Vagrant created and configured a virtual machine via VirtualBox
* The shell script `vagrant_provision.sh` installs our desired set of packages
* Vagrant automatically configures a couple of useful shortcuts like a shared folder in `/vagrant` with the host system and convenient passwordless logins via SSH Keys to the VM. 

>         The box has 2048 MB of RAM and 2 CPU cores assigned. Change that in the `Vagrantfile` if you want more or less RAM/CPU.

The VM windows is also shown for your convenience (Vagrant normally hides it), so you can login graphically and test e.g. graphical wallets.

## Connect to your VM
Connecting to your VM is as easy as run a command in a terminal. You need exactly one command to connect:

```sh
$ vagrant ssh
```

> For SSH connections Vagrant looks for a SSH client (`ssh.exe`) in your $PATH. This is already the case for OSX and Linux. On Windows you want to install Git for Windows for this.

## Working with your new VM
As noted above, the included shell script `vagrant_provision.sh` installs your desired set of packages. The example i currently provide with the source installs the $RNS wallet. It can be started via after installation with the command: 

```sh
$ /usr/local/bin/runwallet
``` 

Have fun and stay tuned for the next entry!

[Git-Homepage]: <https://github.com/git-for-windows/git/releases/latest>
[VirtualBox-Homepage]: <https://www.virtualbox.org/wiki/Downloads>
[Vagrant-Homepage]: <https://www.vagrantup.com/downloads.html>
[MaibornWolff-Git]: <http://git.maibornwolff.de/mwea/ADEmployeeService>
