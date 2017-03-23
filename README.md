# alexa command line client

A naive command line client to interact with alexa voice service (record, post audio, play response)

<a href="http://www.youtube.com/watch?feature=player_embedded&v=W00Xq1SpXCs
" target="_blank"><img src="http://img.youtube.com/vi/W00Xq1SpXCs/0.jpg" 
alt="alexa interaction by command line" width="240" height="180" border="1" /></a>

Created for my [Big mouth alexa bass](https://github.com/neyfrota/Big-Mouth-Alexa-Bass/blob/master/bin/alexa.pl) project. Amazon alexa client app was too overkill and complex, so i need trim down.   

## Install 
* copy ```alexa``` script to something in your path (no need clone repo)
* Install dependences
    * ```sudo apt-get install sox``` we use sox to record and manipulate audio
    * ```sudo apt-get install mplayer``` we use mplayer to play audio

## Configure

Visit [alexa-avs-sample-app for Raspberry-Pi](https://github.com/alexa/alexa-avs-sample-app/wiki/Raspberry-Pi) and follow steps 2 (*Register for an Amazon developer account*) and step 3 (*Create a device and security profile*)

Create a file  ```~/.alex.conf``` with this content
```
ProductID=<ProductID from step 3>
ClientID=<ClientID from step 3>
ClientSecret=<ClientSecret from step 3>
ReturnURLs=https://localhost:3000/authresponse

```

## Authenticate

* run "```alexa login```" so we can create a custom URL to authenticate the app
* Copy url and visit in your browser
* Login with same credential at step 2
* Extract code value from response URL 
* run "```alexa login <code>```" so we generate access token and save local to persist authentication

## Test audio

* run "```alexa test```" to record and playback, so you can hear what alexa will hear
* Adjust your system for better possible audio. 

## ask

* run "```alexa ask```" 
* Ask something
* listen alexa response