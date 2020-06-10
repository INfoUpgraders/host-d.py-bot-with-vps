# How to Host your Discord Python Bot using a Virtual Private Server
**I made a video [here](https://www.youtube.com/watch?v=t__APf2IOcI) on how to host it 24/7 with these steps!**

![thumbnail](https://i.ibb.co/qjT4P1F/how-to-host-python-vps.png)

**I made a video [here](https://www.youtube.com/watch?v=t__APf2IOcI) on how to host it 24/7 with these steps!**


## Getting Started  
**I made a video [here](https://www.youtube.com/watch?v=t__APf2IOcI) on how to host it 24/7 with these steps!**

- You first need an SSH client such as [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) or [Termius](https://termius.com/) you can buy an amazing VPS (Virtual Private Server) from [webhost.sh](https://webhost.sh/vps) which is what I recommend.

- Next your need to login to it by doing `ssh user@ip_address` and click yes to verify your fingerprint.

- Create a directory by doing `mkdir` and you can name it bots, so `mkdir Bots` then change into it by doing `cd Bots`

- After that, run the command `sudo add-get install software-properties-common` press `y` to continue and install.

- Next, you need to `sudo add-apt-repository ppa:deadsnakes/ppa` press `enter` to continue and install it.
  - Make sure you update everything by doing `sudo apt update`

- Now we need to install Python and a few packages with it, to do this, run `sudo apt install python3.8 python3.8-venv python3-pip` and press `y` to continue and add it.

- Now we need to install git so we can clone our bot from GitHub, you can do this by running the command `sudo apt-get install git` and press `y` to continue and install it.

- Then we want to clone our bot from GitHub, we can do this by running `git clone <repo link>` and it will create a folder with your repository name and put all of your content inside of it. 
  - A **very** important step is to do `cd <repo name>` into your bot directory, if you don't know what it is called, run the command `ls` and look for your bot folder, then you can `cd` into it.

- Then you want make sure your bot runs before we make it run in the background, to do this, you need to run `python3.8 -m venv venv` and then do `source venv/bin/activate` to activate it, once activated, run the command `pip install -U discord.py` to install the discord module (add the voice option to it if needed) then run `python3.8 <botfile>.py` (`python3.8 bot.py` in most instances) to start the bot. 

- You will most likely get an error along the lines of `module not found` don't let this fear you as you just need to install the modules, you can do this by running `pip install -U <module name>` 
  - If you get an error along the lines of `x86-64-linux-gnu-cc failed with exit status 1` your need to add a package, you do this by running `sudo apt-get install python3.8-dev` and then reinstall the package.
  
- Your bot should now be started but now you notice you cant exit and do other things without having to stop it.

### Keeping it on with systemd
- Some featues of systemd are that the service will automaticalled start after the machine has been rebooted or anything, there is a much easier option called screen, but systemd offers more benefites.

**To get started with systemd** you need to first run the command `nano /etc/systemd/system/<filename>.service` so we can edit the file. Paste below and fill in the `<>` with what you want.

```
[Unit]
Description=<whatever you want here>
After=multi-user.target

[Service]
WorkingDirectory=/root/Bots/<BOT DIRECTORY FOLDER>
User=root
ExecStart=/bin/bash -c "source venv/bin/activate && python3.8 bot.py"
Restart=always

[Install]
WantedBy=multi-user.target
```
Press `ctrl+x`, `y`, then `enter` to save the file.

- Once you saved the file, start it by running `systemctl enable <filename>.service` then `systemctl start <filename>.service` then your bot should be started!
**I made a video [here](https://www.youtube.com/watch?v=t__APf2IOcI) on how to host it 24/7 with these steps!**
