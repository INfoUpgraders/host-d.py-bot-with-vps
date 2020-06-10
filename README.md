# How to Host your Discord Python Bot using a Virtual Private Server
![thumbnail](https://i.ibb.co/qjT4P1F/how-to-host-python-vps.png)


## Getting Started
- You first need an SSH client such as [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) or [Termius](https://termius.com/) you can buy an amazing VPS (Virtual Private Server) from [webhost.sh](https://webhost.sh/vps) which is what I recommend.

- Next your need to login to it by doing `ssh user@ip_address` and click yes to verify your fingerprint.

- Create a directory by doing `mkdir` and you can name it bots, so `mkdir Bots` then change into it by doing `cd Bots`

- After that, run the command `sudo add-get install software-properties-common` press `y` to continue and install.

- Next, you need to `sudo add-apt-repository ppa:deadsnakes/ppa` press `enter` to continue and install it.
  - Make sure you update everything by doing `sudo apt update`

- Now we need to install Python and a few packages with it, to do this, run `sudo apt install python3.8 python3.8-venv python3-pip` and press `y` to continue and add it.

- Now we need to install git so we can clone our bot from GitHub
