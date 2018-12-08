# WebRTC Messaging Demo App
Peer-to-peer (e.g. bot-to-desktop) messaging.
When both peers are on same network this messaging provides low latency and high bandwidth - suitable for gamepad and large, fast file transfers.

This code follows [ScaleDrone](https://www.scaledrone.com/blog/webrtc-chat-tutorial/) and [Shane Tully's](https://shanetully.com/2014/09/a-dead-simple-webrtc-example/) tutorials

[![Deploy](https://www.oomwoo.com/wp-content/uploads/2018/11/deploy.png)](https://kaia.ai/deploy)

## Live Demo
- [Sample App](https://kaia.ai/view-app/5bf910b2b7f0731e286bbccc)
- Sample app [source code](https://github.com/kaiaai/tree/master/webrtc-messaging)

## Installation
Kaia.ai robot apps run on Android smartphones. To run the sample app:
1. Go to [kaia.ai](https://kaia.ai/), familiarize yourself with how the robot platform works
2. Optional, but highly recommended: if you don't have Kaia.ai account, create an account
3. Go to Google Play, search for "kaia.ai" to find and install Kaia.ai Android app
4. Launch Kaia.ai Android app on your Android smartphone
5. In Kaia.ai Android app: (optional, but highly recommended): sign in, navigate to Kaia.ai App Store
6. Choose a robot app to launch
7. Optionally: click the heart icon to pin the robot app to your launch screen 

## Develop and Publish Your App
- clone the repository
- navigate to My Files, create a sub-folder at Kaia.ai
- upload all repository files into the new sub-folder
- navigate to My Apps, click New App, fill out and submit app form to publish your new app

## WebRTC Messaging Code Overview
```js
let messaging = await createMessaging({ io: io(), rooms: roomName });
let webrtc = await createWebRTCHelper({ messaging: messaging, eventListener: onWebRTCEvent, room: roomName });
// Peer has joined 
webrtc.send('Hello');
 
function onWebRTCEvent(err, msg) {
  switch (msg.event) {
    case 'dataChannelMessage':
      console.log('Received message: ' + JSON.parse(event.data));
      break;
    case 'dataChannelOpen':
    case 'dataChannelClose':
      console.log('Data channel is ' + msg.dataChannel.readyState));
      break;
    case 'dataChannelError':
      console.log('Data channel error: ' + msg.err); 
  }
}
````
