# rpi-config
stuff to do with configuring the raspberry pi


## Cloning an SD card 

Following this guide [here](https://medium.com/platformer-blog/creating-a-custom-raspbian-os-image-for-production-3fcb43ff3630)

Using Ubuntu 20.04

install pishrink

```
wget  https://raw.githubusercontent.com/Drewsif/PiShrink/master/pishrink.sh 
chmod +x pishrink.sh
sudo mv pishrink.sh /usr/local/bin
```
Copy the image to the hard disk, then shrink it.

```
sudo fdisk -l   
sudo dd if=/dev/sdc of=/home/tim/rpi-27-10-20.img bs=4M status=progress
sudo pishrink rpi-27-10-20.img rpi-vw-27-10-20.img
```

Write the image back with the raspberry pi cloner


## Setting up mplayer to run on boot

mplayer will not run properly with elevated privileges, so set user to ubuntu in the service file

To test the streaming of rtmp to hdmi, you can use an mp4 clip and stream it from another machine
```
wget https://file-examples-com.github.io/uploads/2017/04/file_example_MP4_1920_18MG.mp4
ffmpeg -re -i file_example_MP4_1920_18MG.mp4 -f flv  rtmp://<your-pi-ip>/live/video
```

