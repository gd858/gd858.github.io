# steps to install Android Studio on Fedora


```
sudo dnf install kernel-modules snapd fuse squashfuse -y

sudo systemctl enable --now snapd.socket

sudo ln -s /var/lib/snapd/snap /snap

sudo reboot

```

```
sudo snap install android-studio --classic
```


Certainly! Here's a detailed explanation of each command used to install Android Studio on Fedora:

1. **Install Required Packages**

   ```bash
   sudo dnf install kernel-modules snapd fuse squashfuse -y
   ```

   - **`sudo`**: Runs the command with superuser (root) privileges. This is necessary for installing software and modifying system configurations.
   - **`dnf`**: The package manager for Fedora (and other RPM-based distributions). It handles the installation, updating, and removal of software packages.
   - **`install`**: The command used by `dnf` to install packages.
   - **`kernel-modules`**: This package contains kernel modules necessary for various system functionalities. Installing this ensures that the kernel modules required by other packages (like `snapd`) are available.
   - **`snapd`**: This is the daemon that manages Snap packages. Snap is a package management system that allows you to install software bundled with its dependencies.
   - **`fuse`**: Filesystem in Userspace (FUSE) is a module that allows non-privileged users to create and manage filesystems without modifying kernel code.
   - **`squashfuse`**: A FUSE module for mounting SquashFS filesystems. SquashFS is a compressed read-only filesystem that Snap packages use.
   - **`-y`**: Automatically answers "yes" to all prompts during the installation process, so you don’t need to manually confirm each action.

2. **Enable and Start the Snap Socket**

   ```bash
   sudo systemctl enable --now snapd.socket
   ```

   - **`systemctl`**: A command-line utility used to examine and control the systemd system and service manager.
   - **`enable`**: Configures `systemd` to start the `snapd.socket` service automatically on boot.
   - **`--now`**: Starts the `snapd.socket` service immediately, without requiring a reboot.
   - **`snapd.socket`**: A systemd socket unit file for Snap’s communication. This enables Snapd to listen for Snap requests.

3. **Create a Symbolic Link for Snap**

   ```bash
   sudo ln -s /var/lib/snapd/snap /snap
   ```

   - **`ln`**: The command used to create links between files or directories.
   - **`-s`**: Creates a symbolic link (also known as a symlink) instead of a hard link. A symbolic link is a reference to another file or directory.
   - **`/var/lib/snapd/snap`**: The actual directory where Snap packages are stored.
   - **`/snap`**: The location where the symbolic link is created. This is the directory that Snap applications will use to find and access the Snap packages.

4. **Reboot the System**

   ```bash
   sudo reboot
   ```

   - **`reboot`**: This command restarts the system. Rebooting ensures that all changes (like enabling services and creating symlinks) take effect and that the Snapd service starts correctly.

5. **Install Android Studio via Snap**

   ```bash
   sudo snap install android-studio --classic
   ```

   - **`snap`**: The command-line interface for managing Snap packages.
   - **`install`**: Installs a Snap package.
   - **`android-studio`**: The name of the Snap package for Android Studio.
   - **`--classic`**: This flag indicates that the Snap package should be installed in classic mode, which allows it to access the broader filesystem and system resources, similar to traditional packages. This is necessary for Android Studio as it requires access to a wide range of system resources.

In summary, these commands are setting up Snapd (the Snap package manager) on your Fedora system, enabling it to run properly, and then using it to install Android Studio in classic confinement mode, which is suitable for development environments.
