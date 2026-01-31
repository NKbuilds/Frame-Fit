# Frame Fit

## Why did I make this app?

I made this app because I personally faced this issue many times.

When uploading images as profile pictures or banners on different platforms, the platforms usually auto-crop the image. That turns into a frustrating trial-and-error process where you keep adjusting the image just to make it fit properly.

So I thought why not make this automatic?  
That’s why I created this application.

---

## What does this application do?

This application takes an image at any resolution and makes it suitable for the target platform.

You just enter the required width and height, and the app:
- keeps the original aspect ratio
- centers the image
- adds padding instead of cropping

This way, more of the original image is preserved without losing important parts.

---

## Requirements

You only need two libraries:
- Pillow (for image processing)
- Tkinter (for the GUI)

Tkinter comes pre-installed with Python, so you only need to install Pillow.

To install Pillow, run:
```bash

pip install pillow

```
## Why not OpenCV?

Initially, this project was planned to be implemented using OpenCV in C++.

However, this application is quite small and is meant to solve a simple but annoying problem. While working on it, I realized that implementing the same idea in Python would be much simpler and faster.

Pillow is also lighter for this use case, and Python allowed me to build and test the application quickly without adding unnecessary complexity.

So instead of overengineering it with OpenCV and C++, I decided to use Python and Pillow, which fit this project better.


## Possible Improvements

There are a few things that can be improved and extended in this project:

1. The UI is very basic and can be improved by adding things like a loading bar or a preview to show how the final image will look
2. Bulk image import support can be added so multiple images can be processed at once
3. Presets like YouTube thumbnails, Instagram posts, LinkedIn banners, etc., can be added so users can just select a preset and move on
4. The same logic can be implemented in C++, but for now Python is fast enough unless we are working with thousands of images

Contributions and suggestions are always welcome.



