---
title: Setup
---

There are a number of tasks you need to complete *before* the workshop to ensure that you get the 
best learning experience:

1. Create a Docker Hub account (if you do not already have one)
2. Make sure you have a working installation of Docker Desktop or Docker on your laptop
3. Check you can login to the ARCHER2 account you created during course registration

## Create an account on Docker Hub

Please seek help at the start of the lesson if you have not been able to establish a website account on:
- The [Docker Hub](http://hub.docker.com). We will use the Docker Hub to download pre-built container images, and for you to upload and download container images that you create, as explained in the relevant lesson episodes.

## Install Docker Desktop or Docker

In most cases, you will need to have administrator rights on the computer in order to install the Docker software. If you are using a computer managed by your organisation and do not have administrator rights, you *may* be able to get your organisation's IT staff to install Docker for you. Alternatively your IT support staff *may* be able to give you remote access to a server that can run Docker commands.

Please try to install the appropriate Docker software from the list below depending on the operating system that your computer is running. Do let the workshop organisers know as early as possible if you are unable to install Docker using these instructions, as there may be other options available.

#### Microsoft Windows

**You must have admin rights to run Docker!** Some parts of the lesson will work without running as admin but if you are unable to `Run as administrator` on your machine some elements of this workshop might not work as described.

Ideally, you will be able to install the Docker Desktop software, following the [Docker website's documentation](https://docs.docker.com/docker-for-windows/install/). Note that the instructions for installing Docker Desktop on Windows 10 Home Edition are different from other versions of Windows 10.

Note that the above installation instructions highlight a minimum version or "build" that is required to be able to install Docker on your Windows 10 system. See [Which version of Windows operating system am I running?](https://support.microsoft.com/en-us/windows/which-version-of-windows-operating-system-am-i-running-628bec99-476a-2c13-5296-9dd081cdd808) for details of how to find out which version/build of Windows 10 you have.

If you are unable to follow the above instructions to install Docker Desktop on your Windows system, the final release of the deprecated Docker Toolbox version of Docker for Windows can be downloaded from the [releases page of the Docker Toolbox GitHub repository](https://github.com/docker/toolbox/releases). (Download the `.exe` file for the Windows installer). _Please note that this final release of Docker Toolbox includes an old version of Docker and you are strongly advised not to attempt to use this for any production use. It will, however, enable you to follow along with the lesson material._

> ## Warning: Git Bash
> If you are using Git Bash as your terminal on Windows then you should be aware that you may run
> into issues running some of the commands in this lesson as Git Bash will automatically re-write
> any paths you specify at the command line into Windows versions of the paths and this will confuse
> the Docker container you are trying to use. For example, if you enter the command:
> ```
> docker run alpine cat /etc/os-release
> ```
> Git Bash will change the `/etc/os-release` path to `C:\etc\os-release\` before passing the command
> to the Docker container and the container will report an error. If you want to use Git Bash then you
> can request that this path translation does not take place by adding an extra `/` to the start of the
> path. i.e. the command would become:
> ```
> docker run alpine cat //etc/os-release
> ```
> This should suppress the path translation functionality in Git Bash.
{: .callout}

#### Apple macOS

Ideally, you will be able to install the Docker Desktop software, following the
[Docker website's documentation](https://docs.docker.com/docker-for-mac/install/).
The current version of the Docker Desktop software requires macOS version 10.14 (Mojave) or later.

If you already use Homebrew or MacPorts to manage your software, and would prefer to use those
tools rather than Docker's installer, you can do so. For Homebrew, you can run the command
`brew install --cask docker`. Note that you still need to run the Docker graphical user interface
once to complete the initial setup, after which time the command line functionality of Docker will
become available. The Homebrew install of Docker also requires a minimum macOS version of 10.14.
The MacPorts Docker port should support older, as well as the most recent, operating system
versions (see the [port details](https://ports.macports.org/port/docker/details/)), but note that
we have not recently tested the Docker installation process via MacPorts.

#### Linux

There are too many varieties of Linux to give precise instructions here, but hopefully you can locate documentation for getting Docker installed on your Linux distribution. It may already be installed. If it is not already installed on your system, the [Install Docker Engine](https://docs.docker.com/engine/install/) page provides an overview of supported Linux distributions and pointers to relevant installation information. Alternatively, see:

 - [Docker Engine on CentOS](https://docs.docker.com/install/linux/docker-ce/centos/)
 - [Docker Engine on Debian](https://docs.docker.com/install/linux/docker-ce/debian/)
 - [Docker Engine on Fedora](https://docs.docker.com/install/linux/docker-ce/fedora/)
 - [Docker Engine on Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

Alternatively, Docker now provide a version of Docker Desktop for some Linux distributions which give a user experience similar to Docker Desktop on Windows or macOS. You can find instructions on installing this at:

 - [Docker Desktop for Linux](https://docs.docker.com/desktop/install/linux-install/)

### Verify Installation

To quickly check if the Docker and client and server are working run the following command in a new terminal or ssh session:
~~~
$ docker version
~~~
{: .language-bash}
~~~
Client:
 Version:           20.10.2
 API version:       1.41
 Go version:        go1.13.8
 Git commit:        20.10.2-0ubuntu2
 Built:             Tue Mar  2 05:52:27 2021
 OS/Arch:           linux/arm64
 Context:           default
 Experimental:      true

Server:
 Engine:
  Version:          20.10.2
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.13.8
  Git commit:       20.10.2-0ubuntu2
  Built:            Tue Mar  2 05:45:16 2021
  OS/Arch:          linux/arm64
  Experimental:     false
 containerd:
  Version:          1.4.4-0ubuntu1
  GitCommit:        
 runc:
  Version:          1.0.0~rc95-0ubuntu1~21.04.1
  GitCommit:        
 docker-init:
  Version:          0.19.0
  GitCommit:        
~~~
{: .output}

The above output shows a successful installation and will vary based on your system.  The important part is that the "Client" and the "Server" parts are both working and returns information.  It is beyond the scope of this document to debug installation problems but common errors include the user not belonging to the `docker` group and forgetting to start a new terminal or ssh session.

## Check you can login to ARCHER2

As part of the course registration process, you will have created an account on ARCHER2. You should
check you can successfully login to ARCHER2 using this account ahead of the course. To do this you will 
first need to setup a TOTP (Time-base One Time Password).

### Setup TOTP on your ARCHER2 account

To log into ARCHER2, you will need to use a one time code as well as your SSH key. You can find information on how to set this up in the SAFE documentation:

- [How to turn on MFA on your machine account](https://epcced.github.io/safe-docs/safe-for-users/#how-to-turn-on-mfa-on-your-machine-account)

### Log into ARCHER2

You should now be able to log into ARCHER2 by following the [login instructions in the ARCHER2 documentation](https://docs.archer2.ac.uk/user-guide/connecting/). As noted above, in addition to the SSH key you should already have specified for the account, you will also need to register an autheticator app to generate TOTP for ARCHER2 login.

Note, you will need three credentials the first time you log into ARCHER2: SSH key, MFA TOTP and one-shot password from SAFE. Once you have successfully logged in, you should never need to use a password again, your access will be via SSH key + TOTP.

Step-by-step guide:

1. Apply for an account and register SSH key (should already be done as part of course registration)
2. [Setup TOTP for your ARCHER2 account (should already be done by following the instructions above)](https://docs.archer2.ac.uk/user-guide/connecting/#mfa-time-based-one-time-passcode-totp-code)
3. [Retrieve single use password from SAFE (first login only)](https://docs.archer2.ac.uk/user-guide/connecting/#first-login-password-required)

### A quick tutorial on copy/pasting file contents from episodes of the lesson
Let's say you want to copy text off the lesson website and paste it into a file named `myfile` in the current working directory of a shell window. This can be achieved in many ways, depending on your computer's operating system, but routes I have found work for me:

- macOS and Linux: you are likely to have the `nano` editor installed, which provides you with a very straightforward way to create such a file, just run `nano myfile`, then paste text into the shell window, and press <kbd>control</kbd>+<kbd>x</kbd> to exit: you will be prompted whether you want to save changes to the file, and you can type <kbd>y</kbd> to say "yes".
- Microsoft Windows running `cmd.exe` shells:
  - `del myfile` to remove `myfile` if it already existed;
  - `copy con myfile` to mean what's typed in your shell window is copied into `myfile`;
  - paste the text you want within `myfile` into the shell window;
  - type <kbd>control</kbd>+<kbd>z</kbd> and then press <kbd>enter</kbd> to finish copying content into `myfile` and return to your shell;
  - you can run the command `type myfile` to check the content of that file, as a double-check.
- Microsoft Windows running PowerShell:
  - The `cmd.exe` method probably works, but another is to paste your file contents into a so-called "here-string" between `@'` and `'@` as in this example that follows (the ">" is the prompt indicator):

        > @'
        Some hypothetical
        file content that is

        split over many

        lines.
        '@ | Set-Content myfile -encoding ascii

{% include links.md %}
