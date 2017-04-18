#### How to keep firewall enabled 

If you enable the firewall on the GUI, it will not stay enabled after a restart.
To maintain it always enabled you have to do this:

```
sudo systemctl enable ufw
sudo systemctl start ufw
```