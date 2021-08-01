# Write-up

This challenge was started with an SSH connection to the host in a restricted shell(rbash)
Trying out multiple commands.. you can find out the `echo` command is available

`echo *` to find the directories in pwd and then `echo step1/*`

You will find vim which is a hint to gain priveleges using that particular command


For most of this challenge we will be using the valuable resource GTFObins which is a compilation of privelege escalation techniques with many binaries

So we use it for vim and get out of the rbash and forward slash restriction... Now according to the challenge we use `sudo -l` to check the available commands we can run as root


So we just keep implementing the techniques from the GTFObins site while making some tweaks of our own (`sudo -u app-script-ch14-x`) 

A few things to be noted:

-use a $TF variable to execute git otherwise the next level will not work

-make a c file and Makefile for the make command

The last level is a bit different where you have to use `compgen -C` to list available commands and try out each to escape from the rbash

Or as I did it

`p=$(>"echo ../.passwd")`

echo $p
