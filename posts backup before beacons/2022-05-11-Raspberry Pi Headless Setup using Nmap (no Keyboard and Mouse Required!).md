---
layout: post
title: Raspberry Pi Wireless Setup using NMAP – no Keyboard, Mouse, or Monitor Required
---


<div class="message">
We leverage new updates to the Raspberry Pi OS Imager to edit the `/etc/wpa_supplicant/wpa_supplicant.conf` file with known WiFi credentials. After powering on our Raspberry Pi, we find it using an Nmap Ping scan, SSH in, enable VNC, and will have a full screen share of our desktop without ever having to plug in a mouse, keyboard, or monitor.
</div>

1.1: Overview

This guide is meant to take away the pain of prototyping your embedded or IoT device. We aim to take you through all of the setup, install, networking, and then provide working example code to allow you to start prototyping your application in an hour.

1.2: Materials
  *1 Raspberry Pi 4 
  *1 USB-C Power Cord
  *1 MicroSD Card for the Operating System on the Raspberry Pi
  *1 Control PC (Windows, MacOS, Ubuntu) for configuring the Raspberry Pi OS, remotely accessing the Raspberry Pi, and writing code using our favorite IDE
  *WiFi Connection (Home Network with known SSID / Password)

2: Installations and Setup

2.1: Imaging Raspberry Pi OS

Raspberry Pi supports many flavors of Linux. The default Raspberry Pi OS, which is a flavor of Debian Linux, is a good distribution and will allow us to have a stable OS for our embedded / IoT prototype.

Listed out here are the steps for imaging an SD card with Raspberry Pi OS:

  2.1.1: Download and install the latest Raspberry Pi Imager at https://www.raspberrypi.com/software/
  2.1.2: Insert a MicroSD Card into your Control PC. The MicroSD card will most likely be in a MicroSD adapter. The MicroSD card houses the operating system for the Rapsberry Pi (like an HDD or SSD would for your Control PC). The MicroSD card adapter converts the electrical pinout of the MicroSD card to that of an SD card, which is a slot supported by many computers. Please see appendix X.X for more on MicroSDs, adapters, and dongles if your Control PC doesn’t have a built-in SD card reader.
  2.1.3: Launch Raspberry Pi Imager
  2.1.4: Click on “Choose OS” and select “Raspberry Pi OS” (32-bit, ~0.8 GB size) 
  2.1.5: Select Storage (a MicroSD card) to flash the OS to.
  2.1.6: The program should now look similar to this:
  [Pi-Blog-1](/public/img/pi-blog-1)
  2.1.7: To do advanced configuration of our Raspberry Pi, enable remote access OOB, ensure that it will connect to our WiFi network, and choose a secure username, click on the “Settings” Gear in the lower right hand corner of Raspberry Pi Imager
  2.1.8: Every option in the Advanced Configuration Menu can be of utility to us, enabling things like remote access (via SSH) and automatic connection to a known WiFi network much easier. Ensure that we are on the screen below:
  [Pi-Blog-2](/public/img/pi-blog-2)
  2.1.9: Here is a description of fields to set and their utility:
    *Set hostname: Our Pi’s name op the network. Setting distinct hostnames ensures that we can identify different Pi’s on the network. Set this to a hostname and make note of it -- we can use it to directly SSH into the Pi in the next section.
    *Enable SSH: SSH is a useful option for remote access. We will not have any graphical user interface (a necessity for some projects).
    *Set username and password: Setting this here will make us able to SSH into the Pi without doing any additional setup.
    *Configure Wireless LAN: Input a known WiFi network name (SSID) and password that your Pi will be in proximity to the router of, for a good signal that will allow it to be on your local network.
    *Of the last three checkboxes in the “Persistent Settings”, the first two are inconsequential. Please uncheck “Enable Telemetry”
2.1.10: Click “SAVE”, go back to the main menu, and click “WRITE” to image the microSD card with Raspberry Pi OS. The process will take a handful of minutes to complete.

## Use Case: Using Computer Vision to Verify Radar Data for Advanced Driver Assistance in Vehicles

