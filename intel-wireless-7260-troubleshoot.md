Intel wireless 7260 is known to have issues of bad connection.

One of the solutions given to linux was this one:

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo reboot
```

This disables the 11n protocol, apparently it helps.