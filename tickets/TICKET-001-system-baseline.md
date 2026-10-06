# TICKET-001 - System Baseline

## Objective
Document the current configuration of my RHEL server before making
additional changes to the system.

## System Information

### Operating System
- RHEL Version: Red Hat Enterprise Linux 10.2 (Coughlan)
- Kernel: 6.12.0-211.49.1.el10_2.x86_64
- Hostname: localhost.localdomain
- Uptime: 5 days, 13 hours, 27 minutes at time of check

## Hardware

### CPU
- Model: Intel Core i5-8350U @ 1.70GHz
- Sockets: 1
- Physical Cores: 4
- Threads per Core: 2
- Logical CPUs: 8

### Memory
- Total RAM: ~15 GiB
- Available RAM: ~13 GiB
- Swap: ~7.7 GiB

## Storage

### Physical Storage
- Primary Disk: nvme0n1
- Size: 476.9G

### Partitions and Filesystems
- nvme0n1p1 - 600M - FAT32/vfat - /boot/efi
- nvme0n1p2 - 2G - XFS - /boot
- nvme0n1p3 - 474.4G - LVM2 member

### LVM
- rhel-root - 70G - XFS - /
- rhel-swap - 7.7G - swap
- rhel-home - 396.6G - XFS - /home

### Filesystem Usage
- / - 70G total, 9.6G used, 61G available
- /home - 397G total, 8.1G used, 389G available
- /boot - 2.0G total, 576M used, 1.4G available
- /boot/efi - 599M total, 9.0M used, 590M available

## Networking

### LAN
- Interface: wlp61s0
- Type: Wi-Fi
- IPv4 Address: 192.168.1.64/24
- Default Gateway: 192.168.1.1
- DNS Server: 192.168.1.1

### Ethernet
- Interface: enp0s31f6
- Status: Disconnected

### Tailscale
- Interface: tailscale0
- IPv4 Address: 100.118.115.5/32

## Running Services

Some important running services discovered during the baseline:

- sshd.service - OpenSSH server
- tailscaled.service - Tailscale node agent
- firewalld.service - Firewall
- NetworkManager.service - Network management
- auditd.service - Security auditing
- chronyd.service - Time synchronization
- crond.service - Scheduled jobs
- rsyslog.service - System logging
- systemd-journald.service - Journal logging

## Commands Learned

- `cat /etc/os-release` - Displays operating system release information.
- `uname -r` - Displays the running kernel release.
- `hostname` - Displays the current hostname.
- `uptime -p` - Displays system uptime in a readable format.
- `lscpu` - Displays CPU architecture and topology information.
- `lscpu -e=MODELNAME` - Displays the CPU model for each logical CPU.
- `free -h` - Displays memory usage in human-readable units.
- `lsblk` - Displays block devices and their relationships.
- `lsblk -f` - Displays block devices with filesystem information.
- `df -h` - Displays mounted filesystem usage in human-readable units.
- `ip address` - Displays network interfaces and IP addresses.
- `nmcli device show` - Displays detailed NetworkManager device information.
- `systemctl list-units --type=service --state=running` - Lists currently running services.

## Problems Encountered

I initially had trouble finding some commands because I was using broad
`apropos` searches. This returned too many results to be useful.

I also learned that command documentation uses symbols such as `<value>`
and `[option]` as placeholders and that they should not always be typed
literally.

While using `lscpu`, I initially confused logical CPUs with physical CPU
cores. I also tried some invalid command options while learning how the
command worked.

## How I Solved Them

I started using each command's `--help` output to understand its available
options instead of trying to guess commands.

Using `lscpu -e` helped me see that eight logical CPUs mapped to four
physical cores, with two threads per core.

I also compared the output of `lsblk`, `lsblk -f`, and `df -h` to better
understand the relationship between physical disks, partitions, LVM
logical volumes, filesystems, and mount points.

## What I Learned

I learned how to collect a basic system baseline on a RHEL server without
changing its configuration.

I learned that Linux storage has multiple layers. My physical NVMe disk
contains partitions, one partition is used by LVM, and LVM provides
logical volumes containing the root, home, and swap storage.

I also learned the difference between physical CPU cores and logical CPUs,
how Linux reports available memory, and how to identify network interfaces,
IP addresses, gateways, DNS servers, and currently running systemd
services.
