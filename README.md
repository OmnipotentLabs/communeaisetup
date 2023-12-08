First off, this is based on the installation guide made by Visate. Without his steps, I would have been stuck!<br>
For more info regarding many of the below steps. please read more on his page.

https://github.com/Visate/communeai-scratchpad
<br><br>
# Setup Commune on Windows 10 Pro/Enterprise



### Install Docker Desktop for Windows
- Go to https://www.docker.com/products/docker-desktop
- Download and install, you can click next on everything and only change settings if you know what you are doing.
- Reboot!


### After reboot start Docker Desktop
- Start Docker-desktop, you can skip registering if you want. *(Sometimes Docker-desktop can crash the first time it starts and can ask if you want to reset to default, just click reset and restart Docker-desktop if this happens)*

### Setup WSL and Ubuntu
- **Right** click the Start menu and open Windows Powershell (admin).
- Type the following in the Powershell window, the installation can take a while.

```sh
wsl --install -d Ubuntu
```
- During the installation, set user and pass and remember them!
- You can close the window after the installation.
- Open Docker-Desktop and go to Settings --> Resources --> WSL integration.
- Check the box for "Enable integration with my default WSL distro".
- Enable "Enable integration with additional distros:" for the Ubuntu distros.
- Click on "Apply a& restart".

### Start Ubuntu
- Click on the Start menu and start Ubuntu, there should now be a shortcut in the Start menu.
- Let's start with updating and upgrading our installation.

```sh
sudo apt update && sudo apt upgrade
```
*If you see a message regarding **libcuda.so**, you can ignore this. It is just a warning.*

- Let's continue the setup, now we need to install pip.

```sh
sudo apt install -y python3-pip
```
- Install pipenv

```sh
pip install --user pipenv
```
- Check our path. The below returns /home/omni/.local (for the sake of this guide).

```sh
python3 -m site --user-base
```
- Now let's update the path.

```sh
export PATH="$HOME/.local/bin:$PATH"
```
-  Permanently add to the path

```sh
nano ~/.bashrc 
```
- This opens Nano text editor, use the arrow keys on the keyboard and go down to the end of the file.
- Paste or write (export PATH="$HOME/.local/bin:$PATH") without () at the end of the file, if you are new to Nano, one right-click will paste where the cursor is.
- Once you have added the above line, press CTRL + x, answer Y and press enter to save and overwrite.













