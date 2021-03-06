![laserdisc logo](https://raw.githubusercontent.com/edweena/laserdisc/master/___laserdisc.gif)

# LASERDISC
## HTML5 Video Wrapper

WARNING: ALPHA RELEASE IN ACTIVE DEVELOPMENT. MOST OF THE FEATURES BELOW WORK, BUT SOME ARE STILL UNDER CONSTRUCTION. USE AT YOUR OWN RISK. BREAKING CHANGES WILL OCCUR UNTIL BETA RELEASE – WHICH WILL BE SOON

This is going to be the greatest video player of all time. At least, that is the plan. With that being said, it is only ever going to be in the semi-professional arena
because that's where all the cool stuff on the web is happening. If you want a really professional, conservative thing, use [video.js](http://videojs.com/), which does 
a bunch of stuff. However, LASERDISC does a bunch of stuff too, including many features video.js does not, making it the cooler pick.

### Setting up a LASERDISC sesh
```
npm install --save laserdisc
```

Grab the CSS file and dump into your HEAD:

```
https://s3.amazonaws.com/laserdisc-assets/laserdisc.css

//minified
https://s3.amazonaws.com/laserdisc-assets/laserdisc.min.css
```

Or via CDN:
```
http://dc6emjnxox7vk.cloudfront.net/laserdisc.min.css
```



### Video Formats
WEBM and MP4 must be included. Furthermore, names must indicate video width using the following convention: 'video/my_video_960.mp4'

```
video/
  my_video_640.mp4,
  my_video_640.webm,
  my_video_960.webm,
  my_video_960.mp4,
  my_video_1280.webm,
  my_video_1280.mp4
  etc...
```



## Example setup

HTML
```html
<div class="someclassname" id="someid"
  data-source="data/your_video_with_no_file_extension"
  data-poster="data/yourposter.jpg"
></div>

```


JS
```js
//import module
import LaserDisc from 'laserdisc';

//grab all the vids to turn into laserdiscs
const laserTarget = document.getElementById("someid")

//render
const options = {};
const item = new LaserDisc(lasersTarget, options);
```

### Styling + DOM

LASERDISC exposes several classes to use and style at will. By default, all videos will be responsive.

**Note**: Laserdisc will *replace* the provided DOM node with the following DOM structure

```css

.laser-outer-wrap
  .laser-inner-wrap
    .laser-poster-wrap
    .laser-video

```


### Options

You can pass a lot of options and stuff to LaserDisc.

```js
const options = {
  
  //Screen size ratio. Options '16:9', '4:3'
  ratio: '16:9',
  
  //widths of video files. If no sizes
  // are specified, then only data-source will be used.
  // Again, please make not of the naming convention
  // that is required for videos. Do not append file extensions
  sizes: [280,640,960,1280,1920],
  
  //default true
  loop: true,
  
  //default false
  controls: false,
  
  //default true
  muted: true,
  
  //default false
  autoplay: false,
  
  //default false. video will toggle play/pause on clicks
  clickToPlay: false,
  
  //default false. video will toggle play/pause on mouseenter, mouseleave
  hoverToPlay: false,
  
  //default false. Will display PNG over video until played
  showPlayButton: false,
  
  //CALLBACKS
  
  //called when video has begun loading
  onload: function(ev){
  },

  //called when video info is in. Before any seek events, make sure 
  // this has been hit
  onLoadedMetaData: function(){

  },
  
  //video has loaded enough frames to begin playing
  onCanPlay: function(ev){
  },
  
  //video is playing
  onPlay: function(ev){
  },
  
  //video is paused
  onPause: function(ev){
  },
  
  //end is over (please note: this event will only fire if 'loop' option is set to FALSE)
  onEnd: function(ev){
  },
  
  //onError
  onError: function(err){
  },
  
  //called on default browser schedule when video progress
  // is made
  onTimeUpdate: function(ev){
  },

  //Can be used if you want to handle clicks
  // manually. This callback will fire (if specified/passed in like below)
  // regardless of whether clickToPlay options is set to true
  // or not.
  onClick: function(ev){

  },


  //Called when duration of video updates.
  // This happens either when video is loaded
  // and duration data exists
  onDurationChange: function(ev){

  }
};
```

### Methods

There are also these.

```js
const item = new LaserDisc(laser[i], options);

//play function. Can optionally pass in time in seconds to
// begin at that moment
item.play();

item.pause();

item.mute();

item.unmute();

//float between 0.0 (muted) and 1.0 (full volume)
item.setVolume(level);

//jump to point
item.seekTo(timeInSeconds);

//Remove all event listeners and remove container
item.destroy();

//Manual load. You probably won't need this much.
item.load();

//Pass in new video and reload. Optional (recommended) array of sizes.
// Make sure to follow naming convention.
item.swap(newFile, [640, 960, 1280, 1920]);

//set volume (between 0.0 and 1.0);
item.setVolume(newVolumeFloat);

```


### Properties

```js
item.duration;

//retrieve current time of video (in seconds)
// note: this is not the same as setting 
// currentime directly on video
item.currentTime;

//retrieve current volume
item.volume;

```





*Cool logo by Stephanie Davidson*

