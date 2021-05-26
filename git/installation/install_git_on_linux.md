# Install Git on Linux

Git was originally developed to version the Linux operating system! So, it only makes sense that it is easy to configure to run on Linux.

You can install Git on Linux through the package management tool that comes with your distribution.

#### For Redhat, CentOS and Fedora

1. Git packages are available using `dnf`.
2. To install Git, navigate to your command prompt shell and run the following command: `sudo dnf install git-all`.
3. Once the command output has completed, you can verify the installation by typing: `git version`.

#### For Debian/Ubuntu

1. Git packages are available using `apt`.
2. It's a good idea to make sure you're running the latest version. To do so, Navigate to your command prompt shell and run the following command to make sure everything is up-to-date: `sudo apt-get update`.
3. To install Git, run the following command: sudo apt-get install git-all.
4. Once the command output has completed, you can verify the installation by typing: `git version`.

Note: You can download the proper Git versions and read more about how to install on specific Linux systems, like installing Git on Ubuntu or Fedora, [in git-scm's documentation](https://git-scm.com/download/linux).
