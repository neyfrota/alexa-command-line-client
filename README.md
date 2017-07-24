# Alexa command line client

A alexa client for my [voice assistant](https://github.com/neyfrota/Billy-bass-voice-assistant/).

* **Command line based:** ```alexa ask``` record, post audio at amazon and play response. 
* **kiss:** Keep it simple and stupid. (Official raspberry alexa client is heavy and complex)
* **Smart authentication:** Automatic persist and refresh authentication tokens (even after reboot)    

<a href="http://www.youtube.com/watch?feature=player_embedded&v=W00Xq1SpXCs
" target="_blank"><img src="http://img.youtube.com/vi/W00Xq1SpXCs/0.jpg" 
alt="alexa interaction by command line" width="360" height="270" border="1" /></a>

# Install 
Install dependency
```
sudo apt-get install sox mplayer libjson-perl liburi-perl
``` 
[Configure raspberry pi audio](https://permissiontowrite.wordpress.com/raspberry-pi-audio-setup/)

Install and link to a well known folder (so we can run in any place) 

```
sudo git -C /opt/ clone https://github.com/neyfrota/alexa-command-line-client.git
sudo ln -s  /opt/alexa-command-line-client/alexa /usr/bin/alexa
``` 

# Register

We need register your alexa app at amazon. 

Visit [alexa-avs-sample-app for Raspberry-Pi](https://github.com/alexa/alexa-avs-sample-app/wiki/Raspberry-Pi) and follow steps 2 (*Register for an Amazon developer account*) and step 3 (*Create a device and security profile*)

Create a file  ```~/.alexa.conf``` with this content
```
ProductID=<ProductID from step 3>
ClientID=<ClientID from step 3>
ClientSecret=<ClientSecret from step 3>
ReturnURLs=https://localhost:3000/authresponse

```

# Log-in

We need log-in to link your local alexa command to your amazon device.

* run "```alexa login```" so we can create a custom URL to authenticate the app
* Copy url and visit in your browser
* Login with same credential at step 2
* Extract code value from response URL (*yes. page fail to load. This is fine. Focus in url*)
* run "```alexa login <code>```" so we generate access token and save local to persist authentication


# Run

Run local record/playback test, so you can hear what alexa will hear. Adjust [audio](https://permissiontowrite.wordpress.com/raspberry-pi-audio-setup/) if need
```
alexa test
``` 

ask something to alexa and listen response
```
alexa ask
```

We recommend check [hotwordDetection](https://github.com/neyfrota/hotwordDetection) to enable "hey alexa" hotword


# Credits

* Miguel Mota with some code examples about alexa [authentication](https://miguelmota.com/blog/alexa-voice-service-authentication/) and [interaction by curl](https://miguelmota.com/blog/alexa-voice-service-with-curl/).
* Russell Grokett wit more code examples in they [asterisk-raspberryPi-alexa](https://github.com/rgrokett/RaspiAsteriskAlexa) project
* Amazon to provide [alexa information](https://github.com/alexa/) so we can hack and play
