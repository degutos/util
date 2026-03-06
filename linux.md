# Utils

## Notes 

This is my notes for day to day stuffs 

## Linux


## zsh

### How to install ZSH and Theme

Installing zsh and others like curl and git

```
# apt install zsh curl git
```

Lets run zsh

```
# zsh
```

Lets set the default SHELL for the user root or any other user

```
# usermod -s $(which zsh) root
```

#### Installing oh-my-zsh and themes via curl

```
# sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Set up new THEME - fino-time

```
sed -i 's/^ZSH_THEME.*/ZSH_THEME="fino-time"/g' ~/.zshrc
```

---

# curl

## Test connection from the pod to service 

```
➜  cat curl-test.sh 
for i in {1..3}; do
   kubectl exec --namespace=kube-public curl -- sh -c 'test=`wget -qO- -T 2  http://webapp-service.default.svc.cluster.local:8080/info 2>&1` && echo "$test OK" || echo "Failed"';
   echo ""
done
```

---

# VIM

## split

We can use :split or :sp to open a window in vim to open the same file twice or open another file in the same vim window. It will split the screen horizontally as default

```
:split
:sp
:split another-file-path.txt
```
Alternatively you can open a window vertically with command:
```
CTRL + w + v     # this will open the same file vertically
```

To move between window 
```
CTRL + w + arrow up
CTRL + w + arrow down
OR
CTRL + w + arrow right
CTRL + w + arrow left
```
Macros
```
Q+w To start recording into register w
Q To stop recording
@w To run the macro again
4@w To run the macro 4 times (4 lines).
```

Reference to more details on screen: https://www.geeksforgeeks.org/splitting-vim-screen-horizontally-and-vertically-in-linux/

---

## Add color to shell

```sh
PS1='\e[33;1m\u@\h: \e[31m\W\e[0m\$ '
```

```sh
export COLOR_NC='\e[0m' # No Color
export COLOR_BLACK='\e[0;30m'
export COLOR_GRAY='\e[1;30m'
export COLOR_RED='\e[0;31m'
export COLOR_LIGHT_RED='\e[1;31m'
export COLOR_GREEN='\e[0;32m'
export COLOR_LIGHT_GREEN='\e[1;32m'
export COLOR_BROWN='\e[0;33m'
export COLOR_YELLOW='\e[1;33m'
export COLOR_BLUE='\e[0;34m'
export COLOR_LIGHT_BLUE='\e[1;34m'
export COLOR_PURPLE='\e[0;35m'
export COLOR_LIGHT_PURPLE='\e[1;35m'
export COLOR_CYAN='\e[0;36m'
export COLOR_LIGHT_CYAN='\e[1;36m'
export COLOR_LIGHT_GRAY='\e[0;37m'
export COLOR_WHITE='\e[1;37m'
```

## grep by IP Address

```sh
$ ip a | grep --color=always -E '([0-9]{1,3}\.){3}[0-9]{1,3}|$'
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether dc:a6:32:4f:fd:f7 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether dc:a6:32:4f:fd:f8 brd ff:ff:ff:ff:ff:ff
    inet 192.168.68.65/22 brd 192.168.71.255 scope global dynamic noprefixroute wlan0
       valid_lft 4262sec preferred_lft 4262sec
    inet6 fe80::34dd:b6f8:93b2:e94e/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```

- This will show the entire output of "ip a" and highlight the IP address (red color). The |$ will show the no matching lines also.



# VIM command navigation on bash command

This is util to use VIM motions in the command line bash to edit and navigate through your command

```sh
$ set -o vi # this command enable your VIM motions in the command line
```

Example: 
- when working with a large command line

```sh
kubectl exec my-pod -- find /var/log -name "*.log"
```

use:
- ESC to go to vim motions movingset 
- b -> to go back one word
- w -> to go front one word
- 0 -> to go to begining of the line
- $ -> to go to end of the line
- F letter -> to go BACK to the letter
- f letter -> to go FRONT to the letter
- dw -> delete word
- db -> delete word back
- d$ -> delete until the end of the line
- d0 -> delete until the begining of the line

## To unset the VIM motion

```sh
set -o emacs
```

## To check all set

```sh
set -o
```




  


