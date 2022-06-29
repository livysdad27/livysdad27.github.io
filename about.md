---
title: About
layout: page
permalink: "/about/"
---
I built this site for a couple reasons.  The first is that I used to enjoy blogging and writing now and again.  Sometimes this was about work and often it was about family, fishing or mini-farming and sometimes combinations of the above.  Second, I chose the platform I did so that I'd get my hands dirty learning something new.  It turns out static site generators are very powerful but non-trivial, at least for me.  

### About This Site
This site is built using [Jekyll](https://jekyllrb.com) and hosted on Github using [Github Pages](https://pages.github.com).  I use the [Minima-modified](https://github.com/livysdad27/minima-modified) theme, that I forked from minima, although there are a ton of [really great themes](http://jekyllthemes.org) for Jekyll out there.

### About the Weather
The [Weather link](https://weather.boggyhollowfarm.com/) goes to a [weewx](https://weewx.com/) instance running on an Amazon Lightsail instance.  It's fed from a [Raspberry Pi 400](https://www.raspberrypi.com/products/raspberry-pi-400/) running in my house that polls for UDP pakcets from a  [Weatherflow Tempest](https://weatherflow.com/tempest-weather-system/).  I use the Weewx [Weatherflow UDP driver from captain-coredump](https://github.com/captain-coredump/weatherflow-udp) which works rather nicely!  The Tempest comes with a REST, UDP Broadcast and Websocket API that are all fun to play with.  It also has out of the box integrations including to [Weather Underground] where my station is named KWAOLYMP512.  I got the device because we have a rather large garden and seeing the weather trends hyper-locally is a nice trick.  People always ask if I plan on setting up a smart sprinkler integration but I don't think so.  I like having the data but the nature of a garden is to literally get your hands dirty!