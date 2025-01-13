---
layout: post
title: Embedding YouTube Videos
subtitle: The beginning of Tournatube
tags: [Dota 2, tournament, streaming]
---
<style>
.box-note {
  background-color: #385170;
  border-left-color: #9fd3c7;
}
code {
  color: #fdb44b;
}
</style>

**Embedding YouTube videos and customising them for spoiler free watching**

Tournatube is my first web project. The idea is to create a place to watch streamed tournaments spoiler free. This is achievable by embedding YouTube links without titles, thumbnails or timelines that spoil the outcome of each game.

**the code**

It was surprisingly easy to embed a link without controls. I created a test solution [here](/tournatube).

{: .box-note}
Check [YouTube's up to date player parameters](https://developers.google.com/youtube/player_parameters) before going ahead as things might have changed. Note that we can add other parameters as needed, such as end time with **&end**.

~~~
<iframe src="https://www.youtube.com/embed/YOUTUBEVIDEOID&start=NUMBEROFSECONDSFROMVIDEOSTARTTOYOURDESIREDSTARTTIME&disablekb=0&fs=1&showinfo=0&autoplay=1&controls=0&color=white&rel=0&playsinline=1&enablejsapi=1"
    title="YouTube Video Player" frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    allowfullscreen></iframe>
~~~

Here is an example of the above html in action. Note that we can't see the timeline, but can still see the title of the video in the video overlay. We can use the spacebar and arrow keys to navigate the video.

~~~
<iframe width="560" height="315" src="https://www.youtube.com/embed/SYepvZU7rsE?si=f6qX9BUuS1lJ7sfu&amp;start=3017&disablekb=0&fs=1&showinfo=0&autoplay=1&controls=0&color=white&rel=0&playsinline=1&enablejsapi=1&playlist=SYepvZU7rsE"
    title="DreamLeague Season 25 - Closed Qualifiers - WEU - Day 3 - Stream A" frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    allowfullscreen></iframe>
~~~

<iframe width="560" height="315" src="https://www.youtube.com/embed/SYepvZU7rsE?si=f6qX9BUuS1lJ7sfu&amp;start=3017&disablekb=0&fs=1&showinfo=0&autoplay=1&controls=0&color=white&rel=0&playsinline=1&enablejsapi=1&playlist=SYepvZU7rsE"
    title="DreamLeague Season 25 - Closed Qualifiers - WEU - Day 3 - Stream A" frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    allowfullscreen></iframe>

Now we need to add CSS to hide the video title and other YouTube buttons, set the video to fill the width of the browser window.

Wrap the iframe player in this div.

~~~
<div class="yt-embed-holder">
  </div>
~~~

Add this custom CSS to the page.
~~~
<style>
    body {
        background-color: #000;
    }
    .yt-embed-holder{
        width: 100%;
        overflow: hidden;
        aspect-ratio: 16/9;
        pointer-events: auto;
    }
    .yt-embed-holder iframe{
        width: 300%;
        height: 100%;
        margin-left: -100%;
    }
</style>
~~~

Note that you may need to allow video and audio autoplay in your browser.
![autoplay setting in Firefox](/assets/img/autoplay.png)

Now all that is left to do is fetch YouTube video links and organise the tournament vods by day.


