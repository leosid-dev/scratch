# SSH with X11Forwarding for windows11

## Prerequisites:
 - Windows10/11
## Instructions:
#### Install puTTY and Xming:
- Using winget (Easy):
  - Open cmd/powershell and type
    ```bash
    winget install --name puTTY Xming --source winget
    ```
  - Accept all the terms and when asked for UAC, click Yes to install.
- From Browser:
  - [Xming](https://sourceforge.net/projects/xming/files/Xming/6.9.0.31/Xming-6-9-0-31-setup.exe/download)
  - [puTTY](https://the.earth.li/~sgtatham/putty/latest/w64/putty-64bit-0.83-installer.msi)
  - Then install them using the setup <br>
    **SSH CONNECTION**
    - Open Xming and Allow the UAC for port Access.
    - Open puTTY, In the left side, go to SSH->X11 and Enable X11Forwarding.
    - Go back to Session enter the __ipaddress__ of the server given by the guide and save the session Session->Save and click Open.
    - Click Accept/Connect_Once and enter the __username__ of the server. After that enter the __password__ given by the guide.
    - Once connected, you are good to go. Open any GUI applications. (with few caveats specific to centos7 in the server)
  # SSH with X11Forwarding for linux based distros
  -Install **openssh** (refer your distro's Package Manager to install- MOstly present by default)
  - Make sure X11Forwarding and TrustedX11Forwarding(Optional-Some distros require this to function properly) is **set to yes** in ```/etc/ssh/ssh_config```
  - If you modified the file in previous step then enter this in terminal
  ```bash
  sudo systemctl restart ssh
  ```
  - Open a Terminal and type
  ```bash
  ssh -Y <username>@<ipaddress>
  ```
  -Accept the fingerprint prompt to add the server to known hosts.
  - Once connected, you are good to go. Open any GUI applications. (with few caveats specific to centos7 in the server)

 


