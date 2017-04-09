#### How to run dotnet core c# debugger on Arch/Manjaro

This was quite tricky to do, I've tried many different approaches and finally I think I've found one that works.

The developers are trying to fix this, so this may change in the future, but we have an idea of how to make it work anyway.

Here are the 2 issues on github that helped me to get here:
[https://github.com/OmniSharp/omnisharp-vscode/issues/661]
[https://github.com/OmniSharp/omnisharp-vscode/issues/1323]

The 1232 was the one where I docummented how I fixed it.

First we edit the file `/etc/os-release` to tell the installer that this is an arch based distro, so we add the following line:

```
ID_LIKE=arch
```

Then we use `pacaur` to install icu54 and icu55.
These are libraries that help some apps to work, apparently it's the case of the debugger (we are using ubuntu's one here, that maybe is the reason.)