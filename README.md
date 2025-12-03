Linux Fundamentals & System Hardening Lab

This project is a Linux learning lab built inside an Ubuntu virtual machine.
The goal of this was to practice Linux skills learned from Tryhackme.com and coursework as well as some system hardening techniques I learned about as well. 

The project includes users and groups, file permissions, system services, firewall configuration, basic security hardening, Bash scripting, and screenshots documenting each step.

Environment:

* Host: Windows

* Virtualization: VirtualBox

* Guest OS: Ubuntu 24.04 LTS

* Working User: analyst (non-root user with sudo)

Documentation: Commands, configurations, and screenshots included


1. Users & Groups

I created a non-root user, added them to a group called "security-team", gave them sudo access, and validated group membership.

Key tasks:

* Created a user (analyst)
* Created a group (security-team)
* Added user to sudo
* Verified user/group info

Commands:

* sudo adduser analyst

* sudo groupadd security-team

* sudo usermod -aG security-team analyst

* sudo usermod -aG sudo analyst

* id analyst

Screenshots:

Output of id analyst:

<img width="1280" height="800" alt="Screenshot from 2025-11-26 17-44-42" src="https://github.com/user-attachments/assets/f16fd783-9228-42b9-ac1d-ea452f98832f" />

Successful sudo test:

<img width="1280" height="800" alt="Screenshot from 2025-11-26 17-46-16" src="https://github.com/user-attachments/assets/1a90c0ae-c7ff-45cf-bf0e-c2892fabdb40" />

Group membership:

<img width="622" height="246" alt="Screenshot 2025-12-03 135011" src="https://github.com/user-attachments/assets/08ae1965-33fe-4dfb-bc01-a84adb1c8263" />




2️. File Permissions & Ownership

I practiced reading, changing, and managing permissions using chmod and chown.

Key tasks:

* Created a test lab directory

* Created files with sensitive data

* Locked down file permissions

* Created a shared team directory with setgid

Commands:

* chmod 600 secret.txt

* chmod 640 shared.txt

* sudo chown root:security-team shared.txt

* sudo chmod 2770 /srv/security-share

Screenshots:

Output of section:

<img width="1280" height="800" alt="Screenshot from 2025-11-26 17-52-57" src="https://github.com/user-attachments/assets/7635d904-7b26-4bf1-93d9-3828a26e432a" />

3. Managing Services 

I explored system services, checked their status, enabled/disabled them, and reviewed logs.

Key tasks:

* Checked SSH service

* Installed and enabled OpenSSH

* Viewed systemd logs

Commands:

* systemctl status ssh

* sudo systemctl start ssh

* sudo systemctl enable ssh

* journalctl -u ssh --since "today"

Screenshots:

SSH Status/Install:

<img width="1280" height="800" alt="Screenshot from 2025-11-26 17-55-48" src="https://github.com/user-attachments/assets/5b5f4b9f-ff95-4f15-9da1-bb3865c834d5" />


systemctl enable/start ssh:

<img width="654" height="137" alt="Screenshot 2025-12-03 140239" src="https://github.com/user-attachments/assets/b995476e-4b06-4d4f-bfb5-9709fffa605e" />

journalctl:

<img width="657" height="55" alt="Screenshot 2025-12-03 140539" src="https://github.com/user-attachments/assets/f65083d9-7eda-41ad-be40-0e31beb99b9e" />


4. Firewall Configuration (UFW)

I hardened the firewall using a deny-by-default posture and only allowed necessary traffic.

Key tasks:

* Set default rules

* Allowed SSH

* Enabled firewall

* Exported rules

Commands:

* sudo ufw default deny incoming

* sudo ufw default allow outgoing

* sudo ufw allow OpenSSH

* sudo ufw enable

* sudo ufw status numbered

Screenshots:

Firewall Status, Rules, Enable Confirmation:

<img width="656" height="316" alt="Screenshot 2025-12-03 141115" src="https://github.com/user-attachments/assets/e5a78514-f8b0-4396-bc26-fce0e0d15e68" />

5️. Basic System Hardening

I modified SSH settings, enabled automatic updates, and checked system authentication logs.

Key tasks:

* Disabled root SSH login

* Backed up SSH config

* Enabled unattended upgrades

* Monitored /var/log/auth.log

Commands:

* sudo nano /etc/ssh/sshd_config

* sudo systemctl restart ssh

* sudo apt install -y unattended-upgrades

* sudo tail -n 50 /var/log/auth.log

Screenshots:

sshd-config.png:

<img width="1280" height="800" alt="Screenshot from 2025-12-03 14-22-48" src="https://github.com/user-attachments/assets/eb700f7b-69b6-4ada-9382-de3d6d5e34c6" />


SSH restart, Unattended Upgrades & Logs:

<img width="1280" height="800" alt="Screenshot from 2025-12-03 14-22-48" src="https://github.com/user-attachments/assets/4a205588-83f4-4c14-8705-bed823954ee5" />
<img width="1280" height="800" alt="Screenshot from 2025-12-03 14-22-57" src="https://github.com/user-attachments/assets/1d7b1f23-7817-480e-9f83-04fc7b9c1235" />
<img width="1280" height="800" alt="Screenshot from 2025-12-03 14-23-07" src="https://github.com/user-attachments/assets/eda897b6-7695-49a8-94e8-58bc70c4ade7" />

6. Bash Automation Scripts

I wrote three Bash scripts to automate common system audits.

Scripts:

* user_audit.sh — checks logged-in users + sudo group

* permissions_audit.sh — lists permissions in a folder

* firewall_status.sh — displays firewall rules

Screenshots:

Scripts: 

<img width="1280" height="800" alt="Screenshot from 2025-11-26 18-22-53" src="https://github.com/user-attachments/assets/d614a3f3-1aa6-421f-911d-a9a9f45ba78c" />

What I Learned:

* How to manage Linux users, groups, and privileges

* How Linux file permissions control access

* How systemd manages critical system services

* How to configure and verify UFW firewall rules

* Why SSH hardening is important

* How to automate system checks with Bash

* How to document, structure, and present cybersecurity labs

* How to take clean screenshots that support technical work


My Next Steps:

This lab sets me up for:

Network scanning & enumeration (Nmap)

Vulnerability scanning

SSH key authentication

Log analysis

Mini SOC project
