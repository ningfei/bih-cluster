# Connecting via SSH on Windows

!!! hint

    - Please read the [pre-requisites](prerequisites.md). Especially pay attention to the [username](prerequisites.md#what-is-my-username).
    - Install an [SSH client for Windows](../ssh-client-windows.md).

## Connecting from within MDC/Charite Network

Click on `Session`.

![](figures/mobaxterm_connect1.png)

Click on `SSH`.

![](figures/mobaxterm_connect2.png)

In **Basic SSH settings**, enter a hostname (`hpc-login-X.cubi.bihealth.org`, where `X` is 1 or 2), check **Specify username** and enter your username in the textfield.
Select the tab **Advanced SSH settings**, check **Use private key** and select your private SSH key file (possible choices described with the next to figures).

![](figures/mobaxterm_connect3.png)

Select the `id_rsa` file generated in Linux OR

![](figures/mobaxterm_connect3a.png)

select the `id_rsa.ppk` file generated in Windows with MobaXterm.

![](figures/mobaxterm_connect3b.png)

Afterwards hit the **OK** button and MobaXterm will connect.

![](figures/mobaxterm_connect4.png)

The session will be stored automatically and you can establish new connections later on, or also multiple ones at the same time, if you like.

## Mounting the FS from within the MDC/Charite Network

Once WinSshFS is started, an icon will be added to your taskbar:

![](figures/winsshfs1.png)

Left-clicking that icon will bring up a window.
If not, right click the taskbar icon, select `Show Manager` and click `Add` in the menu.

![](figures/winsshfs2.png)

Fill out the marked fields:

- **Drive Name:**
Name that will show up in the windows explorer
- **Host:**
`hpc-transfer-1.cubi.bihealth.org`
- **Username:**
Your cluster username
- **Authentication method:**
`PrivateKey`. Select the `id_rsa` private key, not the `.ppk` format that is provided by PuTTY.
Enter the password that you used to secure your key with.
- **Directory:**
Cluster directory that will be mounted, you can choose any directory you have access to on the cluster.

Then click `Save` and then `Mount`.

Open the explorer. A new drive with the name you gave should show up:

![](figures/winsshfs3.png)

Finished!


## Connecting via MDC Jail Node

* This requires an active MDC account!

1. Additional to the steps above, click on the tab `Network settings`.
2. Check **Connect through SSH gateway (jump host)** and in the text field **Gateway SSH server** enter `ssh1.mdc-berlin.de` and in the field **User** your MDC username.
3. Check **Use private key** and select the SSH key that you uploaded to the MDC persdb (this might differ from your cluster key!).
4. Click **OK**

![](figures/mobaxterm_connect5.png)

## X11

!!! question "Do you really need to run a graphical application on the cluster?"

    Please note that running more complex Java applications, such as IGV may be not very efficient because of the connection speed. In most cases you can run them on your local workstation by [mounting them via SSHFS](#file-system-mount-via-sshfs).

Start MobaXterm, it should automatically fetch your saved Putty sessions as you can see on screen below:

![](figures/mobaxterm_main.png)

Connect to one of the login nodes, by double-click on saved profile, and then use `srun --pty --x11 bash` command to start X11 session to one of the nodes:

![](figures/mobaxterm_login.png)

Finally, start X11 application (below example of starting Visual Terminal):

![](figures/mobaxterm_xterm.png)
