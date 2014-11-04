[Home](../README.md)    | [Getting started](../installation/getting-started.md)     | [Managing users](../manage-users/README.md) | [Collecting work](../collect-work.md) | [Shared folders](../shared-folders/README.md) | [Backups](../backups/README.md) | [Advanced options](../advanced/README.md) 
| :-----------: |:-------------:| :-----:| :-----:| :-----:| :-----:| :-----:| 


Changing RaspberryPi-LTSP background
======

RaspberryPi-LTSP comes with the amazing stars background photograph taken by [John Lemieux](https://www.flickr.com/photos/newdimensionfilms/7108632527/).   
![](../images/desktop-background.png)   

##Changing this image
If you want to change it to your own custom background image, the image is stored in 2 places.    
- Desktop background - ```/opt/ltsp/armhf/usr/share/images/desktop-base/raspi-LTSP.png```.
- Login screen background - ```/opt/ltsp/armhf/usr/share/ldm/themes/raspi/bg.png```.

If you wish to change either of these images, all you have to do is overwrite them with your new image.   
For example, to replace the desktop background    
```sudo cp /home/myname/myamazingimage.png /opt/ltsp/armhf/usr/share/images/desktop-base/raspi-LTSP.png```
   
**Note the images must be in PNG format.**

##Changing the login screen logo
The default login logo is the Raspberry Pi logo, if you wish to change it, apply the same process as above.   
It is stored at ```/opt/ltsp/armhf/usr/share/ldm/themes/raspi/logo.png```.   
   
**Make sure your logo is also in PNG format and has transparency enabled!**