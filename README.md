# Ubuntu-Build-A-Server-ISO
A Linux script that takes a preseed file and bakes it into an Ubuntu ISO for unattended install and configuration.

The preseed file is already configured to install a developer ready LAMPstack and can be used as is or adjusted as necessary.
***

## If you already have Ubuntu.
If you already have Ubuntu up and running you can use the following command to install the software packages the script depends on.

1. Install dependencies.
```
sudo apt install dos2unix p7zip-full cpio gzip genisoimage whois pwgen wget fakeroot isolinux xorriso
```


## If you have Windows 10 but need Ubuntu.
If you have Windows 10 but need a copy of Ubuntu you can use [Techintheclouds/Windows-WSL-Ubuntu-LAMP-Wordpress](https://github.com/Techintheclouds/Windows-WSL-Ubuntu-LAMP-Wordpress) as a jump off point it automatically installs the required dependencies to run the script.

## Once you have Ubuntu.
Once you have a running copy of Ubuntu with the dependencies clone the repo to the desired directory with
***

2. Clone the repo.
```
git clone https://github.com/Techintheclouds/Ubuntu-18.04-BuildserverISO.git
```
***

## Bake the Golden Image.
Once you have the environment, dependencies and repository in place and you are ready to bake your golden image just run the script and it will download the netinstaller and inject the preseed file into the generated ISO.

3. Bake the Golden Image.
```
bash buildserver.sh
```

Enjoy!
***

## Common adjustments you can make.

### Change the release.

*I prefer to change the following three of these together, although in theory the preseed file can tell the netinstaller what release to download.*

#### Change ISO release via net installer source url.

Edit buildserver.sh line 15 from bionic to desired release codename such as bionic, disco, eoan.
*This is the only thing to edit in the script and as stated above in theory isn't completely necessary.*

#### Change release via preseed.

Edit preseed.cfg line 39 with release codename such as bionic, disco, eoan.

#### Change the kernal.

Edit preseed.cfg line 207 with your desired kernal, you should change the version number to match the release and is typically all you need if you plan to keep it virtualized. Otherwise do your due diligence when choosing a kernal.


### Configure networking preseed.cfg lines 17-27.

#### Change Hostname.
Edit preseed.cfg line 20 & 22 with desired hostname.

#### Change static IP Address.
Edit preseed.cfg line 23 to desired IP Address.

#### Change DNS servers.
Edit preseed.cfg line 26 to desired DNS currently it is pointed to Google.

### Configure user preseed.cfg lines 86-91.

#### Set username.
Edit preseed.cfg line 88 & 89 to desired username it's currently set as dev.

#### Set password.
Edit preseed.cfg line 90 this is currently set to password for easy testing, but can and should use an encrypted and salted password. Will contribute more instructions on that soon.
***

### How I made it.
I referenced heavily from [core-process/linux-unattended-installation](https://github.com/core-process/linux-unattended-installation) although that script didn't work for my setup out of the box so I had to research it and understand it, I eventually found what wasn't working for my setup was able to change it, pruned what I didn't deem necessary and studied the debconf output of an already installed system to get some really detailed and intricate settings regarding setting up the LAMPstack and preseed file.


### Why I made it.
It was made from a desire to have a virtual machine that I can spin up quickly for web development pursuits but also have a detailed breakdown of how to configure a LAMPstack that I could reference in the future or use to help others learn. I also built a powershell script that can be pointed to the generated ISO from this script to build a preconfigured Hyper-V Virtual Machine on Windows 10 that will spin up and install the preseeded Ubuntu, you can find that at [Techintheclouds/Windows-Hyper-V-BuildVM](https://github.com/Techintheclouds/Windows-Hyper-V-BuildVM).
