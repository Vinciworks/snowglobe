# VinciSnowGlobe

by Rafi Miller, 6 December 2017

## Overview

This is a snow globe. There is snow inside a globe. The snow falls from the top of the globe to the bottom of the globe. 

## Usage

Click on the globe to shake it.

When the globe shakes, the current animal leaves and the next animal appears. It's like a carousel slider, but cooler because it's inside a snow globe.

## Developer notes

### Add an animal

To add an animal to the globe, open `index.html` and add an `.animal` to the `#globe`. The JS will include it in the carousel.

Add a second class to the div to give it a background image, e.g. `.animal.fox`.

### Mathematics

The flakes’ starting positions are taken randomly from a uniform distribution on the unit circle in the *x-z* plane at the top of the globe. 

The *x* coordinate from [-1, 1] maps to a percentage from 0% to 100%, which becomes the snowflake's `left` property. 

The *z* coordinate from [-1, 1] maps to [0, 1], and determines the snowflake's size, opacity, and velocity, to create the illusion of depth. Using `matrix3D` for these effects isn't possible because we are in an `overflow: hidden` div.

Each flake has a fixed random rotation on its *z* axis.

Each flake also has a random initial and final rotation on both its *x* and *y* axis, and rotation is tweened during the flake's fall. The flake's `transform-origin` is set outside the flake, so that its rotation on these axes causes it to spiral at a random angle as it falls.
