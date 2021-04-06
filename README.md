# Pi-Camera-HTTP-Video-Streaming
> ## This procedure allows live streaming of Raspberry Pi Camera within the same network at 720p resolution with 60 FPS.
> * This method allows Raspberry Pi to broadcast the Raspberry Pi 5MP Camera Module's video feed on a HTTP URL within the same network and does not need additional softwares like VLC Player to access the video feed. The HTTP URL can be accessed from a Web Browser.
> * To get video stream on HTTP, the simplest method is to configure Motion serivce on the Raspberry Pi. But this Motion service runs a motion detection feature on the video stream by default and gets defaulted to 1 FPS when no motion is detected (which is a useful for applications like CCTV cameras). But this procedure is for getting maximum performance at minimum lag from the camera over the network, so we will disable the motion detection feature.
> * #### By default the video is broadcast in colour format. But to reduce bandwidth requirement, we use greyscale mode, although 720p 60FPS is possible on colour mode also. 
> * #### **Note: This was tested on Raspberry Pi 4 and Raspberry Pi 5MP Camera Module. Other combinations have not been tested.**

> ## Pre-Requisites:
> * Raspberry Pi should already be setup completely (including SSH if required) and must be connected to a network.
> * Remove Motion if it is already installed using apt-get.

> ## Setup (on the Raspberry Pi). Run the following commands on the terminal of Raspberry Pi 
> ### Step 1: Navigate to any personal folder (optional). 
> ### Step 2: Run the following commands one by one: 
>> #### `$ sudo mkdir motion`
>> #### `$ cd motion`
>> #### `$ git clone https://github.com/Motion-Project/motion.git`
>> #### `$ cd motion`
>> #### `$ sudo autoreconf -fiv`
>> #### `$ sudo ./configure`
>> #### `$ sudo make`
>> #### `$ sudo make install`
>> #### `$ cd /usr/local/etc/motion`
>> #### `$ sudo wget -L https://raw.githubusercontent.com/Kailash-Natarajan/Raspberry-Pi-Camera-Video-Streaming-60-FPS-HTTP/main/motion_720p60.conf`
>> #### `$ sudo mv motion_720p60.conf motion.conf`

> ## Starting Motion Service
>> #### `$ motion`
> ## Stopping Motion Service
>> #### Press `Ctrl+C`

> ## Start the Motion service and type the URL of the format 'http://<rpi_ip>:8081` to access the video feed, where <rpi_ip> is the local network IP address of the Raspberry Pi. You should be getting 720p 60FPS video at greyscale
> ## You can change the stream_grey parameter from 'on' to 'off' without the quotes in the file motion.conf (after performing Step 2 fully) for colour format.

> Email Me: kailash.natarajan.kn@gmail.com
