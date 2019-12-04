# Ubuntu-18.04-BuildserverISO
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


*Once you have a local copy of the repo you can adjust the preseed file as needed.*

## Bake the Golden Image.
Once you have the environment, dependencies and repository in place and you are ready to bake your golden image just run.

```
bash buildserver.sh
```

Enjoy!

