---
author: thearcticrose
category:
  - narrowboats
cover:
  alt: img_5328
  image: /wp-content/uploads/2024/02/img_5328-3422523793-e1707738841108.jpg
date: "2024-02-02T17:07:32+00:00"
guid: https://theethicalengine.wordpress.com/?p=19
tag:
  - batteries
  - boats
  - home-assistant
  - remote-monitoring
title: Narrowboat Remote Battery Monitor
url: /2024/02/02/narrowboat-remote-battery-monitor/

---
If you live on a boat then batteries are probably something on your mind quite a lot, along with emptying the loo and having enough water in your tank.

It’s really important to know the state of your batteries so you can decided when to charge them. A surprising number of boats don’t have a simple voltmeter fitted. Ours didn’t when we got her. Sticking your voltmeter probes into vacant 12v socket works perfectly well for quick checks. A cheap and cheerful ‘lighter socket” meter can be left plugged in all the time.

There are more sophisticated solutions. For instance, we have a [SmartGauge](http://www.smartgauge.co.uk/smartgauge.html). That gives accurate voltage readings for both our leisure and starter batteries, and a solid estimate of the state of charge of the leisure bank. There are many others but by-and-large you have to be aboard to read them.

What if you want to know what’s going on when you’re away for a while? Or get a bit more data so you can see trends? That’s what motivated me to build something a bit more sophisticated.

I briefly toyed with the idea of just pointing a webcam at a voltmeter. It’s a workable solution, but not much good if you want to see trends, or get alarms.

I already had a basic home automation setup using Home Assistant so that seemed a logical place to start. I also had a drawer full of electronics oddments (Raspberry Pis , Arduino, and so on)

I’ll go into more detail in later posts but my overall setup is:

- [Raspberry Pi 4](https://www.raspberrypi.com) running [Home Assistant](https://www.home-assistant.io)
- Pi Zero with an [Automation HAT](https://shop.pimoroni.com/products/automation-hat-mini?variant=31478878077011) and some custom MQTT code
- Everything connects to our onboard WiFi, and can be accessed remotely via the HA app.

Coming soon…

- [Part 1: Home Assistant setup](/2024/02/11/part-1-home-assistant-setup/)
- Part 2: Getting the voltage information
- Part 3: Hooking everything up
- Part 4: Dashboards and data
