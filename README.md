# linux_tricks

### ubuntu terminal colors
[explanation how to](https://askubuntu.com/questions/558280/changing-colour-of-text-and-background-of-terminal)</br>

```bash
#!/bin/bash
for((i=16; i<256; i++)); do
    printf "\e[48;5;${i}m%03d" $i;
    printf '\e[0m';
    [ ! $((($i - 15) % 6)) -eq 0 ] && printf ' ' || printf '\n'
done
```


```bash
echo -ne '\e]10;#123456\e\\'  # set default foreground to #123456
echo -ne '\e]11;#abcdef\e\\'  # set default background to #abcdef
```
