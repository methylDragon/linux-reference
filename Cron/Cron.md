# Cron Tutorial

Author: methylDragon  
Cron!    

------

## Introduction

Cron is a way of automating tasks to run every hour/day/month, or even on reboot!

> **Cron:** Cron comes from chron, the Greek prefix for ‘time’. Cron is a daemon which runs at the times of system boot.
>
> **Crontab:** Crontab (CRON TABle) is a file which contains the schedule of cron entries to be run and at specified times. File location varies by operating systems.
>
> **Cron job or cron schedule:** Cron job or cron schedule is a specific set of execution instructions specifying day, time and command to execute. crontab can have multiple execution statements.
>
> Source: <http://www.adminschoice.com/crontab-quick-reference>



## Check Cron

###  Check if Cron is Active

On Ubuntu

```shell
$ service cron status

# Might need to restart it
$ service cron stop
$ service cron start
```

On General Linux

```shell
$ service cron status

# Might need to restart it
$ service cron stop
$ service cron start
```

Note:

Ensure that cron is within `/etc/init.d` so you know it starts up on boot!



### Cron Commands

```shell
# List cronjobs
$ crontab -l

# Edit crontab
$ crontab -e

# Remove crontab
$ crontab -r

# Display last edit (available on a few systems only)
$ crontab -v
```



## Set Up Cron

### By Directory

Place the scripts you run in the very self-explanatory directories!

- /etc/cron.hourly/
- /etc/cron.daily/
- /etc/cron.weekly
- /etc/cron.monthly/

Scripts placed in this locations will be run **as root** hourly, daily, weekly, or monthly!



### By Crontab

**DO NOT EDIT CRONTABS MANUALLY! ALWAYS DO IT USING THE CRONTAB TOOL.**

If you don't then the daemon won't update!



#### **Edit Cronfile**

Use the edit command to edit the crontab as a user

```shell
$ crontab -e
```

Use `sudo crontab` to edit the crontab for root

```shell
$ sudo crontab -e
```

**Note:** Make sure any script you want to run has executable permissions set!



#### **Cronjob Format**

Cronjob listings follow this format. They run when the system clock hits the number listed.

Eg. 0 * * * * sets an hourly task that runs at the start of every hour

![crontab](assets/crontab-layout.png)

**Run every 15 minutes**

`*/15 * * * * <command>`

**Run every on 5, 10, and 15 minutes each hour**

`5,10,15 * * * * <command>`

**Run a job once a year on 1 Jan**

`* * 1 1 * <command>`



#### **Cronjob @ Format**

There's also a couple of useful shortcuts! And one that lets you run each time the system reboots!

| Shortcut  | Description           |
| --------- | --------------------- |
| @reboot   | Run once, at startup. |
| @yearly   | Run once a year.      |
| @annually | (same as @yearly).    |
| @monthly  | Run once a month.     |
| @weekly   | Run once a week.      |
| @daily    | Run once a day.       |
| @midnight | (same as @daily).     |
| @hourly   | Run once an hour.     |



## Control Access to Cron

> If the **/etc/cron.allow** file exists, then users must be listed in it in order to be allowed to run the **crontab** command. If the **/etc/cron.allow** file does not exist but the **/etc/cron.deny** file does, then users must not be listed in the **/etc/cron.deny** file in order to run **crontab**.
>
> In the case where neither file exists, the default on current Ubuntu (and Debian, but not some other Linux and UNIX systems) is to allow all users to run jobs with **crontab**.
>
> https://help.ubuntu.com/community/CronHowto

### Allow and Deny Access

You need root access.

Also note that **the cron allow and deny files might exist in a different location depending on your system!**

```shell
$ su

# Or

$ su -
```

**Allow**

Go to `/etc/cron.allow` and add the usernames you want to allow

**Note: Make sure root is in the file, otherwise sudo commands won't be allowed!**

**Deny**

Go to `/etc/cron.deny` and add the usernames you want to deny



### Verify Access

```shell
# Logged in as user
$ crontab -l
```

If you're not authorised, you'll get `crontab: you are not authorized to use cron. Sorry.`

If you are but the tab isn't created, you'll get `crontab: can't open your crontab file`



## FAQ

### Run Scripts in a Certain Directory

Cron usually runs in the home directory. If you want it to run the scripts somewhere else, just add a cd line!

Try to avoid using ~/, since that tends to fail, instead, write the full directory.

```shell
# In the crontab preceding the script running line
cd /directory
```



### Run sudo Commands

If you want to run sudo commands, ensure that when you were configuring the crontab, you did so using

```shell
$ sudo crontab -e
```

Otherwise, you'll need to put your password in plaintext

```shell
# Inside the crontab file
echo <password> | sudo <command>
```



### Set Custom Logs

```shell
# Add to the end of your command
* * * * * <command> > /log/file/directory/logfile_name.log
```





```
                            .     .
                         .  |\-^-/|  .    
                        /| } O.=.O { |\
```

​    

------

 [![Yeah! Buy the DRAGON a COFFEE!](../assets/COFFEE%20BUTTON%20%E3%83%BE(%C2%B0%E2%88%87%C2%B0%5E).png)](https://www.buymeacoffee.com/methylDragon)