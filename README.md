# connect2ssh

This open source and freely available tool is written to run in the BASH shell and allows for management and connection to computers via SSH and SSHFS via key file(s) and/or password(s) without compromising security. It also requires zero system configuration file changes, uses standard well known libraries, is easily removed, and even portable.

More information: [https://www.cyberws.com/bash/connect2ssh/](https://www.cyberws.com/bash/connect2ssh/)

Need help using Connect2SSH? [Youtube Instruction Videos](https://www.youtube.com/watch?v=gQsglNH-w4M&list=PL7DdW0jxJRrGbjomR6bgwmyeRUvt7jHOT)

----

## Updates

* Follow this page
* [Follow on Youtube](https://www.youtube.com/channel/UCeQtI9fcAapQkiHph42NjWA)
* [Follow on Facebook](https://www.facebook.com/cyberwscom/)

## Contribute/Contact

If contacting for technical support please see video manuals first.  I'll do my best to help troubleshoot but can't make any promises due to limited time.

Contributors please see the "[Contributors Readme](contributors.md)" for important information.

* Message through Github
* [Contact Form on CyberWS](https://www.cyberws.com/contact-us/)

## Installing

This is a very easy utility to install.  You simply need to put the file **connect2ssh** on your system and turn on executable permissions like chmod 700 or 755.  It is suggested you place the file in either **/home/YOUR_USER/bin/** or **/usr/local/bin/** depending on who you want using this program.  Once that step has been done simply run the command from the commandline.

Now run the utility which will setup the necessary files and database (SQLite3)

shell> **connect2ssh**

To bring up a list of commands:

shell> **connect2ssh help**

### Removing

What? You want to remove Connect2SSH? Why!? :-(

1) Remove the **connect2ssh** file itself; where ever you installed it.  If necessary use whereis or find commands to locate the file.
2) Now delete the directory **/home/YOUR_USER/.config/connect2ssh** - it may be necesssary to remove /.config/connect2ssh from other users' home directories.  It depends on if other users ran the command.
3) Done.  Now reinstall it right? ;-)

## Customizing

#### How do I move and/or change the SQLite database?

By using your favorite text editor open "**~/.config/connect2ssh/config**” and set the variable **DB_FILE_PATH** to the new SQLite directory with filename.  Then save, close, and rerun the connect2ssh command.  Also you should note permissions matter so make sure your user can read and write changes to the new location. If things go wrong you can restore from a backup or simply delete the config file and connect2ssh should regenerate it.

Example:

DB_FILE_PATH=”/opt/sqlite/c2s.db” 

## Syncing & Encryption

#### Is it possible to sync the Connect2SSH database?

Absolutely!  You could put the Connect2SSH database on a remote system if desired.  You could use syncthing (see how to move the SQLite database), use rsync, use the simple cp command, etc.  You could share the same database among multiple machines or even users.  This page will not get into the complex world of syncing but yes it is possible with various solutions and methods.

#### How can I protect the database?

You could encrypt the SQLite database if desired.  Of course to use Connect2SSH you would have to decrypt the data.  This is an involved process and beyond the scope of this page, however one simple method is to use gpg.

## General

#### Where does Connect2SSH store the configuration data?

**~/.config/connect2ssh/** or another way to put it **[user’s home directory]/.config/connect2ssh/**

#### Since SQLite is used can I open it with SQLite management programs?

Of course!  However becareful when modifying the database as you could render the data useless to this tool.  It is highly recommended you backup the database file before making changes or even viewing it.  If the database becomes corrupted and you don’t have a backup then delete the database file and Connect2SSH will generate a new one.  Of course you’ll lose your data in this case.

#### What is this nohup.out file?

It is the nohangup output file so SSHFS connections aren’t terminated when started by Connect2SSH.  It is harmless.  You may delete it but it will just come back when you generate new SSHFS connections.  In most situations it should remain completely empty.  Yes output could be redirected to /dev/null but a file was chosen just in case of troubleshooting and again it is just a simple file so it isn’t taxing your system.

