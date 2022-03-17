<H1 align="center">
    Are You Blinking?
</H1>

<H5 align="center">
    A blink detection algorithm that can categorize blink duration and translate the Morse Code in real-time.
</H5>

add gif here

# Introduction

Are you taken hostage by a dictator and have no way of communicating with the outside world? Did your kidnappers also coincidentally decide to release a video of you to ask for ransom? 

Fret not! I have you covered 🤝. Just blink away your secret message in Morse Code and this program will take care of the rest.


# How this works

This algorithm can take any recorded video (or, even live camera feed!) and translate the blinks into Morse Code, and then to English in real time. That means, you can send an SOS signal or even the location of those cruel perpetrators to the police. 


# Implementation

This algorithm is inspired from Adrian Rosebrock from pyimagesearch, be sure to check him out for a more in depth guide and more blog posts like this project. 


To detect the eye blinks from a video, this program considers the * *E*ye *A*spect *R*atio*, which is defined as:

equation image

These points p1 ... p6 refer to facial landmarks associated with the eye as follows: 

eye image

As one can see, when you consider the EAR, it rapidly decreases when your eyes are closed and stays approximately around a reasonable threshold when open. We use this threshold to determine if your eye has blinked or not.

Once your eye has blinked we have to, in order: 

* Determine and categorize the duration of the blink
* Use the category to compute if it is a dash (-) or a dot (.)
* Build the Morse Code message and translate it 

We do this using `time.time()` to measure how long it takes for each blink. Once we can figure that out, we seperate them into short blinks and long blinks, and dots and dashes respectively. After that we dynamically build a `string` that stores the encoded secret message. Finally we using a dictionary to decode the string and output that in the terminal.

# Getting Started

