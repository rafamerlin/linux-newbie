#### How to run dotnet core c# debugger on Arch/Manjaro

This is Legacy now, as dotnet core 2.0 has absolutely no need for any of this. 

#### Legacy way of doing it in dotnet core 1.0

This was quite tricky to do, I've tried many different approaches and finally I think I've found one that works.

The developers are trying to fix this, so this may change in the future, but we have an idea of how to make it work anyway.

Here are the 2 issues on github that helped me to get here:
[https://github.com/OmniSharp/omnisharp-vscode/issues/661]
[https://github.com/OmniSharp/omnisharp-vscode/issues/1323]

The 1232 was the one where I [Merurino] documented how I made it work for me.

After choosing the "New" or "Old way and doing it's steps (the new is still only in private release), you need to use `pacaur` to install `icu54` and `icu55`.
These are libraries that help some apps to work, apparently it's the case of the debugger (we are using ubuntu's one here, that maybe is the reason.)

##### New way of making it download Ubuntu's distro for Arch:
Edit the Preferences on Vs-Code and add this line:
`"csharp.fallbackDebuggerLinuxRuntimeId": "ubuntu.16.04-x64"`

You may have to delete the debugger folder in case you have it downloaded already. Check the (I) icon on the option that it will tell you what to do.

On the debug folder (to delete it or check if it exists) use `ls -la` because the `.debugger` folder is a hidden one.

Also you'll need to restart Vs code.


##### Old way of making it download Ubuntu's distro for Arch:
First we edit the file `/etc/os-release` to tell the installer that this is an arch based distro, so we add the following line:

```
ID_LIKE=arch
```
