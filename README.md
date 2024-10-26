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
to find my network station, but no stations were visible.\
I started to look for different things that could cause this and started changing my network setting when booting into VMware Workstation itself. When I switched the Network Adapter to Bridged and didn't check the box that says Replicate physical connection state, my VM was connected to the internet. I think this was because of my ethernet.\
After fixing my internet issue i used
```
archinstall
```
This brought me to the installation page where I could set everything up for the installation\
