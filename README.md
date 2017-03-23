# alexa command line client

A naive command line client to interact with alexa voice service (record, post audio, play response)

<a href="http://www.youtube.com/watch?feature=player_embedded&v=W00Xq1SpXCs
" target="_blank"><img src="http://img.youtube.com/vi/W00Xq1SpXCs/0.jpg" 
alt="alexa interaction by command line" width="360" height="270" border="1" /></a>

Created for my [Big mouth alexa bass](https://github.com/neyfrota/Big-Mouth-Alexa-Bass) project. Amazon alexa client app was too overkill and complex, so i need trim down.   

## Install 

* no need git checkout. Its just ONE file. follow this.
* ```curl https://raw.githubusercontent.com/neyfrota/alexa-command-line-client/master/alexa > /tmp/alexa``` to save file at your temporary folder
* ```head /tmp/alexa``` to check what we download. If all fine, you see my comments
* ```chmod a+rx /tmp/alexa``` to make this executable
* ```sudo mv /tmp/alexa /usr/bin/alexa``` to move to a place that everybody can use.
* ```sudo apt-get install sox``` to install sox. we use sox to record and manipulate audio
* ```sudo apt-get install mplayer``` to install mplayer. we use mplayer to play audio
* ```alexa test``` to test alexa script, record and playback.
* Adjust your system for better audio possible. 
* done

## Configure

Visit [alexa-avs-sample-app for Raspberry-Pi](https://github.com/alexa/alexa-avs-sample-app/wiki/Raspberry-Pi) and follow step 2 (*Register for an Amazon developer account*) and step 3 (*Create a device and security profile*)

Create a file  ```~/.alexa.conf``` with this content
```
ProductID=<ProductID from step 3>
ClientID=<ClientID from step 3>
ClientSecret=<ClientSecret from step 3>
ReturnURLs=https://localhost:3000/authresponse

```

## Authenticate

* run "```alexa login```" to get a custom URL to authenticate the app
* Copy url and visit in your browser
* Login with same credential at above step 2
* Get code from response URL (*yes! page fail to load. its ok. Focus in url. Get code value between \'code=\' and \'&\'*)
* run "```alexa login <code>```" so we generate access token and save local to persist authentication


## Ask

* run "```alexa ask```" 
* Ask something
* listen alexa response

## Credits

We standing on the shoulders of giants. This are my giants.

* Miguel Mota with some code examples about alexa [authentication](https://miguelmota.com/blog/alexa-voice-service-authentication/) and [interaction by curl](https://miguelmota.com/blog/alexa-voice-service-with-curl/).
* Russell Grokett wit more code examples in they [asterisk-raspberryPi-alexa](https://github.com/rgrokett/RaspiAsteriskAlexa) project
* Amazon to provide [alexa information](https://github.com/alexa/) so we can hack and play
* perl, linux etc etc
