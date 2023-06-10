The FHS (Filesystem Hierarchy Standard) is maintained by the Linux foundation, and much like the other standards is a recommended standard so that the code written for one Linux distribution will be cross compatible with another.

Primarily, the FHS is a way of organizing user, program, and system files in a tree-like hierarchy, which makes it easy for us to install, uninstall, and find specific files.

#### Important Directories

*'/' aka root*
Our tree starts from '/', the root. No matter what device a file is on, it will be accessible from the root directory. Root is the highest level of the hierarchy and everything falls underneath it.

We can access information on the FHS with `man file-hierarchy`.

*/root/*
The home directory of the root user. The root user's home directory is located outside of `/home/` in order to make sure the root user may log in without `/home/` being available and mounted.

*/boot/*
The boot partition used for bringing up the system. On EFI systems, this is possibly the EFI System Partition (ESP).
This directory is, usually, strictly local to the host, and should be  considered read-only, except when a new kernel or boot loader is installed. This directory only exists on systems that run on physical or emulated hardware that required boot loaders.

*/usr/bin/*
Binaries and executables for user commands that shall appear in the **$PATH** search path. It is recommended to not place binaries in this directory that are not useful for invocation from a shell (such as daemon binaries); these should be placed in a sub-directory of `/use/lib/` instead.

*/bin/, /sbin/, /usr/sbin/*
These compatibility symlinks point to `/usr/bin/`, ensuring that scripts and binaries referencing these legacy paths correctly find their binaries

*/etc/*
System-specific configuration. This directory may or may not be read-only. Frequently, this directory is pre-populated with vendor-supplied configuration files, but applications should not make assumptions about this directory being fully populated or being populated at all, and should fall back to default if the configuration is missing.

*/home/*
The location for normal user's home directories. Possibly shared with other systems and never read-only. This directory and possibly the directories contained within it might only become available or writable in late boot or even only after authentication. Applications should generally not reference this directory directly, but via the per-user **$HOME** environment variable, or via the home directory field of the user database.

*/usr/lib/*
Static, private vendor data that is compatible with all architectures. Note that this includes internal executables or other binaries that are not regularly invoked from a shell.Such binaries may be for any architecture supported by the system.

*/lib/*
This compatibility symlink points to `/usr/lib/`. 

*/usr/*
Vendor-supplied operating system resources. Usually read-only, but this is not required. Possibly shared between multiple hosts. This directory should not be modified by the administrator, except when installing or removing vendor-supplied packages.

*/var/*
Persistent, variable system data. Writable during normal system operation. This directory might be pre-populated with user vendor-supplied data, but applications should be able to reconstruct necessary files and directories in this sub-hierarchy should they be missing, as the system might start up without this directory being populated. Persistency is recommended, but optional, to support ephemeral systems. This directory might become available or writable only very late during boot. Components that are required to operate during early boot hence shall not unconditionally rely on this directory.

*/tmp/*
The place for small temporary files. This directory is usually mounted as "tmpfs" instance, and should hence not be used for larger files. (Use `/var/tmp/` for larger files.) This directory is usually flushed at boot-up. Also files that are not accessed within a certain time may be deleted.