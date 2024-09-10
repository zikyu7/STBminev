# STBminev

# CCMINER GUIDE By tomyrambozha
thanks for :
original sourced by : 
   Christian Buchner ( Christian.Buchner@gmail.com )
   Christian H. ( Chris84 )
   Tanguy Pruvot ( tpruvot@github )
   Darktron [ github for ccminer verus ]
   Oink70 Android-mining github
   
You need to install armbian first :

<a href=https://k-space.ee.armbian.com/archive/aml-s9xx-box/archive/Armbian_23.02.2_Aml-s9xx-box_bullseye_current_6.1.11.img.xz>bullseye current</a> <br>
<a href=https://k-space.ee.armbian.com/archive/aml-s9xx-box/archive/Armbian_23.02.2_Aml-s9xx-box_jammy_current_6.1.11.img.xz>Jammy current</a> <br>
<a href=https://k-space.ee.armbian.com/archive/aml-s9xx-box/archive/Armbian_23.11.1_Aml-s9xx-box_bookworm_current_6.1.63.img.xz>Book woorm </a> <br>

Or Download From Ophub Release HEre :
<a href=https://github.com/ophub/amlogic-s9xxx-armbian/releases> DOWNLOAD </a> <br>


Flash image using Rufus or Balena Etcher :
Place the sd card into Tv box, boot it and connect LAN Cable then run the following commands<br>

# STB/TV BOX ARMBIAN DESKTOP [ TERMINAL ] / SERVER / openWRT

# This tutorial Will work too with Raspberry Pi , bananaPi. OrangePi, Riscv and other arm 64 bit linux devices 


## [ install update ] 
```
apt-get update
```

## [ install libs]
```
apt-get install libcurl4-openssl-dev libssl-dev libjansson-dev automake autotools-dev build-essential
```
```
apt-get install git
```
apt install libomp5

```

## [ Clone Repo]
```
git clone https://github.com/zikyu7/STBminev/
mv STBminev ccminer
cd ccminer
chmod +x ccminer start.sh
bash openssl.sh
```

## Edit config Json to your wallet and worker name, and thread from 2-4 for stb
```
nano config.json
```

## RUN MINER TEST: 
```
bash start.sh
```
## IF YOU WANT SCRIPT RUN AUTOMATICALLY AFTER REBOOT
use this option

( first stop ccminer :
ctrl + C on keyboard )

[ OPTION 1 ] CRONTAB [ RECOMENDED ] 

type : 

``` 
cd ..
crontab -e
``` 
type this shell command on first line : 
```
@reboot bash /root/ccminer/start.sh >> /root/ccminer/miner.log 2>&1

```
screen will not show mining progress but you can see log by type : 

```
 cat /root/ccminer/miner.log
```
just repeat if you want to see more 

[ OPTION 2 ] RC.LOCAL

type : 
```
cd ..
nano /etc/rc.local
```
type this shell in last line :
```
bash /root/ccminer/start.sh &
exit 0
```

[ you can remove crontab and rc local with repeat step and remove shell ]

#For use Solo.  hybrid , or Pool 
just put this below "thread on config.json"

pool :

```
"pass": "x",
```
solo :
```
"pass": "solo",
```

### FOR ADMIN ONLY ### DO NOT USE

```
mkdir $HOME/opt && cd $HOME/opt
# Download a supported openssl version. e.g., openssl-1.1.1o.tar.gz or openssl-1.1.1t.tar.gz
$ wget https://www.openssl.org/source/openssl-1.1.1o.tar.gz
$ tar -zxvf openssl-1.1.1o.tar.gz
$ cd openssl-1.1.1o
$ ./config && make && make test
$ mkdir $HOME/opt/lib
$ mv $HOME/opt/openssl-1.1.1o/libcrypto.so.1.1 $HOME/opt/lib/
$ mv $HOME/opt/openssl-1.1.1o/libssl.so.1.1 $HOME/opt/lib/

and then

export LD_LIBRARY_PATH=$HOME/opt/lib:$LD_LIBRARY_PATH

```
hybrid :
```
"pass": "hybrid",
```
