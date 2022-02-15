# Github repo for my installation notes

## Installed packages through apt
- Filezilla
- Bloodhound
- Gobuster
- Xclip
- 
```
sudo apt install filezilla Bloodhound gobuster xclip
```

## Installed tools through pip
- Bloodhound.py
```
pip install bloodhound
```

## Installed tools through gem
```
evil-winrm
```

## Installed tools through git
```
cd /opt
git clone https://github.com/danielmiessler/SecLists
git clone https://github.com/CompassSecurity/BloodHoundQueries
git clone https://github.com/zyn3rgy/LdapRelayScan
```

## Manual tasks
- Run this : https://github.com/Dewalt-arch/pimpmykali
- Download Burp Pro https://portswigger.net/burp/releases/professional-community-2022-1-1?requestededition=professional
  - Run the burp .sh script
- Install Bloodhound
  - ```sudo neo4j start``` and go to http://localhost:7474. Fill in default username and password ```neo4j``` and choose a new password.
  - Set custom queries ```cp /opt/BloodHoundQueries/customqueries.json ~/.config/bloodhound/customqueries.json```
  - Start BloodHound and login with the username ```neo4j``` and the new password.
- Install tmux config
  - ```cd ~/ & wget https://raw.githubusercontent.com/0xJs/tmux.conf/master/.tmux.conf```
- Change terminal opacity
  - Open terminal --> File --> Preferences --> Application transperancy to 0%
- 

