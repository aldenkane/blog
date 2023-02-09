---
layout: post
title: Working with Deterministic Computer Vision
---


<div class="message">
I go over the difference between deterministic and aritificial intelligence algorithms in computer vision, and then dive into a use case of deterministic computer vision (with code).
</div>

Computer vision is an integral part of evolving technological landscape. With a few applications including biotmetric authentication and access (facial recognition, [iris recognition](https://en.wikipedia.org/wiki/Iris_recognition)), self-driving vehicles (lane detection and maitenance, pedestrian / animal detection), and pandemic response (body temperature detection using infrared cameras), the technology is experiencing wide commerical deployments and still shows much room for growth. Many human tasks can be aided or automated with computer vision.

We often seeing the media referring to things such as self-driving vehicles and facial recognition as "artificial intelligence"...evoking feelings of all-powerful computers doing human jobs. Despite there being numerous applications of aritificial intelligence in computer vision, many applications of computer vision are effectively using deterministic alogirithms. These algoirthms are computationally less expensive and easier to prototype since engineers do not need annotated training data (a good professor once told me "I do not believe in AI...I believe in people around the world drawing bounding boxes around pictures of cats").

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
