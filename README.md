# Arch Linux Install Guide
## Part 1: Getting ISO File
The first thing I did was go to [archlinux.org](https://archlinux.org/download/) and download an ISO file.
After downloading and verifying the integrity of the file, I went to VMware Workstation and created a new VM using the ISO file.
## Part 2: Using Arch Linux while in ISO file
When I first booted up the file I wasn't connected to the internet.\
I tried 
```
systemctl start iwd
```

then
```
iwctl
```
to find my network station, but no stations were visible. \
I started to look for different things that could cause this and started changing my network setting when booting into VMware Workstation itself. When I switched the Network Adapter to Bridged and didn't check the box that says Replicate physical connection state, my VM was connected to the internet. I think this was because of my ethernet. \
After fixing my internet issue i used
```
archinstall
```
This brought me to the installation page where I could set everything up for the installation \
The important things the archinstall page includes \
- Boot loader
- User Accounts
- Profile
- Additional packages
\
\
I chose grub as my boot loader \
I added my 3 users and set them to root level and added their passwords here \
I chose Desktop as my Profile and chose Gnome for my DE \
I installed Firefox in my additional packages
After selecting everything I wanted I pressed install \
## Part 3: Post Installation
When installation was finished I entered
```
pacman -s gnome
```
then pressed yes \
Next I had to use 
```
exit
```
then 
```
shutdown -h
```
This shuts down the VM \
I then load back in and my DE was active \
Next I did some upkeep on the machine \
I made the codi user and justin user need to change their password on their next login with
```
sudo passwd --expire username
```
I was still in bash at this point so I installed zsh with
```
sudo pacman -s zsh
```
I set up the settings for it then set it as my default with
```
chsh -s /bin/zsh
```
Finally I added some aliases to my terminal and added a color prompt \
Figuring out how to make these changes permanent took me awhile but I eventually did it by using
```
sudo nano `/.zshrc
```
to get into the file and put the changes in there \
the alias layout was
```
alias varname='command'
```


