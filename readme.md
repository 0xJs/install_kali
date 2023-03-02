Installation notes from when I install Kali machine for penetration testing. Focussing on On-Prem Active Directory and Infrastructur. I wrote these notes down so it is easier to reinstall my system. Posted it publicly as inspiration for others. If you have any good tool recommendations feel free to DM me on discord 0xjs#9027.

# Install Kali

#### Todo
- Keep adding stuff along the way I install stuff
- Next time reinstalling running more with git clone and copying tools out so updating tools is easier with ```sudo gitup --add /opt```

## Installed packages through apt
- Filezilla
- Bloodhound
- Gobuster
- Xclip
- sshuttle
- python3-git-repo-updater
```
sudo apt install filezilla bloodhound gobuster xclip sshuttle python3-git-repo-updater sshpass python3.10-venv jq build-essential nodejs npm

npm install -g terminalizer
```

## Installed tools through pip
- Bloodhound.py
- Virtualenv
- mssql-cli
```
pip3 install bloodhound virtualenv mssql-cli
```

## Installed tools through gem
```
sudo gem install evil-winrm
```

## Installed tools through git
```
sudo chown -R user:user /opt/
cd /opt
git clone https://github.com/danielmiessler/SecLists
curl https://raw.githubusercontent.com/CompassSecurity/BloodHoundQueries/master/BloodHound_Custom_Queries_Merger/bloodhound-customqueries-downloader | bash

# Windows dir
mkdir windows && cd /opt/windows
wget https://github.com/ropnop/kerbrute/releases/download/v1.0.3/kerbrute_linux_amd64 -O kerbrute && chmod +x kerbrute
git clone https://github.com/zyn3rgy/LdapRelayScan
mkdir sysinternals && cd sysinternals && wget https://download.sysinternals.com/files/SysinternalsSuite.zip && unzip SysinternalsSuite.zip && rm -rf SysinternalsSuite.zip && cd ../
git clone https://github.com/WazeHell/sam-the-admin
git clone https://github.com/bb00/zer0dump
git clone https://github.com/topotam/PetitPotam
git clone https://github.com/dirkjanm/krbrelayx
git clone https://github.com/dirkjanm/mitm6
git clone https://github.com/Greenwolf/ntlm_theft
git clone https://github.com/Hackndo/WebclientServiceScanner && sudo python3 /opt/WebclientServiceScanner/setup.py install
git clone https://github.com/nccgroup/Change-Lockscreen
git clone https://github.com/login-securite/DonPAPI; cd DonPAPI; python3 -m pip install -r requirements.txt; cd ../


# Privesc section
cd /opt && mkdir privesc && cd privesc && mkdir windows && mkdir linux
cd /opt/privesc/windows && wget https://raw.githubusercontent.com/carlospolop/PEASS-ng/master/winPEAS/winPEASbat/winPEAS.bat 
cd /opt/privesc/ && git clone https://github.com/carlospolop/PEASS-ng
wget https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/master/Privesc/PowerUp.ps1
wget https://github.com/r3motecontrol/Ghostpack-CompiledBinaries/raw/master/Seatbelt.exe
wget https://github.com/r3motecontrol/Ghostpack-CompiledBinaries/raw/master/SharpUp.exe
wget https://github.com/itm4n/PrintSpoofer/releases/download/v1.0/PrintSpoofer32.exe
wget https://github.com/itm4n/PrintSpoofer/releases/download/v1.0/PrintSpoofer64.exe
wget https://github.com/ohpe/juicy-potato/releases/download/v0.1/JuicyPotato.exe
https://github.com/carlospolop/PEASS-ng/releases/download/20220214/winPEASx86.exe
wget https://github.com/carlospolop/PEASS-ng/releases/download/20220214/winPEASx64.exe
git clone https://github.com/bitsadmin/wesng --depth 1 && cd wesng && python3 wes.py --update && cd ../
cp /opt/windows/sysinternals/accesschk64.exe .
cp /opt/windows/sysinternals/accesschk.exe .

cd /opt/privesc/linux
git clone https://github.com/rebootuser/LinEnum && cp LinEnum/LinEnum.sh .  && rm -rf LinEnum
git clone https://github.com/diego-treitos/linux-smart-enumeration && cp linux-smart-enumeration/lse.sh . && rm -rf linux-smart-enumeration
wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh && chmod +x linpeas.sh
wget https://github.com/DominicBreuker/pspy/releases/download/v1.2.0/pspy64
wget https://github.com/DominicBreuker/pspy/releases/download/v1.2.0/pspy32 && chmod +x pspy*
git clone https://github.com/jondonas/linux-exploit-suggester-2

# Covenant install rastamouse
cd /opt && wget -q https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
sudo apt -y update
sudo apt -y install apt-transport-https dotnet-sdk-3.1 dnsutils
rm packages-microsoft-prod.deb
git clone --recurse-submodules https://github.com/ZeroPointSecurity/Covenant.git /opt/Covenant
cd /opt/Covenant/Covenant && dotnet build

# Buffer overflow
cd /opt && mkdir bufferoverflow && cd bufferoverflow
wget https://raw.githubusercontent.com/0xJs/Pentesting_cheatsheet/main/infrastructure/bufferoverflow/fuzzing.py
wget https://raw.githubusercontent.com/0xJs/Pentesting_cheatsheet/main/infrastructure/bufferoverflow/exploit.py
```

## Manual tasks
- Run this : https://github.com/Dewalt-arch/pimpmykali
- Change terminal opacity
  - Open terminal --> File --> Preferences --> Application transperancy to 0%
- Download Burp Pro https://portswigger.net/burp/releases#professional
  - Run the burp .sh script
- Install Bloodhound
  - ```sudo neo4j start``` and go to http://localhost:7474. Fill in default username and password ```neo4j``` and choose a new password.
  - Start BloodHound and login with the username ```neo4j``` and the new password.
- Install tmux config
  - ```cd ~/ & wget https://raw.githubusercontent.com/0xJs/tmux.conf/master/.tmux.conf```
- Configure Burp
  - Download https://github.com/yeswehack/PwnFox/releases/tag/v1.0.3 and add it to burp
  - Download the pwnfox browser extension https://github.com/yeswehack/PwnFox
  - Browsw to ```http://burp``` and install the certificate in Firefox 
- Portproxy
  - Install portproxy firefox addon. 

## Cleanup
```
# Cleanup
rm -rf /opt/pimpmykali
mkdir /opt/kali && mv /opt/BloodHoundQueries /opt/kali
```

#### Update github repos in /opt
```
sudo gitup --add /opt
```

