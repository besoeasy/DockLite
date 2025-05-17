Dock Lite

Folder: /home/jesus/docklite/downloads

Steps

Install Samba
sudo apt update && sudo apt install samba


Set Folder Permissions
sudo chmod -R 777 /home/jesus/docklite/downloads


Configure SambaEdit /etc/samba/smb.conf:
sudo nano /etc/samba/smb.conf

Add to [global] section:
[global]
security = user
map to guest = bad user

Add [downloads] section:
[downloads]
path = /home/jesus/docklite/downloads
read only = no
browsable = yes
public = yes
guest ok = yes
force user = jesus
create mask = 0777
directory mask = 0777

Save and exit: Ctrl+O, Enter, Ctrl+X

Restart Samba
sudo systemctl restart smbd


Access ShareUse smb://<RaspberryPi_IP>/downloads in:

File explorers
VLC Android (ensure Settings > Advanced > "Prefer SMB 1" is unchecked)



Troubleshooting

If VLC Android fails, add as favorite: smb://<RaspberryPi_IP>/downloads, leave username/password blank.
Verify access with apps like FX File Explorer.
Ensure folder permissions: sudo chmod -R 777 /home/jesus/docklite/downloads

Notes

Replace <RaspberryPi_IP> with your Pi's IP address.
Share is fully anonymous; no credentials required.
Tested for compatibility with VLC Android.

