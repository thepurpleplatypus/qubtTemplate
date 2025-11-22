---
author: thearcticrose
category:
  - electronics
cover:
  alt: img_1689-1
  image: /wp-content/uploads/2024/02/img_1689-1.jpg
date: "2024-02-11T19:50:46+00:00"
guid: https://theethicalengine.wordpress.com/2024/02/11/part-1-home-assistant-setup/
tag:
  - home-assistant
  - remote-monitoring
title: 'Part 1: Home Assistant setup'
url: /2024/02/11/part-1-home-assistant-setup/

---
The core of my monitoring system is [Home Assistan](https://www.home-assistant.io/) t. It’s probably overkill if you just want to monitor a couple of voltages, but if you think you want to do a bit more, then this is the way to go.

Home Assistant (HA) is designed for home automation, meaning tasks like temperature monitoring, controlling your heating system, activating lights and so on are relatively easy. It gives you a way to collect data from all sorts of sensors and then take actions based on them.

There are alternative home automation systems like [openHAB](https://www.openhab.org/). And there are other ways of collecting data and “doing stuff” such as [Node-RED](https://nodered.org/). Check those out as they may suit your needs better.

Now you need some hardware. There are some [off-the-shelf](https://www.home-assistant.io/green) options. But I prefer the DIY route with a Raspberry PI. Checkout the [getting started](https://www.home-assistant.io/installation/) section of the HA website to see what bits you might need.

I have run Home Assistant successfully on a Pi3 with 1GB RAM. However, as soon as you start using more substantial integrations or fancy dashboards you might find yourself running out of memory. My current setup is a Pi4 with 4GB RAM. It rarely uses more than 2GB so I’ve got plenty of headroom.

I just run everything on an SD card (SanDisk, 64GB) but if you plan to store a lot of data or really hammer the drive then you might want to consider an SSD drive. There’s a useful guide [here](https://home-assistant-guide.com/guide/how-to-boot-home-assistant-on-a-raspberry-pi-4-of-an-ssd/).

The basic setup of HA is really easy, just follow the instructions [here](https://www.home-assistant.io/installation/raspberrypi). Go with the full-fat Home Assistant Operating System option unless you really really know what you are doing and want to run in on a containerised system like Docker.

The installation wizard will guide you through the process and you’ll end up with a basic install with some example components. You won’t be able to do very much as yet, but have a play around and see what’s what.

You’ll need some add some ‘integrations’ to HA to get ready for the next stage. They are:

- An MQTT integration (part of Home Asssitant)
- An MQTT broker (best option is [Mosquitto)](https://github.com/home-assistant/addons/blob/master/mosquitto/DOCS.md)

And if you want to access Home Assistant remotely you’ll either need to setup HA Cloud (easy, but has a cost) or use the [DuckDNS](https://www.home-assistant.io/integrations/duckdns/) integration (a little more work but free).

I’ll give a bit more detail of my specific configuration for each of these items as we get to using them.

There’s also a phone/tablet app for HA which is really simple to use. I recommend giving it a try - though access via a browser works just fine.

See also:

- [Part 2: Getting the voltage information](/2024/03/02/part-2-getting-the-voltage-information/)
- Part 3: Hooking everything up
- Part 4: Dashboards and data
