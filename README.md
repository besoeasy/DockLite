```markdown
# Dock Lite Setup

**Folder**: `/home/$USER/docklite/downloads`

## Steps

### 1. Install Samba
```bash
sudo apt update && sudo apt install samba
```

### 2. Set Folder Permissions
```bash
sudo chmod -R 777 /home/$USER/docklite/downloads
```

### 3. Configure Samba
Edit `/etc/samba/smb.conf`:
```bash
sudo nano /etc/samba/smb.conf
```

Add `[downloads]` section:
```
[downloads]
path = /home/$USER/docklite/downloads
read only = no
browsable = yes
public = yes
guest ok = yes
force user = $USER
create mask = 0777
directory mask = 0777
```

Save and exit: `Ctrl+O`, `Enter`, `Ctrl+X`

### 4. Restart Samba
```bash
sudo systemctl restart smbd
```
```
