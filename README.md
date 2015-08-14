# node-canvas-animation-example

An example of how to use `node-canvas` to create an animation as a GIF
and a Video

## Install

Requires a recent version of [node.js](https://nodejs.org/).

Clone this repository, and then:

    npm install

## Running it

The `draw.js` file creates a bunch of frames in the `frames/` directory:

    node draw.js

## Creating a GIF

Requires imagemagick & gifsicle. With Homebrew, you can install
gifsicle with `brew install gifsicle`

First, use Imagemagick to convert the series of PNG frames into a series
of static GIFs:

    mogrify -format gif -path frames-gif/ frames/*.png

And then using gifsicle, create an animated GIF:

    gifsicle -d10 frames-gif/*.gif > animated.gif

## Creating a Video

    ffmpeg -i frames/%5d.png -c:v libx264 -r 30 -pix_fmt yuv420p circle.mp4
