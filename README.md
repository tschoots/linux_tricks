# linux_tricks

### ubuntu terminal colors
[explanation how to](https://askubuntu.com/questions/558280/changing-colour-of-text-and-background-of-terminal)</br>


##### script to get the color numbers
```bash
#!/bin/bash
for((i=16; i<256; i++)); do
    printf "\e[48;5;${i}m%03d" $i;
    printf '\e[0m';
    [ ! $((($i - 15) % 6)) -eq 0 ] && printf ' ' || printf '\n'
done
```

##### command line set term color
```bash
echo -ne '\e]10;#123456\e\\'  # set default foreground to #123456
echo -ne '\e]11;#abcdef\e\\'  # set default background to #abcdef
```

##### vi tricksi</br>

[vi split screen](http://www.microshell.com/programming/quick-tips/split-screen-in-vi/)

##### sudo apt-get update failing - “could not open” list file due to “permission denied”</br>
```bash
sudo rm /var/lib/apt/lists/partial/*
```

### enable wake on lan
* [explanation](http://ubuntuguide.net/remotely-turn-on-ubuntu-from-lan)

##### target ubuntu machine
* sample /etc/rc.local file:
```bash
#!/bin/bash
ethtool -s enp0s25 wol g
exit 0
```
* same /etc/init.d/halt file:
```bash
NETDOWN=no
```

### remove docker images with none , or dangling
 ```bash
$ docker rmi $(docker images --filter "dangling=true" -q --no-trunc)
```
### docker images sorted by size
```bash
$ docker images --format '{{.Size}}\t{{.Repository}}\t{{.Tag}}\t{{.ID}}' | sed 's/ //' | sort -h -r
```

### some tricks for timestamp directory
* make a timestamp dir
```bash
$ mkdir $(date '+%Y%m%d%H%M%S')
```


### make bootable usb drive from iso ###
* [blog how to make usb drive command line from iso, mac os](https://www.lewan.com/blog/2012/02/10/making-a-bootable-usb-stick-on-an-apple-mac-os-x-from-an-iso)
