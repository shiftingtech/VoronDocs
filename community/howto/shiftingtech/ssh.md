# SSH HOWTO for Voron
in the course of setting up your raspberry pi, you will encounter a series of instructions along the lines of "ssh into your pi", and do something or other.
ssh is a tool used to open a console, and remotely take control of your pi, using a command line environment.
There are a few different tools you can use to do this, depending on what type of computer you are using.

## Windows 10: command line ssh
Windows 10 has ssh built in.  The advantage of this is that it is already available.  the main disadvantage is that it does not have the ability to save session 
profiles in the way that a tool like Putty does

## Windows (all versions): putty
For many years, before windows 10 added built in support for ssh, Putty was the standard tool for windows users to gain access to ssh.  It is still widely used,
as it is a convenient, and slightly more friendly ssh interface.

## MacOS: command line ssh
MacOS has ssh built in.  Although various other tools do exist to expand on ssh's usefulness, none of them are as clear a choice as Putty is on the windows side.
As such, while you are free to explore them, they are beyond the scope of this document

## Other: 
ssh is extremely widely used in computer networking and systems management circles.  There are all sorts of tools for it, on every imagininable platform.
Feel free to explore!

## Find the pi
When your pi first boots, it should be assigned an IP address by your DHCP server. Finding this address is the first step to logging in to your pi.

The easiest test is to open a command prompt (windows) , or a terminal (mac OS), and try to ping it:  when you succeed, you should see ping responses, 
which will look something like:

in many modern networks, mDNS or DHCP->DNS will let us access the pi by hostname, rather than IP, which is much more user friendly.

* mainsailOS: `ping mainsailos.local` or `ping mainsailos`
* fluiddPI: `ping fluiddpi.local` or `ping fluiddpi`
* Octopi: `ping octopi.local` or `ping octopi`

if none of the options above work, it's likely that neither mDNS, nor DHCP->DNS are enabled on your network, and you will need to locate the actual IP address.
In this case, there are a couple of options available.

* One option is to log into your router, and go to it's DHCP page.  In most routers, this will provide a list of all connected devices, and you should be able to locate  your pi on the list.
* Another option is the "Adafruit Pi Finder", which can be downloaded from [github](https://github.com/adafruit/Adafruit-Pi-Finder/releases).
this small piece of software (available for Windows, Mac, and Linux) will scan your network and report back the pi's address.

## Logging in

### Windows 10 (built in):  

* Open the start menu, open "Windows System", and click "Command Prompt".
* type `ssh pi@`, and then the host or ip from the previous step, for example `ssh pi@mainsailos.local`, then press enter.
* on your first login, you will see a prompt similar to: 

```
The authenticity of host 'voron2 (192.168.1.106)' can't be established.
ECDSA key fingerprint is SHA256:sB7+AYXWidh4HgE1VcYwjWGpIOkFtpjxjAL1Qh6BzHo.
Are you sure you want to continue connecting (yes/no)?
``` 

  type `yes`, and press enter
* you will then be prompted for the login password. the default password is "raspberry".  press enter after the password.  
_Note: you will not see anything while you are typing the password.  this is normal and expected_
* you should now be sitting at a "shell prompt" similar to `pi@mainsailos:~ $`.  You are now ready to proceed with whatever you set out to do.

### MacOS 

* Open finder, go to Applications, and to the Utilities folder.  Double click "Terminal"
* type `ssh pi@`, and then the host or ip from the previous step, for example `ssh pi@mainsailos.local`, then press enter.
* on your first login, you will see a prompt similar to: 

```
The authenticity of host 'voron2 (192.168.1.106)' can't be established.
ECDSA key fingerprint is SHA256:sB7+AYXWidh4HgE1VcYwjWGpIOkFtpjxjAL1Qh6BzHo.
Are you sure you want to continue connecting (yes/no)?
``` 

  type `yes`, and press enter
* you will then be prompted for the login password. the default password is "raspberry".  press enter after the password.  
_Note: you will not see anything while you are typing the password.  this is normal and expected_
* you should now be sitting at a "shell prompt" similar to `pi@mainsailos:~ $`.  You are now ready to proceed with whatever you set out to do.


### Putty
* Download [putty](https://www.putty.org) and install it on your computer
* Launch putty from the start menu
* type `pi@` and then the host or ip from the previous step, for example `pi@mainsailos.local` in the Host Name field
* press the "open"  button
* on first connect, you will receive a warning "the server's host key is not cached..."  Press Yes to continue.
* you will then be prompted for the login password. the default password is "raspberry".  press enter after the password.  
_Note: you will not see anything while you are typing the password.  this is normal and expected_
* you should now be sitting at a "shell prompt" similar to `pi@mainsailos:~ $`.  You are now ready to proceed with whatever you set out to do.

## Misc Tips and Tricks

* Pressing the up arrow will bring back your last command, and allow you to edit it
* In putty, copying from the ssh session is accomplished simply by highlighting some text.  It will immediately be copied to the clipboard
* in Windows 10 ssh, copying from the ssh session is accomplished by highlighting some text, and then right-clicking. 
* In both windows based tools, pasting into the ssh session is accomplished simply by right-clicking in the terminal window
* As a command line interface, each command you enter only actually does anything after you press "enter".  most instructions take this as a given, and do not actually mention it.
 _Note that if you're copying and pasting a list of commands from another document, this will tend to just happen, as a result of the carriage returns in the document_
* It is generally a bad idea to leave a pi sitting on your network with the default password set.  You can change the password by logging in, and then entering the command `passwd`

