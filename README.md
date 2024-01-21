First off, this is based on the installation guide made by Visate. Without his steps, I would have been stuck!<br>
For more info regarding many of the below steps. please read more on his page.

https://github.com/Visate/communeai-scratchpad
<br><br>
# Setup Commune on Windows 10 Pro/Enterprise without Docker Desktop

YouTube version.<br>
https://youtu.be/XyiW0suKqyo

*(for the people that would like to know what you are installing, you can find links at the bottom of the page)*

### Prerequisites
Your IP needs to be a public IP (as in not behind a nat) and ensure you have setup port forwarding rules. Otherwise, Commune will not work!
See step 9 for more details.

### 1. Setup WSL and Ubuntu
- **Right** click the Start menu and open Windows Powershell (admin).
- First set the default version of WSL.
```sh
wsl --set-default-version 2
```
- Make sure WSL is up to date.
```sh
wsl --update
```
- Install Ubuntu 22.04
- During the installation, set user and password and remember them!
```sh
wsl --install -d Ubuntu-22.04 
```
- We could continue directly from here but it is good to check if all is working, so let's close the Powershell window.

### 2. Start Ubuntu and update
- Click on the Start menu and start Ubuntu, there should now be a shortcut for Ubuntu in the Start menu.
- Let's start with updating and upgrading our installation.

```sh
sudo apt update && sudo apt -y upgrade
```
*If you see a message regarding **libcuda.so**, you can ignore this. It is just a warning.*

### 3. Install dependencies
- Install pip
```sh
sudo apt install -y python3-pip
```
- Install pipenv
```sh
pip install pipenv --user
```
-  Check path (result for me: /home/omni/.local)
```sh
python3 -m site --user-base
```
- Update path, append /bin to the above path. Replace omni with your username.
```sh
export PATH="/home/omni/.local/bin:$PATH"
```
-  Permanently add to the path
```sh
nano ~/.bashrc 
```
- This opens Nano text editor, use the arrow keys on your keyboard and go down to the end of the file.
- Paste or write (export PATH="$HOME/.local/bin:$PATH") without () at the end of the file, if you are new to Nano, one right-click will paste **where the cursor is**.
- Once you have added the above line, press CTRL + x, answer Y and press enter to save and overwrite.

<br/>

- Install dependencies.
```sh
pipenv install click numpy protobuf==3.20 streamlit
```

### 4. Starting pipenv
- Start pipenv
```sh
pipenv shell
```

### 5. Setup/installing Commune
- Clone Commune Git
```sh
git clone https://github.com/commune-ai/commune.git
```
- Change directory
```sh
cd commune
```
- Pull latest files
```sh
make pull
```
- Run install for commune
```sh
pip install -e ./
```

### 6. Install and configure Rust
- Run the below commands, one after the other.
```sh
curl https://sh.rustup.rs -sSf | sh -s -- -y
```
```sh
source "$HOME/.cargo/env"
```
```sh
rustup install nightly-2023-01-01
```
```sh
rustup override set nightly-2023-01-01
```
```sh
rustup target add wasm32-unknown-unknown
```

### 7. Make sure you are the owner of the commune folder
- Replace omni with your username
```sh
sudo chown -R omni:omni ~/.commune
```

### 8. Is commune running?
- You should still be in the \~/commune folder. (\~/ This is a shortcut to your home folder).
- Let's see if you can list the modules.
```sh
c modules
```
- If you could see a list of modules, **congratulations!**, commune is now working!

### 9. Set port range
- Now that we know that Commune is running, lets set the port range for Commune (this is the ports you need to set in the port forward rule).
- The blow range is just an example.
```sh
c set_port_range 50000 55000 
```
- If you could see a list of modules, **congratulations!**, commune is now working!

### 10. Some extra commune commands.
- Find your root key, this is good to save.
```sh
c root_key
```
- You can start a local node if you need to. There could be some extra configuration depending on your system, see below for more info.
```sh
c start_local_node
```

### 11. How to start Commune the second time
- If you want to or need to get back into Commune and use it, do the following.
- Start Ubuntu from the Start menu.
- Open the commune folder
```sh
cd commune
```
- Start the pipenv
```sh
pipenv shell
```
- From here you can use any of the commune commands i.e. c mcap, c stats and so on.
- Best of luck!
<br><br><br><br>

### 12. Extra steps, if you want to run a local node.
- Before you begin the below steps, you need to reboot at least once after completing the above steps and setting up Commune.
- Install Docker
```sh
sudo apt install docker.io
```
- Add your user to docker group
```sh
sudo usermod -aG docker $USER
```
- **REBOOT Windows!!**, do not skip this step.
- Go to the commune folder
- Start the pipenv
```sh
pipenv shell
```
- Enter commune folder
```sh
cd ~/commune/
```
- Start local node
```sh
c start_local_node
```

### 13. Troubleshooting
- If you have issues installing Ubuntu on step 1, run the four below commands and reboot your computer.
```sh
wsl --unregister Ubuntu-22.04
```
```sh
wsl --shutdown
```
```sh
netsh winsock reset
```
```sh
netsh int ip reset
```
- If you see an error like this "fatal: No url found for submodule path 'comchat' in .gitmodules" when you try make pull, run this and try again.
```sh
git rm --cached comchat
```

- If you see this error in the dashboard KeyError: 'module', enter the below and try starting the cash again.
```sh
c dash public=true
```
```sh
c st public=true
```

### 14. For the people that would like to know what they are installing.

- **WSL:** https://learn.microsoft.com/en-us/windows/wsl/about
- **Ubuntu:** https://ubuntu.com/
- **Python:** https://www.python.org/
- **PIP:** https://pypi.org/project/pip/
- **pipenv:** https://pypi.org/project/pipenv/
- **Shell:** https://en.wikipedia.org/wiki/Shell_(computing)
- **Commune:** https://github.com/commune-ai/commune
- **Rust:** https://www.rust-lang.org/
- **Docker:** https://www.docker.com/
- **Why update your PATH:** https://realpython.com/add-python-to-path/#how-to-add-python-to-path-on-linux-and-macos
<br><br>
