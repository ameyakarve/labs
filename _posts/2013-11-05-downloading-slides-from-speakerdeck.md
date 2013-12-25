---
layout: post
title: "Downloading slides from SpeakerDeck"
category: labs
---

I was doing this course at college, where the professor decided to make the finals an open-book exam. He puts his slides up on SpeakerDeck. So, like I needed to figure out a way to get them printed without too much of a hassle. 

When I opened up the Networks tab on my Chrome explorer, I figured out that the SpeakerDeck widget actually loads the slides as image files; all I needed to do now was to find a pattern and systematically get all the images. Whenever I hit the next button, the widget made an XHR to the image file of the next slide and fetched it. The URL looked something like 

` https://speakerd.s3.amazonaws.com/presentations/xxxxxxxxxxxxxxxxxxxxx/slide_1.jpg?yyyyyyyyyyyyyy `

So, all I had to do was to write a quick Shell script, and the files were all mine. The final script was something like 

` for i in 0 1 2 3 4 5 6 7 8 9 10; wget 'https://speakerd.s3.amazonaws.com/presentations/xxx/slide_'$i'.jpg?yyy'; end; `

Note that this is a function for Fish Shell. You could as well write a corresponding Bash script easily enough. Also, the numbering starts from 0; 10 slides means 0-9. 
