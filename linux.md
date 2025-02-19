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






