# gopro-wireless-sync
Wireless GoPro connect to share &amp; copy videos and other files located from GoPro device to e.g. a Linux device

Preparation steps to enable GoPro WLAN connectivity:
1) - Power on your camera with the [Mode] button.
2) - On your camera display, swipe down > swipe left > tap [Preferences]
3) - Select [Wireless Connections] > [Connect Device].
4) - Select [GoPro Quik App] to put your camera in pairing mode, and select [Continue]
5) - Select [GoPro App]. You will see the WLAN name and password to connect to your camera by WLAN now (needed for the next steps to connect your Client device)

Next steps on your client device (e.g. Linux workstation):

6) - Activate your device WLAN
7) - Connect to WLAN - Your GoPro device WLAN name and password are provided in step 5)
8) - Open a Webbrowser (e.g. Firefox) and open this link to show and download your videos:

     http://10.5.5.9:8080/videos/DCIM/

Useful bash-script to download all .MP4 video files 
```
cd <download-target-dir-on-your-client-device>   # e.g "cd /tmp"

for goprofiles in ` curl http://10.5.5.9:8080/videos/DCIM/104GOPRO/ | grep .MP4 | sed 's/<tr><td><a href="//g' | awk -F '\\.MP4' '{print "http://10.5.5.9:8080" $1".MP4"}'  `
do
echo "wget $goprofiles"
wget $goprofiles
echo "#########################################################################"
done
```
