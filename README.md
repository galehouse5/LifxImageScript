# LifxImageScript
Command line tool that lets you script a modest light show for your LIFX lights using only an image editor. Makes use of the LIFX LAN protocol.

![Example recording](/ReadmeAssets/recording.gif)

## Image Scripts
An image script is just a normal image file that's interpreted in a special way. Horizontal rows of pixels represent lights and vertical columns of pixels represent frames. An image is read from left to right one frame at a time. The RGB color values in a frame are converted to HSV color values and sent to the corresponding light. Frame rate is configurable up to 20 fps, the max recommended send rate of the LIFX LAN protocol.

### Example 1
This image script creates a red orb that bounces back and forth between four lights. Note that the image has been enlarged for display so it's no longer intended for use as an image script. The working image script has much smaller dimensions.

![Bouncing orb effect](/ReadmeAssets/bouncing-orb-effect.png)

### Example 2
This image script creates a red orb that bounces at an accelerating rate until exploding in a burst of yellow light that trails off with a sparkling effect. Again, the image has been enlarged for display.

![Exploding orb effect](/ReadmeAssets/exploding-orb-effect.png)

### Example 3
This is the actual image script for the light show recording at the top of the page. The red bouncing orb and exploding orb effect are contained within this script. The image hasn't been enlarged for display so it's best viewed under high magnification.

![Bouncing and exploding orb script](/ReadmeAssets/script.bmp)

## Command Line Reference

### Example
The following command executes a script named `hello-world.bmp` for 2 lights at 20 fps, repeating until it's stopped by key press. Lights are specified by IP address and their order corresponds to the order of horizontal rows in the image script. Light `192.168.1.89` is mapped to the topmost horizontal row. The `--smooth` flag indicates that lights should transition their color and brightness smoothly between frames.

`dotnet LifxImageScript.dll --path "hello-world.bmp" --lights 192.168.1.89 192.168.1.88 --fps 20 --smooth --repeat`

### Parameters
<dl>
  <dt>--path</dt>
  <dd>Path of image script.</dd>
  
  <dt>--lights</dt>
  <dd>IP address list of lights. Order is important. The first light maps to the topmost horizontal row of image script.</dd>
  
  <dt>--fps (optional, default=1)</dt>
  <dd>Frames per second. Limited to 20, the max recommended send rate of the LIFX LAN protocol.</dd>
  
  <dt>--repeat-count (optional, default=0)</dt>
  <dd>Repeats image script a specific number of times. A negative number signifies to repeat until stopped.</dd>
  
  <dt>--smooth-transitions (optional, default=off)</dt>
  <dd>Smoothly transitions color and brightness between frames. When disabled, frame changes may create an undesirable strobe effect.</dd>
  
  <dt>--brightness-factor (optional, default=1)</dt>
  <dd>Useful for scaling down brightness when testing a script. Accepts decimal values between 0 and 1.</dd>
</dl>

## Download
LifxImageScript requires the .NET Core Runtime, which is available for Windows, Linux, and macOS.
1. [Download .NET Core Runtime](https://www.microsoft.com/net/download)
2. [Download LifxImageScript](https://github.com/galehouse5/LifxImageScript/releases/latest)
