---
author: thearcticrose
category:
  - electronics
date: "2024-03-02T14:19:23+00:00"
guid: https://theethicalengine.wordpress.com/?p=55
tag:
  - batteries
  - pi-zero
  - python
  - remote-monitoring
title: 'Part 2: Getting the voltage information'
url: /2024/03/02/part-2-getting-the-voltage-information/

---
So we got Home Assistant setup in part 1, now we need to get some data from our battery bank. I opted for a Pi Zero with an [Automation HAT-mini](https://shop.pimoroni.com/products/automation-hat-mini?variant=31478878077011) from Pimoroni.

- The Pi Zero is small, with a low power consumption.
- But it’s still a Pi with all the goodness you’d expect, such as a Linux based OS, Python, ssh etc. Just with rather less oomph.
- The Automation HAT had 3 analogue to digital inputs (ADC) that work up to 24V
- It has a relay output and some general purpose digital IO that might come in handy
- It has a small LCD which can be used to provide a local voltage display. Or anything else you might come up with.

You’ll need to install and configure the Pi Zero. So grab a micro SD card and setup the Pi Zero with the usual Raspberry Pi OS. Instructions [here](https://www.raspberrypi.com/documentation/computers/getting-started.html).

I usually do a headless install, but you can connect a keyboard and monitor and set it up interactively. The Pi imager makes it easier to setup a Wi-Fi connection when you make the boot media. If you want to do it the old fashioned way check out this [guide](https://www.instructables.com/The-Ultimate-Headless-RPi-Zero-Setup-for-Beginners/).

Make sure to connect the Pi Zero to your wifi so it can see your Home Assistant system. Both will probably be using dynamic addresses by default (DHCP). Setting static IPs will make your life easier.

Once the basic Pi setup is done, power it off and fit the Automation HAT mini to the PiZero. It just pushes onto the GPIO header on the Zero. Watch out as not all versions of the PiZero come with the header pins soldered in place. Power back up and login. From here on I’ll assume you’re using the command line via secure shell (ssh). If you’ve connected a monitor and keyboard then open a terminal window.

Install the Python library and tools simply, run the following command

```
curl https://get.pimoroni.com/automationhat | bash
```

For more details see the guide from Pimoroni [here](https://learn.pimoroni.com/article/getting-started-with-automation-hat-and-phat).

To test just try running one of the examples

```
cd ~/Pimoroni/automationhat/examples/hat-mini/python3 analog.py
```

The analog example will display the voltage n the ADC pins. Even with nothing connected you should see something other than zeros as these always a little bit of noise.

If all is good then install my app from [GitHub](https://github.com/thepurpleplatypus/BatteryMonitor). There’s more detail in the readme file in the repository. Basically run the command below with details that match your install.

```
python3 mqtttest.py --broker <broker name> —topic <mqtt topic> --port <mqtt port> --username <username> --password <passowrd> --tls—-broker Hostname of your home assistant server, e.g. home assistant.local—-topic The MQTT topic to publish your data to, e.g. batterymonitor —-port The default unencrypted MQTT port is 1883. The encrypted port is 8883.—-username & —-password These are usually your home assistant login details though you may wish to create a specific one for MQTT—-tls Use this flag if your MQTT connection is encrypted
```

You’ll see some diagnostics in the terminal window verifying the connection and updating the voltage values every 60 seconds. Leave it running for a few minutes and then check what’s coming through to your server.

To check what messages your are receiving go to Settings -> Devices & Service -> Integrations

Look for the MQTT integration. Click ‘“Configure” and then “Start Listening“. You will start to see messages arriving every minute or so. They will be in a format called JSON which is a standard for information interchange over the web.

![](/wp-content/uploads/2024/03/image.jpg?w=1024)![](/wp-content/uploads/2024/03/image-1.jpg?w=1024)

If all is well then it’s time to hook this data up to some sensors in HA. We’ll cover this in part 3.

See also:

- [Part 1: Home Assistant setup](/2024/02/11/part-1-home-assistant-setup/)
- Part 3: Hooking everything up
- Part 4: Dashboards and data
