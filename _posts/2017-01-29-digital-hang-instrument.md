---
layout: post
title:  Digital Hang Instrument
thumbnail: /assets/hang.png
excerpt: The Digital Hang Instrument is my project for composing with data flow programming course. Sound synthesis is done in Pure Data and the Hang like multitouch user interface for playing the 9 different notes.
---

<iframe src="https://player.vimeo.com/video/201553429" width="720" height="405" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
<p><a href="https://vimeo.com/201553429">iPad Hang</a> from <a href="https://vimeo.com/user6135320">Timi Koponen</a> on <a href="https://vimeo.com">Vimeo</a>.</p>

## Making of:

*The Digital Hang Instrument is my project for composing with data flow programming course.*

I got my inspiration from [the original Hang instrument](https://en.wikipedia.org/wiki/Hang_(instrument)). The Hang is an steel pan instrument that you play on your lap and it has quite an unique and interesting sound. I wanted to create my own digital version of it, without trying to mimic or copy it directly but rather to capture the same aesthetics and elegance it has.

The project consisted of two parts. The first part is the multitouch user interface built on iPad where you can play the 9 different notes. Another part was building the sound synthesis with [Pure Data](https://puredata.info/) which you could then play with the iPad app itself. I wanted the instrument to sound calm and peaceful, but still vivid and colourful at the same time. Inspired by the sound of the Hang I needed to have the high hitting sound in the beginning and a long resonating tail afterwards.

{% include image.html
            img="/assets/hang_preview.jpg"
            caption="My version of the Hang running on iPad." %}

I started the project by checking how Pure Data could be integrated within an iOS project and followed this [tutorial](http://defuncapps.tumblr.com/post/129644152544/making-ios-music-apps-with-pure-data-libpd-and). I just wanted to see if I would run into any troubles straightaway and how to get the basic messages going back and forth between Swift and Pure Data. Everything seemed to be working smoothly.

Then when I knew I got the basic connections between Swift and Pure Data working I started to work with the sound synthesis part. I downloaded various samples of Hang and tried to analyse the original sound a bit. I also did some research how other Pure Data patches have produced different metallic sounding instruments.

Since this was my first sound synthesis I have ever done I needed to figure out quite many things. I began the work from producing sine waves and I had the idea of layering them together to make it sound right. But in the end I wasn’t really happy with the results so I needed to figure out a different way.

{% include image.html
            img="/assets/hang_sinewave_synthesis.png"
            caption="My single sinewave oscillator" %}

I stumbled upon [Martin Brinkmann's Pure Data instruments](http://www.martin-brinkmann.de/pd-patches.html) where I found the random_hang_perc1.pd patch from the undocumented instruments zip-file. I studied his work closely and how he had based it on noise synthesis and what type of values he had used to produce the percussive sound.

{% include image.html
            img="/assets/hang_noise_synthesis.png"
            caption="My final version of the noise oscillator" %}

Then in the final version I produced a single hang sound by combining 5 sine wave synthesizers and 8 noise synthesizers seen on the patch below. In the end I just selected a good sounding values by toggling the sounds on and off and tried to fine-tune the values by ear. Both synthesis patches take five input values: played note, velocity, level of the individual sound, frequency multiplier and decay.

{% include image.html
            img="/assets/hang_multiple_synthesis.png"
            caption="My final version of the noise oscillator" %}


On the iPad side I wanted to keep the user interface really simple so it only consists 9 of dots and by touching those it plays the corresponding notes. To make it feel more lively I added small animations when the dots are played and also made them always move a little bit.

{% include image.html
            img="/assets/hang_gif.gif"
            caption="Small animations that play visualise the sound." %}


As a summary I really liked how the project turned out. The sound it produces is interesting and somewhat close what I had initially thought out. The user interface is minimalistic and the small animations give emphasis to the sound itself. I used total 4 days for the sound design and the iOS coding. Roughly 50% for each. And before the actual work I used one day beforehand to test the implementation of Pure Data into iOS.