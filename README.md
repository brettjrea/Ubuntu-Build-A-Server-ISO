# Ubuntu-Build-A-Server-ISO
A Linux script that takes a preseed file and bakes it into an Ubuntu ISO for unattended install and configuration.

The preseed file is already configured to install a developer ready LAMPstack and can be used as is or adjusted as necessary.


## If you already have Ubuntu.
If you already have Ubuntu up and running you can use the following command to install the dependencies needed to run the script.

```
sudo apt install dos2unix p7zip-full cpio gzip genisoimage whois pwgen wget fakeroot isolinux xorriso
```


## If you have Windows 10 but need Ubuntu.
If you have Windows 10 but need a copy of Ubuntu you can use [Techintheclouds/Windows-WSL-Ubuntu-LAMP-Wordpress](https://github.com/Techintheclouds/Windows-WSL-Ubuntu-LAMP-Wordpress) as a jump off point it automatically installs the required dependencies to run the script.

## Once you have Ubuntu.
Once you have a running copy of Ubuntu clone the repo to the desired directory with

```
git clone https://github.com/Techintheclouds/Ubuntu-18.04-BuildserverISO.git
```


## Adjustments you can make.

### Change the release.

*I prefer to change the following three of these together, although in theory the preseed file can tell the netinstaller what release to download.*

#### Change ISO release via net installer source url.

Edit buildserver.sh line 15 from bionic to desired release codename such as bionic, disco, eoan.

#### Change release via preseed.

Edit preseed.cfg line 39 with release codename such as bionic, disco, eoan.

#### Change the kernal.

Edit preseed.cfg line 207 with your desired kernal, you should change the version number to match the release and is typically all you need if you plan to keep it virtualized. Otherwise do your due diligence when choosing a kernal.

## Bake the Golden Image.
Once you have the environment, dependencies and repository in place and you are ready to bake your golden image just run.

```
bash buildserver.sh
```

Enjoy!

### How I made it.
I referenced heavily from [core-process/linux-unattended-installation](https://github.com/core-process/linux-unattended-installation) although that repo didn't work for my setup out of the box so I had to research and make some changes. I leaned it down and refrenced other resources regarding preseed files on and off Github to get it working.


### Why I made it.
It was made from a desire to have a virtual machine that I can spin up quickly for web development purposes and couples well with my [Techintheclouds/Windows-Hyper-V-BuildVM](https://github.com/Techintheclouds/Windows-Hyper-V-BuildVM) repo.


