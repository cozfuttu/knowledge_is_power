/boot : Contains file that is used by the boot loader (grub.cfg).
/root : root user home directory. Not the same as "/".
/dev : System devices (e.g. disk, cdrom, speakers, flash drive, keyboard etc.).
/etc : Configuration files
/bin (now /usr/bin) : everyday user commands
/sbin (now /usr/sbin) : system/filesystem commands
/opt : Optional add-on applications (not part of OS apps)
/proc Running processes (only exist in memory)
/lib (/usr/lib) C programming library files needed by commands and apps (use `strace -e open pwd` for tracing library file used for specified command)
/tmp : temporary files directory
/home : directory for user
/var : system logs
/run : system daemons that start very early (e.g. systemd and udev) to store temporary runtime files like PID files
/mnt : To mount external filesystem (mounting means making a filesystem accesible to user)
/media : for cdrom mounts
![[Screenshot_2024-12-12-17-13-35-993_com.linkedin.android.jpg]]