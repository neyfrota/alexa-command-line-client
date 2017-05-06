# alexa command line client

A command line client to interact with alexa voice service for my [Billy Bass Alexa Client](https://github.com/neyfrota/Billy-Bass-Alexa-Client) project.

<a href="http://www.youtube.com/watch?feature=player_embedded&v=W00Xq1SpXCs
" target="_blank"><img src="http://img.youtube.com/vi/W00Xq1SpXCs/0.jpg" 
alt="alexa interaction by command line" width="360" height="270" border="1" /></a>

* **Command line based:** ```alexa ask``` record, post audio at amazon and play response using default mic and speaker. 
* **Simple:** Can inetegrate in multiple other projects. ("hey alexa" [hotword detection](https://github.com/neyfrota/hotword-detection-service) for example) 
* **Lite:** Just a perl script. Official alexa client is a very heavy and complex system using java and node
* **Authentication persistence:** Automatic persist and refresh tokens even after reboot.    

# Install 
* ```sudo apt-get install sox``` we use sox to record and manipulate audio, so we need install
* ```sudo apt-get install mplayer``` we use mplayer to play audio, so we need install
* ```sudo mkdir /opt/alexa-command-line-client``` create a folder to store project
* ```sudo chown $USER /opt/alexa-command-line-client``` change ownership to make it easy
* ```git clone git@github.com:neyfrota/alexa-command-line-client.git /opt/alexa-command-line-client``` clone project in above folder
* ```sudo ln -s  /opt/alexa-command-line-client/alexa /usr/bin/alexa``` add alexa command line to a well known folder so we can run in any place

# Register at amazon

Visit [alexa-avs-sample-app for Raspberry-Pi](https://github.com/alexa/alexa-avs-sample-app/wiki/Raspberry-Pi) and follow steps 2 (*Register for an Amazon developer account*) and step 3 (*Create a device and security profile*)

Create a file  ```~/.alexa.conf``` with this content
```
ProductID=<ProductID from step 3>
ClientID=<ClientID from step 3>
ClientSecret=<ClientSecret from step 3>
ReturnURLs=https://localhost:3000/authresponse

```

# Authenticate

* run "```alexa login```" so we can create a custom URL to authenticate the app
* Copy url and visit in your browser
* Login with same credential at step 2
* Extract code value from response URL (*yes. page fail to load. This is fine. Focus in url*)
* run "```alexa login <code>```" so we generate access token and save local to persist authentication

# Test

* run "```alexa test```" to record and playback, so you can hear what alexa will hear
* Adjust your audio. Check [microphone setup](https://github.com/neyfrota/Billy-Bass-Alexa-Client/blob/master/docs/audio.md) for help.

# Ask

* run "```alexa ask```" 
* Ask something
* listen alexa response

# Credits

I cannot build this without help. **__"I am what I am because of who we all are"__**

* Miguel Mota with some code examples about alexa [authentication](https://miguelmota.com/blog/alexa-voice-service-authentication/) and [interaction by curl](https://miguelmota.com/blog/alexa-voice-service-with-curl/).
* Russell Grokett wit more code examples in they [asterisk-raspberryPi-alexa](https://github.com/rgrokett/RaspiAsteriskAlexa) project
* Amazon to provide [alexa information](https://github.com/alexa/) so we can hack and play
