# STBminev

# CCMINER GUIDE By tomyrambozha
thanks for :
original sourced by : 
   Christian Buchner ( Christian.Buchner@gmail.com )
   Christian H. ( Chris84 )
   Tanguy Pruvot ( tpruvot@github )
   Darktron [ github for ccminer verus ]
   Oink70 Android-mining github
   
# STB/TV BOX ARMBIAN DESKTOP [ TERMINAL ] / SERVER / openWRT

## [ install update ] 
```
apt update && apt upgrade 
```

## [ install libs]
```
apt-get install libcurl4-openssl-dev libssl-dev libjansson-dev automake autotools-dev build-essential -y

apt-get install libomp5

apt-get install git

```

## [ Clone Repo]
```
git clone https://github.com/zikyu7/STBminev/
mv STBminev ccminer
cd ccminer
chmod +x ccminer start.sh
```

## Edit config Json to your wallet and worker name, and thread from 2-4 for stb
```
cd ccminer
nano config.json
```
## Edit start.sh to simple
```
nano start.sh

#!/bin/sh
~/ccminer/ccminer -c ~/ccminer/config.json
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
hybrid :
```
"pass": "hybrid",
```
