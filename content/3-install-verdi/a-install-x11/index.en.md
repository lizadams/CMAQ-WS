---
title: Install X11 and get Display working
weight: 20
--- 

###  Install X-11 Display

1. Update package manager

`sudo apt-get update`

2. Install Imagemagick

`sudo apt-get install imagemagick`

3. Install X11-apps

`sudo apt install x11-apps`

4. Install X11 development

`sudo apt-get install xserver-xorg-dev`

5. Install X11 Xaw

`sudo apt-get install libxaw7-dev`

6. Install udunits

`sudo apt-get install libudunits2-dev`

7. Install Java version 17 for VERDI

`sudo apt install openjdk-17-jdk`

8. Make sure it is the default version

`sudo update-alternatives --config java`

4. Enable X11 forwarding

```
sudo vi /etc/ssh/sshd_config
```

add line

```
X11Forwarding yes
```

Verify that it was added

```
sudo cat /etc/ssh/sshd_config | grep -i X11Forwarding
```

Restart ssh

```
sudo service ssh restart
```

Exit the cluster

`exit`

Relogin to the cluster

`pcluster ssh -v -Y -i ~/cmas.pem --region=us-east-1 --cluster-name cmaq-cluster`

Test display

`display`

Output

### logout of cluster and then install VERDI from your local laptop

`exit`

From your local machine 

`scp -i ~/cmas.pem VERDI_2.1.4_linux64_20230425.tar.gz ubuntu@54.80.227.174:/shared/build`


Also install ncview

`scp -i ~/cmas.pem ncview-2.1.9.tar.gz ubuntu@54.80.227.174:/shared/build`


### Login to cluster and extract VERDI software

`pcluster ssh -v -Y -i ~/cmas.pem --region=us-east-1 --cluster-name cmaq-cluster`

`cd /shared/build`

`tar -xzvf VERDI_2.1.4_linux64_20230425.tar.gz`


### Run verdi to look at Ozone

```
cd /fsx/data/output/output_v54+_cb6r5_ae7_aq_WR413_MYR_gcc_2018_12US1_3x64_classic/
/shared/build/VERDI_2.1.2/verdi.sh -f $cwd/CCTM_CONC_v54+_cb6r5_ae7_aq_WR413_MYR_gcc_2018_12US1_3x64_classic_20171222.nc -s "O3[1]" -g tile
```

### Run VERDI to look at PM2.5

```
/shared/build/VERDI_2.1.2/verdi.sh -f $cwd/CCTM_AELMO_v54+_cb6r5_ae7_aq_WR413_MYR_gcc_2018_12US1_3x64_classic_20171222.nc
```


