#### To add Colours to the Bash (including Git Branch)

##### Manjaro: 

Unlike others, manjaro doesn't use `~/.bashrc` directly, it uses `~/.extend.bashrc` instead.

The structure is pretty much the same as Ubuntu's one, but has some difference in the script and also the script caters for root or regular user.

So for Arch I searched for: 
`if ${use_color} ; then`

And added bellow this function the following:
```
parse_git_branch() {
 git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
```

Also inside the function I've replaced this:
```
	if [[ ${EUID} == 0 ]] ; then
		PS1='\[\033[01;31m\][\h\[\033[01;36m\] \W\[\033[01;31m\]]\$\[\033[00m\] '
	else
		PS1='\[\033[01;32m\][\u@\h\[\033[01;37m\] \W\[\033[01;32m\]]\$\[\033[00m\] '
	fi
```

With this:
```
	if [[ ${EUID} == 0 ]] ; then
		PS1='\[\033[01;31m\][\h\[\033[01;36m\] \W\[\033[01;33m\]$(parse_git_branch)\[\033[01;31m\]]\$\[\033[00m\] '
	else
		PS1='\[\033[01;32m\][\u@\h\[\033[01;37m\] \W\[\033[01;33m\]$(parse_git_branch)\[\033[01;32m\]]\$\[\033[00m\] '
	fi
```

##### Ubuntu Mate:

We have to edit the file `~/.bashrc`

Search for the following line and uncomment it
`force_color_prompt=yes`

Search for the block bellow and replace it entirely by the new one:
```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt
```

And replace them with this:
```
parse_git_branch() {
 git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
if [ "$color_prompt" = yes ]; then
 PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[01;33m\]$(parse_git_branch)\[\033[00m\]$ '
else
 PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w$(parse_git_branch)\$ '
fi
unset color_prompt force_color_prompt
```

After that run `source ~/.bashrc` so the file will be re-executed and changes applied immediately

In regards to the colours, they are the `01;??m` in the `[\033[01;33m\]` blocks, they represent the colour for the very next instruction. More colours in http://unix.stackexchange.com/a/124408

Also, a quick turo in regards to the fields in the config:
u = username
h = host
w = working folder