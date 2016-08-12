# LASERDISC
## HTML5 Video Wrapper

WARNING: ALPHA RELEASE

This is going to be the greatest video player of all time. At least, that is the plan. However, it is only ever going to be in the semi-professional arena
because that's where all the cool stuff on the web is happening. If you want a really professional thing, use [video.js](http://videojs.com/). It does 
a bunch of stuff, but LASERDISC does a bunch of stuff too.

### Setting up a LASERDISC sesh
- `npm install --save laserdisc`


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
```
<div class="someclassname"
  data-source="data/your_video_with_no_file_extension"
  data-poster="data/yourposter.jpg"
></div>

```


JS
```
//import module
import LaserDisc from 'laserdisc';

//grab all the vids to turn into laserdiscs
const lasers = document.getElementsByClassName('someclassname');

//render each one
for (let i = 0; i < lasers.length; i++ ){

  const options = {};

  const item = new LaserDisc(lasers[i], options);
  
}
```


### Options

You can pass a lot of stuff to LaserDisc.

```
const options = {
  
  ratio: '16:9', //Screen size ratio. Options '16:9', '4:3'
  
  sizes: [280,640,960,1280,1920]
  
  
};
```



