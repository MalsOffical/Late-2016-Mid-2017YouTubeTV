Late 2016-Early 2017YouTubeTV

A project to revive the old Late-2016(console)Early-2017 YouTube TV HTML5 Web App. Project used to make this: https://github.com/theDSi2homebrewGuy/2016YoutubeTVplus/

My instance (need to fix not getting past the YT splash screen):

https://malsoffical.github.io/Late-2016-Mid-2017YouTubeTV/

Project's i'm using:

https://github.com/theDSi2homebrewGuy/2016YoutubeTVplus

Orginal project:

https://github.com/erievs/2016YouTubeTV

---------------------------------------------------------------------------------------------------------------------

Watch this guide to install it:

https://www.youtube.com/watch?v=tXKlVcWBzEY

Also follow THIS guide if you close cmd and want to go on this project:

WARNING: do NOT close "CMD", or else it will be "RESTART TIME!"

1. go to downloads in file explorer and open "2016-2017YouTubeTV-main"
2.copy file path and open "CMD" them paste it in.
3.press enter, then type "npm start" and press enter.
4.wait to finish then go to "http://you.re.web.link:8090"
5.Enjoy!


------------------------------------------------------------------------------------------------------------------
Moddified version:

Credits
YouTube/Google

Erie Valley Software/Erievs

youtube-dl-exec [https://github.com/microlinkhq/youtube-dl-exec]

cors-anywhere [https://github.com/Rob--W/cors-anywhere?tab=readme-ov-file]

qr-code [https://www.npmjs.com/package/qrcode]

dx for his knowlage

Venus5687 found a sound effect

Before Posting An Issue!
Do not hide your damn local ip adress, I have no idea why SO many people do not know that a 192.168.1.blank or equivlient is not your public IP. I cannot help you if you're hiding part of your screen.

Do not report an issue if you modified the port or adress you're hosting this on , you're on your own if you wanna host it on a different port.

Be damn well sure you read through this ENTIRE readme, I'll close your issue if you're asking for help and I know for a fact you missed something here!

Progress Report:(not made by me).

Search - 100% Done

Status: Done. Next Steps: None.

Guide - 100% Done

Status: Done Next None;

Browse/Channels - 85% Done

Status: Working on finishing up the browse API, the homepage is close to being done but other parts may need work. Next Steps: Fully finish the implemtion.

4a. Watch - 90% Done

Status: Videos play, a tiny bit buggy somtimes **you need to play and pause and play again** for progress to work, but works.
Next Steps: Make it less bugger and chunk less data.

** Right now SOME videos don't work, this is just because I haven't done the WebM to H264 fallback yet, it will be fixed **
4b. Watch Interactions - 100% Done

Status: You can sub, unsub, like, and they'll all load.
Next Steps: Nothing.
Pairing - 30% Done

Status: Got some end points implemented, but they don't create the code. Next Steps: Get it to create the pairing code.

Sign In - 75% Done

Status: Implemented /o/oauth2/code and it properly grabs the oauth code or whatever it is calle, and Implemented /o/oauth2/token!! Next Steps: Make it so the token can request the token more than 5 times (rn you have to be fast).

Assets - 95% Done

Status: Most of the assets are there, with a few missing sound files and 404 errors that need to be addressed. Next Steps: Find the missing assets and add em.

Playlists - 20% Done

Status: The api seems to be there but just gotta figure how to format the browse api properly for the client to use em. Next Steps: Figure how to format the browse api properly for the client to use em.

Info On Hosting
In the YouTube TV client scripts (tv-player and app-prod), APP_URL is where it's hosted on assets, apis, and more are all there, PROXY_URL is where the CORS-ANYWHERE proxy is hosted on, and APP_HOST is just the hostname.

Settings are in ./back/settings.json!

serverIp: the sever IP adress you set with the 2016youtubetvsetup.js script! [default: localhost]

expBrowse: make the server use the wip browse api that fetches from the YouTube server, it is mostly complete! [default: true]

Be careful with your token folder, this has device ids and also has oauth tokens, I had issues when I didn't save it to a json file, luckly had no issues with refreshing so it doesn't save when you refresh. Just don't leak it or anything, it should expire anyways.

We Use:

Port 8090, you maybe to change this without modifications,

Port 8070 (this HAS to be a fixed port since it cannot be hosted on the same 8090 port easily, you can change it but you'll need to alter scripts)

How This Works
The server is a middleman in bewteen the YouTube TV client and InnerTube, and hosts the TV webapp itself.

The server translate the new YouTube Data from InnerTube into a format this understands, since YouTube stopped giving us V5 data.

Cool Things To Know
This doesn't need FFMPEG, videos are streamed straight from googlevideo link throw a CORS proxy! (idk if yt-dlp requires it I don't think so, you only need it to merge formats iirc).

This uses DASH formats, so this should work into the future (of course APIs may change, but the video playback is yt-dlp based so it'll probbaly be fine).

The TV Player uses a custom system for fetching videos, as I had troubles with the original MediaSource BS it uses, it used media-source but ran into too many issues with how the player set it up. So yeah this player script is quite modifed.

This should support JavaScript ES5 now, before I used const and let and for a little time fetch(), now it uses XHR for the custom MediaStream stuff. Which means now it can run on era appropriate smart devices, well at least when I do IP adressed rather than localhost!

Why We Use "youtube-dl-exec"
This is so we can get video urls, without having to deal with all the chiper bs you have to deal with no ** you will now need python3.7 or higher installed! though **

Why We Use "qr-code"
Just to make qr codes for the google chart api implementation.

Why We Use "cors-anywhere"
YouTube has CORS on their googlevideo links (I forgot which settings) and it will give a CORS error if you try to get it, luckly this exsits so googlevideo links are all going to be filtered through port 8070!

Supported YouTube TV Clients
We only offically supprort clients which use InnerTube version 5.20150715 as of right now.

Be aware though it does require some patching of the app-prod.js to get it working properly, this is due to me having to base off of a InnerTube v6 response as no V5 exsit.

This MAY (and I emphasise MAY) work on "6.20170807" clients without modifying models and some other parts of the app-prod.js.

[Look at and search from a.register("tiles/video_tile.html"), model.durationLabelCustom, and customVideoTileKg if you want an understanding of what I had to do to get it to work."]

Clients I May Choose To Support In The Future
Client V4 (https://web.archive.org/web/20140517113435/https://www.youtube.com/tv#/?mode=search)

6.20170807 (https://web.archive.org/web/20170930120178/https://www.youtube.com/tv#/search?resume)

2017 - 2018 -(https://web.archive.org/web/20170301064917/https://www.youtube.com/tv#/search?resume (6.20170807)

(The guide api should work on the above one, since that's what we requested for the json data)

What Will Never Happen are clients that fully use GDATA, now there's a chance I may support client V4 as that uses innertube for search and stuff, but not fully GDATA ones. Just use YT2009 at that point!

Other

Newer icons for guide

(Maybe) tweak player a TINY bit

(Sure i will do this) change icon/icons on SERACH.

OG Other - Support other versions of YouTube TV

Other languages

Fix grammar

Enjoy!