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
 + Hardware:
   + **LED** strip (which is controllable via IR, I have one that's controllable via the 44 key remote)
   + Samsung **Galaxy S5** (or a phone that has an IR emitter, but may not work with the app)
   + Amazon **Alexa** device (doesn't matter which, I've used an Echo Dot)
  
 + Software: 
   + [**IFTTT**](https://ifttt.com/) account and [app](https://play.google.com/store/apps/details?id=com.ifttt.ifttt) - to handle special Alexa commands and make web requests.
   + [**ngrok**](https://ngrok.com/) account - to expose your local server securely.
   + Android **server** application (github link) - to run your localhost server, handling HTTP requests and controlling your LED strip.
   + [**Termux**](https://play.google.com/store/apps/details?id=com.termux) terminal emulator - to run ngrok on your phone.
   + [Hacker's Keyboard](https://play.google.com/store/apps/details?id=org.pocketworkstation.pckeyboard&hl=en) - you'll need it to navigate in Termux. Or just use an external keyboard.


## Setting up

### Termux

1. Install Termux on your phone from the Google Play Store link provided earlier.

2. Install ngrok in Termux. I won't write a tutorial for this, since a number of them already exist, so I'll link the [first](https://steemit.com/utopian-io/@faisalamin/how-to-download-install-ngrok-in-android-termux-also-work-for-non-rooted-devices) written one I found, but you may follow an other one as well.

3. Once you installed them I'll provide a short snippet which you can use to make the startup a bit easier. Because if you have a free account, on each restart the url you get - as your exposed address - will be different.  

    3.1 Since you'd need to start ngrok by typing `./ngrok http 8080`, it's easier to create a script which does the same, but you have to type less on that tiny keyboard.  
    
    3.2 Open the nano editor (inside Termux) by typing `nano start.sh` (_start.sh_ will be the name of the script file).  
    
    3.2 Enter your command to start your ngrok, e.g.: `./ngrok http -region eu 8080` to start your server in the eu region.  
    
    3.3 `CTRL + X`, `y` and then `Enter` to save the file and exit. (Actually you're trying to exit without saving, so it asks if you want to save it, and whether the given name is good for you.)  
    
    3.4 One more thing left, we need to make this script executable by typing `chmod +x start.sh`. 

    3.5 Now you can start ngrok by typing `./start.sh`.

4. If you succeeded, you'll see a screen stating your session is online, and there will be 2 URLs, that are the same, just the HTTP protocol changes. For example: `https://8d7232ca.eu.ngrok.io`.

### IFTTT

5. Now you'll need to install IFTTT on your phone from the Play Store.

6. Log into your IFTTT account in the app, and go to the `My Applets` tab.

    2.1 Create a new Applet by clicking on the `+` icon in the top right corner.

    2.2 Set Alexa as the trigger (`this`). You might have to connect your Alexa to your IFTTT account along the way.

    2.3 Choose: `Say a specific phrase`.

    2.4 Set the phrase you want to say to trigger the action.

    2.5 Set Webhooks as the action (`that`).

    2.6 `Make a web request`.

    2.7 Enter the earlier mentioned ngrok URL and append `/led` at the end. So it will look like this: `https://8d7232ca.eu.ngrok.io/led`

    2.7 The *method* should stay `GET`.

    2.8 Choose `application/json` as *Content Type*.

    2.9 You can leave the *Body* empty.

    2.10 Now you are finished with the IFTTT part.

### Server application

7. Now you need to download the server application I've written. This can be found here.

8. Once you've installed my app, you just need to open it, and click the `Start service` button and you're ready to roll.


I hope you like it!
