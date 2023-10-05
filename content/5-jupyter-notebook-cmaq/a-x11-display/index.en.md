---
title: Prepare cluster and enable X11 display
weight: 23
--- 

Your user should be similar to `ec2-user@ip-<IP-address>`. If it is otherwise something like `sh-4.2` or `ssm-user@<IP-address>`, then run the following command before proceeding:

```csh
sudo su ec2-user
```

![ec2-user](/static/images/1-gettoknow-ec2user.png)

1. **Test to see if X11 is already enabled**

```csh
display
```

Output

![ImageMagick Display](/static/images/1-imagemagick-display.png)

------

These instructions will take some time, so be patient!

1. **Update Yum** (this will take 5 minutes)

    ```csh
    sudo yum update -y
   ```

2. **Add amazon linux extras**

    ```csh
    sudo amazon-linux-extras install epel -y
    ```

3. **Add Firefox Browser**

   ```csh
   sudo amazon-linux-extras install firefox -y
   ```

4.  Additional yum instructions

```csh
sudo yum makecache fast
```

5. Install Imagemagic

```csh
sudo yum install ImageMagick ImageMagick-devel -y
```

6. Enable X11 forwarding

```csh
sudo vi /etc/ssh/sshd_config
```

add line

```csh
X11Forwarding yes
```

Verify that it was added

```csh
sudo cat /etc/ssh/sshd_config | grep -i X11Forwarding
```

Restart ssh

```csh
sudo service sshd restart
```

Exit the cluster (exit until the terminal closes)

`exit`

Relogin to the cluster using the Nice DCV "MATE Terminal"

7. Test display

```csh
display
```

If display still doesn't work, if you had previously started the DCV, you need to exit and then restart it.

8. After restarting DCV verify your username and restart the tcsh shell.

```csh
/bin/tcsh
```  

7. Run display on the terminal window within DCV

```csh
display
```
