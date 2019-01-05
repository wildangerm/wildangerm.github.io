---
title:  "Voice controlled LED with Alexa"
layout: post
author: wildangerm
---

# [TUTORIAL] Voice controlled LED strip using Galaxy S5 and Amazon Echo Dot (Alexa)

The idea to control my LED strip from the network came, when I got my new smartphone, which didn't have an IR emitter. So I thought to myself, what if I create a server application onto my Galaxy S5, and I send HTTP requests to control it.

So I built a very simple application, that is capable of receiving requests, and for a specific one, it sends an IR signal to the LED strip. Since the IR, IR codes and the exact codes that my LED strip used were pretty unfamiliar for me, I had to do a lot of research. But at the end, it worked! I was able to send an HTTP request through local network to turn on/off my LED strip! 
 
But when I managed to get my hands on an Alexa device, a new idea came to my mind. What if I could control my LED strip _just_ by saying something to Alexa? This is how the idea was born.

## What you'll need:
 + **LED** strip (which is controllable via IR, I have one that's controllable via the 44 key remote)
 + Samsung **Galaxy S5** (or a phone that has an IR emitter, but may not work with the app)
 + Amazon **Alexa** device (doesn't matter which, I've used an Echo Dot)
 + **IFTTT** account - to handle special Alexa commands and make web requests.
 + **ngrok** account - to expose your local server securely.
 + Android **server** application (github link) - to run your localhost server, handling HTTP requests and controlling your LED strip.
 + **Termux** terminal emulator - to run ngrok on your phone.



I hope you like it!