Autonomous vehicles and Advanced Driver Assistance Systems (ADAS), such as blind-spot detection, adaptive cruise control, lane maitenance, and animal/pedestrian detection, use a combination of imaging sensors across the visual and nonvisible electromagnetic light spectrum. For example, [Driver Monitoring Systems](https://www.aptiv.com/en/insights/article/what-is-a-driver-monitoring-system) and [Night Vision for Pedestrian / Animal Detection](https://www.youtube.com/watch?v=hp9lR4x7Kok) use infrared sensors to detect the heat signature of the driver of the vehicle, as well as pedestrians and animals that could be potential roadway hazards, respectively. Many vehicle systems combine sensor data to provide an accurate and robust automated system. For example, blind spot detection in vehicles uses radar (common frequencies being 24 GHz and 77 GHz), but also might combine camera data to that runs a computer vision algorithm for vehicle detection.

![This Image](/public/img/BLIS-Taurus.jpg)

With this in mind - say we have the end goal of validating the radar for a blind spot detector in a vehicle (giving accurate distance readings and timely driver warnings). The primary measurement of distance to another car in the blind spot is made by our mmWave radar.

- **To bold text**, use `<strong>`.
- *To italicize text*, use `<em>`.
- Abbreviations, like <abbr title="HyperText Markup Langage">HTML</abbr> should use `<abbr>`, with an optional `title` attribute for the full phrase.
- Citations, like <cite>&mdash; Mark otto</cite>, should use `<cite>`.
- <del>Deleted</del> text should use `<del>` and <ins>inserted</ins> text should use `<ins>`.
- Superscript <sup>text</sup> uses `<sup>` and subscript <sub>text</sub> uses `<sub>`.

Most of these elements are styled by browsers with few modifications on our part.

## Heading

Vivamus sagittis lacus vel augue rutrum faucibus dolor auctor. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Morbi leo risus, porta ac consectetur ac, vestibulum at eros.

### Code

Cum sociis natoque penatibus et magnis dis `code element` montes, nascetur ridiculus mus.

{% highlight js %}
// Example can be run directly in your JavaScript console

// Create a function that takes two arguments and returns the sum of those arguments
var adder = new Function("a", "b", "return a + b");

// Call the function
adder(2, 6);
// > 8
{% endhighlight %}

Aenean lacinia bibendum nulla sed consectetur. Etiam porta sem malesuada magna mollis euismod. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa.

### Lists

Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Aenean lacinia bibendum nulla sed consectetur. Etiam porta sem malesuada magna mollis euismod. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.

* Praesent commodo cursus magna, vel scelerisque nisl consectetur et.
* Donec id elit non mi porta gravida at eget metus.
* Nulla vitae elit libero, a pharetra augue.

Donec ullamcorper nulla non metus auctor fringilla. Nulla vitae elit libero, a pharetra augue.

1. Vestibulum id ligula porta felis euismod semper.
2. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
3. Maecenas sed diam eget risus varius blandit sit amet non magna.

Cras mattis consectetur purus sit amet fermentum. Sed posuere consectetur est at lobortis.

<dl>
  <dt>HyperText Markup Language (HTML)</dt>
  <dd>The language used to describe and define the content of a Web page</dd>

  <dt>Cascading Style Sheets (CSS)</dt>
  <dd>Used to describe the appearance of Web content</dd>

  <dt>JavaScript (JS)</dt>
  <dd>The programming language used to build advanced Web sites and applications</dd>
</dl>

Integer posuere erat a ante venenatis dapibus posuere velit aliquet. Morbi leo risus, porta ac consectetur ac, vestibulum at eros. Nullam quis risus eget urna mollis ornare vel eu leo.

### Tables

Aenean lacinia bibendum nulla sed consectetur. Lorem ipsum dolor sit amet, consectetur adipiscing elit.

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Upvotes</th>
      <th>Downvotes</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <td>Totals</td>
      <td>21</td>
      <td>23</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>Alice</td>
      <td>10</td>
      <td>11</td>
    </tr>
    <tr>
      <td>Bob</td>
      <td>4</td>
      <td>3</td>
    </tr>
    <tr>
      <td>Charlie</td>
      <td>7</td>
      <td>9</td>
    </tr>
  </tbody>
</table>

Nullam id dolor id nibh ultricies vehicula ut id elit. Sed posuere consectetur est at lobortis. Nullam quis risus eget urna mollis ornare vel eu leo.

-----

Want to see something else added? <a href="https://github.com/poole/poole/issues/new">Open an issue.</a>
