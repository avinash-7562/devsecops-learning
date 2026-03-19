Realtime linux usage:
=====================
Q1. Display line number that ends with word "arch"
A. grep -n "arch$" <filename>

Q2. Display the lines from 3 to 15 in a file
A. head -n 15 <file> | tail -n 12 

Q3. Print user information which are not system users in /etc/passwd
A. [ ec2-user@<ip> ~ ]$ awk -F ":" '$3 >=1000 {print $1, $3}' /etc/passwd
nobody 65534
maintuser 1000
ec2-user 1001
[ ec2-user@<ip> ~ ]$ awk -F ":" '$3 >=1000 {print $1F, $3F}' /etc/passwd
nobody 65534
maintuser 1000
ec2-user 1001

Q4. Print users which has nologin in /etc/passwd
A. [ ec2-user@<ip> ~ ]$ awk -F ":" '$7 == "/sbin/nologin" {print $1, $3}' /etc/passwd
bin 1
daemon 2
adm 3
lp 4
mail 8
operator 11
games 12
ftp 14
nobody 65534
systemd-coredump 999
dbus 81
tss 59
polkitd 994
sssd 993
sshd 74
chrony 992
[ ec2-user@<ip> ~ ]$ awk -F ":" '$NF == "/sbin/nologin" {print $1, $3}' /etc/passwd
bin 1
daemon 2
adm 3
lp 4
mail 8
operator 11
games 12
ftp 14
nobody 65534
systemd-coredump 999
dbus 81
tss 59
polkitd 994
sssd 993
sshd 74
chrony 992
[ ec2-user@ip-172-31-31-187 ~ ]$



