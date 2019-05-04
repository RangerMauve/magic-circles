# magic-circles
A QR-code-like graphical representation of URLs that look like magic circles.

## Why?

The idea of magic is really appealing, but sadly the magic that I've seen practiced in real life is more about spirituality and self fulfillment than having physical effects on the world.

So if I can't get "real" magic from the ether, I'll need to create it from scratch using technology.

The idea of this project is to have a more mystical interface to our technology. You write some code for a machine to interpret, upload it somewhere, and turn the link to your code into a magic circle that people can draw by hand. Invoking the magic circle requires having a machine read it and execute it's code.

The first application I want to target is VR worlds served from P2P networks. Ideally, I'd like to create a scene using [WebXR](https://aframe.io/), store it in a [P2P Website](https://docs.datproject.org/docs/intro), turn the link into a magic circle, stick the circle somewhere in real life, and have a [VR Headset](https://www.atmos.world/) load the virtual space from the internet for the user to experience.

## Implementation

- Only encode characters from URLs (`ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789-._~:/?#[]@!$&'()*+,;=`)
- Data should be stored within a circle with some sort of symbol to denote the "top"
- Start with a shape for encoding data
  - Triangles, Squares, 5 - 8 sided stars
  - Additional data within subdivisions of the shape?
  - Shape should always have a "center" which contains a sylbol that will inform what shape it is.
- Should have concentric rings around the inner circle for storing the bulk of the data
  - Rings will be subdivided into circles in order to reduce
  - Number of circles and their radius should be a precise and predefined size per ring
  - Use computer vision and a neural network for parsing symbols from the circles
  - Rings should have circles within them for symbols that encode part of the URL
    - Base characters off of [Canadian Aboriginal Syllabics](https://en.wikipedia.org/wiki/Canadian_Aboriginal_syllabics)
    - About 693 symbols (reduce it for ease of writing)
    - Data should be pronounceable for added effect
    - Symbols should be taken from Unicode so that they can be rendered in SVG on most systems
    - Would it be better to make something up from scratch?
  - Make a symbol representing the "end" of the URL and loop data from that point
  - Parsing of rings should be clockwise starting from the top
