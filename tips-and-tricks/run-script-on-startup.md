# Run a script on startup

You may wish to add a script or program to run on startup. This can done in a few ways, one of whcih being using [Cron](https://en.wikipedia.org/wiki/Cron). 

First you will need to install this utility if you do not have it already.
```shell
sudo apt-get update
sudo apt-get install cron
```

After successfully installing cron you can then add a command to the crontab using: 
```shell
crontab -e
```
Once inside crontab simply append to the bottom of the file, the command to execute your code on reboot. For example:
```shell
@reboot python3 /home/user/my_startup_script.py
```
Now your script will run on startup.
