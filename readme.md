# Github repo for my installation notes

## First step


## Installed packages through apt
- Filezilla
- Bloodhound
- Gobuster
```
sudo apt install filezilla Bloodhound gobuster
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
```


## Manual tasks
- Run this : https://github.com/Dewalt-arch/pimpmykali
- Download Burp Pro https://portswigger.net/burp/releases/professional-community-2022-1-1?requestededition=professional
  - Run the burp .sh script
- Install Bloodhound
  - ```sudo neo4j start``` and go to http://localhost:7474. Fill in default username and password ```neo4j``` and choose a new password.
  - Set custom queries ```cp /opt/BloodHoundQueries/customqueries.json ~/.config/bloodhound/customqueries.json```
  - Start BloodHound and login with the username ```neo4j``` and the new password.
- 
