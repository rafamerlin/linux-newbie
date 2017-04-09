#### How to install stuff from AUR?

[https://aur.archlinux.org/] AUR stands for Arch user Repository

First we find the package, clone it using GIT, and then run
`makepkg`

##### Tool to help doing this (better than using the repo manually)
The tool is called `pacaur`

This tool allows me to download packages and it's dependencies automatically (using `makepkg` forces me to download each indivitual dependency).

The best way to install it is using another one (that I've heard is not as secure as pacaur called `yaourt`)

To install yaourt we do this:
`sudo pacman -S yaourt`

Then we do this:
`yaourt -S pacaur`

!Important: sometimes `cower` package may have issues, I had to add a key on `gpd` to make it work, as provided by the maintainer in AUR [https://aur.archlinux.org/packages/cower/]

Also, pacaur may require an editor, you can install vim using pacman and them do this:
```
export EDITOR=vi
pacaur -S vim
```

If you want to make export fixed for editor, add it to the last line of `~/.extend.bashrc`

This will isntall pacaur and it's dependencies.

Then after pacaur is installed we can use `pacaur -S packageName` to install stuff.

Something also useful is the remove cache from pacaur, it will remove all the unecessary files after the instalations:
`pacaur -Sc`

If you want to uninstall some other package, you can use pacman directly, as all of them are registered on pacman after instalation.

##### Clean up unused dependencies.
Since we have `pacaur` installed, we can use it instead of using `pacman` directly.
I think there's no difference though.

First let's see all the unused/orphans packages.
`pacman -Qdt`

Now we remove them:
`pacman -Rsn $(pacman -Qdtq)`