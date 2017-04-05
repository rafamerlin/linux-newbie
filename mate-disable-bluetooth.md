### How to disable bluetooth from startup on Ubuntu Mate
	
First, stop the service:

`sudo systemctl stop bluetooth.service`

Then disable it:

`sudo systemctl disable bluetooth.service`

Check:

`sudo systemctl status bluetooth.service`