# Setup Communex on Windows 10 Pro

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

### 3. Install pip
- Install pip
```sh
sudo apt install -y python3-pip
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

### 4. Install Communex
- Start pipenv
```sh
pip install communex
```

### 5. Create your key  (if you do not have one)
- Create the key and replace ThisIsMYKey with the name you want for your key
```sh
comx create key ThisIsMyKey 
```

### 6. If you did not have Commune installed and created a new key (step 5), ensure you have the correct permissions on your Commune folder.
- Replace omni with your username
```sh
sudo chown -R omni:omni ~/.commune
```

### 8. List your keys.
- Quick and easy way to list your keys.
```sh
comx key list
```

### 9 For the people that would like to know what they are installing.

- **WSL:** https://learn.microsoft.com/en-us/windows/wsl/about
- **Ubuntu:** https://ubuntu.com/
- **Python:** https://www.python.org/
- **PIP:** https://pypi.org/project/pip/
- **Communex:** https://github.com/agicommies/communex
- **Commune:** https://github.com/commune-ai/commune
- **Why update your PATH:** https://realpython.com/add-python-to-path/#how-to-add-python-to-path-on-linux-and-macos
<br><br>
