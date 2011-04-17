# OpenKinect library for Processing

Currently OSX only, please feel free to help remove that dependency.

### Gimme the binary already! (Updated 17 Apr 2011)

If you don't care for building from source, there are a couple of downloads available.

17 Apr 2011

10.6 - Snow leopard: [http://nrocy.github.com/files/kinect20110417.zip](http://nrocy.github.com/files/kinect20110417.zip)

10.5 - Leopard: [http://nrocy.github.com/files/kinect20110417_leopard.zip](http://nrocy.github.com/files/kinect20110417_leopard.zip)

19 Dec 2010

10.6 - Snow leopard: [http://nrocy.github.com/files/kinect20101222.zip](http://nrocy.github.com/files/kinect20101222.zip)

10.5 - Leopard: [http://nrocy.github.com/files/kinect20101222_leopard.zip](http://nrocy.github.com/files/kinect20101222_leopard.zip)

### Screenshot Porn

![Screenshot](http://nrocy.github.com/images/processing_screenshot.jpg)

### Methods available:

NativeKinect.init() - _initialize the Kinect_<br />
NativeKinect.setVideoRGB() - _output RGB video (default)_<br />
NativeKinect.setVideoIR() - _output IR video_<br />
NativeKinect.start() - _tell the Kinect to start streaming data to the library_<br />
NativeKinect.getVideo() - _pull the latest video frame_<br />
NativeKinect.getDepthMap() - _pull the latest depthMap frame_<br />
NativeKinect.getDepthMapRaw() - _pull the latest depthMap raw data_<br />
NativeKinect.setLed(int) - _change the Kinect LED colour (0-6)_

### Example:

	import king.kinect.*;

	PImage img, depth;
	short[] rawDepth;

	void setup()
	{
		size(1280, 480);
		
		img = createImage(640,480,RGB);
		depth = createImage(640,480,RGB);
		
		NativeKinect.init();
		NativeKinect.setVideoIR(); // View the IR images, see also setVideoRGB()

		NativeKinect.start();
	}

	void draw()
	{
		img.pixels = NativeKinect.getVideo();
		img.updatePixels();

		depth.pixels = NativeKinect.getDepthMap();
		depth.updatePixels();

		rawDepth = NativeKinect.getDepthMapRaw();
		println( rawDepth[0] );

		image(img,0,0,640,480);
		image(depth,640,0,640,480);
	}

### Build Requirements:

Prebuilt 32-bit libraries are included, so no external deps.

- Xcode

### Build Instructions:

Coming soon.

### TODO:

- More error checking
- Implement motor control methods
- Implement accelerometer methods
- Remove OSX/XCode specific dependencies

