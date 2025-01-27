```bash
1. Install "Remote - SSH extension
2. Open Command > Remote-SSH
3. Create a config as below
4. Copy the pem file (A PEM file (Privacy Enhanced Mail) is a file format that contains cryptographic keys or certificates. It’s commonly used in SSH and TLS/SSL communications)

if not using PEM,  but passwords
IdentityFile is not needed, when commecting it will prompt for password.

Host amps-vm-test-01
  HostName 20.2.153.240
  User azureuser
  IdentityFile "/C:/Users/kalje/.ssh/kaljessy.pem"

5. Remote-SSH: Connect to Host
6. To edit files, user Open folder menu

```

```bash
# COnnect using PEM file from Windows Cmd
ssh -i kaljessy.pem azureuser@20.2.153.240

# Copy files using scp (Secure Copy)
scp -i kaljessy.pem C:\projects\deno\deno-compile\main.exe
       azureuser@20.2.153.240:/home/azureuser/deno

# Change ownership of the /root/amps directory and its contents to azureuser
# - sudo: Run as superuser for administrative privileges
# - chown: Change ownership of files or directories
# - -R: Recursively apply changes to all files and subdirectories
# - azureuser:azureuser: Set both the owner and group to 'azureuser'
sudo chown -R azureuser:azureuser /root/amps

# Add write (w) permission for the owner (user) on the 'deno' directory and its contents
# - sudo: Run as superuser for permission to modify protected files
# - chmod: Change file or directory permissions
# - -R: Recursively apply changes to all files and subdirectories
# - u+w: Add write permission for the owner (user)
sudo chmod -R u+w ./deno

# Add execute (x) permission for the owner (user) on the 'main.exe' file
# - chmod: Change file permissions
# - u+x: Add execute permission for the owner (user)
chmod u+x main.exe
```

# System-wide Program Directories

/usr/bin: Contains most of the user-executable programs (binaries) for system-wide use.
Example: Programs like python, nano, gcc.

/usr/local/bin: For locally installed programs (compiled or manually added by the user).
Not managed by the system's package manager.
Example: Custom-built programs or scripts.

```bash
# Common Directories for Installed Programs:

# 1. System-wide Directories
/usr/bin       # Most user-executable programs (e.g., python, nano)
/usr/local/bin # Locally installed programs (manually or custom-built)
/bin           # Essential system binaries (e.g., ls, cp)
/sbin          # System administration binaries (e.g., ifconfig, fsck)
/usr/sbin      # Additional system administration tools (e.g., apache2)
/opt           # Optional software from third-party vendors (e.g., Chrome)
/lib, /usr/lib # Shared libraries used by installed programs

# 2. User-specific Directories
~/.local/bin   # User-installed programs (e.g., pip install --user)
/~/.bin        # Custom executables created by the user

# 3. Temporary Directories
/tmp           # Temporary files created during runtime (not permanent)

# 4. Package Manager-Specific Directories
/var/lib/<package-manager> # For installed packages via a package manager
/snap                       # Snap packages
/var/lib/flatpak            # Flatpak packages
/home/linuxbrew/.linuxbrew  # Homebrew (Linuxbrew)

# Commands to Locate Installed Programs:

# 1. Locate an installed program
which program_name
# Example: which python

# 2. Find program in the file system
find / -name program_name 2>/dev/null
# Example: find / -name nginx

# 3. List installed packages via package managers:
apt list --installed         # Debian/Ubuntu
rpm -qa                      # RedHat/CentOS
dnf list installed           # Fedora
snap list                    # Snap packages
flatpak list                 # Flatpak packages
brew list                    # Homebrew (Linuxbrew)

# Use Cases:
# - Use /usr/local/bin for custom tools/scripts.
# - Use ~/.local/bin for user-specific installations.
# - Use /opt for third-party software not managed by the system package manager.

```

```

```
