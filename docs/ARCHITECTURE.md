# Detailed Lab System and Specifications Report
Generated on: May 23, 2026

---

## Host: Kali Station (Local)
### System Status
Linux kali 6.19.14+kali-amd64 #1 SMP PREEMPT_DYNAMIC Kali 6.19.14-1+kali1 (2026-05-05) x86_64 GNU/Linux
PRETTY_NAME="Kali GNU/Linux Rolling"
 19:26:44 up 3 days, 21:52,  1 user,  load average: 2.11, 2.45, 2.60
### Hardware Specifications
Model name:                              Intel(R) Xeon(R) CPU E5-2630 v4 @ 2.20GHz
Mem:            62Gi        17Gi        12Gi       753Mi        34Gi        45Gi
/dev/sda1       909G  713G  151G  83% /
### Network Configuration
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet 127.0.0.1/8 scope host lo
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet <KALI_IP>/24 brd 10.0.0.255 scope global dynamic noprefixroute eth0
11: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    inet <GATEWAY_IP>/24 brd 10.42.0.255 scope global noprefixroute wlan0

## Host: Arch Cluster (<ARCH_CLUSTER_IP>)
### System Status
Linux archlinux 7.0.5-zen1-1-zen #1 ZEN SMP PREEMPT_DYNAMIC Fri, 08 May 2026 09:29:10 +0000 x86_64 GNU/Linux
PRETTY_NAME="Arch Linux"
 19:26:47 up 2 days,  1:39,  6 users,  load average: 1.80, 1.85, 1.93
### Hardware Specifications
Model name:                              Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz
Mem:            15Gi       1.8Gi       6.3Gi       222Mi       7.9Gi        13Gi
/dev/sda2       119G   93G   24G  80% /
### Network Configuration
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet 127.0.0.1/8 scope host lo
11: wlan2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    inet <EXTERNAL_NETWORK_IP_1>/24 brd 192.168.7.255 scope global wlan2
    inet <ARCH_CLUSTER_IP>/24 brd 10.42.0.255 scope global noprefixroute wlan2

## Host: Raspberry Pi (<RASPBERRY_PI_IP>)
### System Status
Linux pi-hole 6.12.75+rpt-rpi-v8 #1 SMP PREEMPT Debian 1:6.12.75-1+rpt1 (2026-03-11) aarch64 GNU/Linux
PRETTY_NAME="Debian GNU/Linux 13 (trixie)"
 19:26:50 up 3 days, 21:55,  4 users,  load average: 0.11, 0.19, 0.08
### Hardware Specifications
Model name:                              Cortex-A53
Mem:           905Mi       313Mi        42Mi        10Mi       625Mi       592Mi
/dev/mmcblk0p2   29G   20G  8.0G  71% /
### Network Configuration
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet 127.0.0.1/8 scope host lo
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet <EXTERNAL_NETWORK_IP_2>/24 brd 192.168.7.255 scope global dynamic noprefixroute wlan0
4: wlan1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    inet <RASPBERRY_PI_IP>/24 brd 10.42.0.255 scope global dynamic noprefixroute wlan1

## Host: Canwork189 (<CANWORK_IP>)
### System Status
Linux canwork189 5.15.0-139-generic #149~20.04.1-Ubuntu SMP Wed Apr 16 08:29:56 UTC 2025 x86_64 x86_64 x86_64 GNU/Linux
PRETTY_NAME="Ubuntu 20.04.6 LTS"
 19:27:07 up 25 min,  2 users,  load average: 0.00, 0.05, 0.15
### Hardware Specifications
Model name:                           AMD FX(tm)-8320 Eight-Core Processor
Mem:          7.2Gi       1.3Gi       4.1Gi        11Mi       1.8Gi       5.6Gi
/dev/sdd1        46G   24G   20G  56% /
### Network Configuration
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet 127.0.0.1/8 scope host lo
3: wlx00a1b0501d50: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    inet <CANWORK_IP>/24 brd 10.42.0.255 scope global dynamic noprefixroute wlx00a1b0501d50

## Host: Dell Precision (<DELL_PRECISION_IP>)
### System Status
Linux DESKTOP-JGPTREA 6.6.114.1-microsoft-standard-WSL2 #1 SMP PREEMPT_DYNAMIC Mon Dec  1 20:46:23 UTC 2025 x86_64 x86_64 x86_64 GNU/Linux
PRETTY_NAME="Ubuntu 24.04.4 LTS"
 19:27:11 up 50 min,  3 users,  load average: 0.15, 0.40, 0.95
### Hardware Specifications
Model name:                           Intel(R) Xeon(R) CPU E5-1603 v3 @ 2.80GHz
Mem:            15Gi       1.6Gi       5.3Gi       4.0Mi       8.9Gi        13Gi
/dev/sdd       1007G   24G  933G   3% /
### Network Configuration
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet 127.0.0.1/8 scope host lo
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    inet <EXTERNAL_NETWORK_IP_3>/20 brd 172.27.31.255 scope global eth0
