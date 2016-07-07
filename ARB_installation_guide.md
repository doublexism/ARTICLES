### ARB Installation from Binary on Ubuntu 16.04
#### Step 1 _Download .tar and .sh files_
[ARB Download: You do not need to download manually, just follow the instructions](http://download.arb-home.de/release/latest/)
* .tar file contains the binary files to install
* .sh file is the installation script

**Create a new directory to hold the downloaded files**
```
$ cd ~/Downloads/
$ mkdir arb_download
$ cd arb_download/
```
**Defining local path variables**
```
$ path=http://download.arb-home.de/release/latest/
$ file=arb-6.0.5.ubuntu1604-amd64.tgz
$ shfile=arb_install.sh
```
**Begin downloading the files**
```
$ wget $path$file
$ wget $path$shfile
```
#### Step 2 _Run the .sh file_
**Run the .sh file**

```
$ sh arb_install.sh
```
**Follow the instructions printed out on the terminal**  
1. Enter a path where the arb to be installed. I used the path "/Home/Xiao/ARB".  
2. Choose stand along if no other users on your computer are using ARB.  
3. Choose 1 for the very last option.  
> modify the .bashrc or .profile files.

**Open .bashrc file**  
```
$ vim ~/.bashrc
```
**Add the following lines to the end of Your .bashrc file**  
```
ARBHOME=/home/xiao/arb;export ARBHOME
LD_LIBRARY_PATH=${ARBHOME}/lib:${LD_LIBRARY_PATH}
export LD_LIBRARY_PATH
PATH=${ARBHOME}/bin:${PATH}
export PATH
```
#### Step 3 Specify the location of libxm.so.4 file
You may still fail to launch arb after installation. You will need to link libxm3 to libxm4 to fix it.  
**Login as super user and link in the mode of superuser**
```
$ sudo -i
$ cd /usr/lib/
$ ln -s LibXm.so.4 libXm.so.3
$ exit
```
**Now run arb on terminal, you shall have the ARB gui prompt out.**
```
$ arb
```
## **HAPPY ARBBING!**
