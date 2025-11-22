---
author: thearcticrose
category:
  - electronics
cover:
  alt: eufyvac
  image: /wp-content/uploads/2024/02/eufyvac-3882431315-e1707816513592.jpg
date: "2024-02-13T17:17:56+00:00"
guid: https://theethicalengine.wordpress.com/?p=39
tag:
  - batteries
title: Robovac battery pack
url: /2024/02/13/robovac-battery-pack/

---
Our robot vacuum (a [eufy Robovac 11S](https://uk.eufy.com/products/t2108)) has recently been refusing to charge. The error (solid red light while charging) indicated a failed battery. Eufy's vacs are nicely put together and easy to work on, so it was a simple matter to get the old pack out. Two standard screws and you're in.

I measured the voltage on the pack at 10.2 volts. The battery pack suggests a voltage of 14.4V so 10.2V is rather flat.

![](/wp-content/uploads/2024/02/image.jpg?w=1024)Dead battery pack

This type of battery pack is made up of 4 barrel type cells each with a typical voltage around 3.7V. 4\*3.7 gives a pack voltage of 14.8 fully charged. So a couple of things might have happened. Either one cell in the pack has given up so we'll never get over about 11V - this is the most likely scenario with cells in series. Or the pack as a whole is on the way out. Or it just got so heavily discharged that the charger in the vac decided it was dead.

That final scenario is the place I decided to start, even though it's not the most likely. There's no obvious signs of the burst cell, the pack isn't hot or squishy. So we might be able to get some charge into it. By using a bench power supply where I can control voltage and limit the current, it will be safe to see if we can push some charge in. Please note, you should **NEVER** charge lithium cells like this. Use a proper charger or you'll burn your house down. Seriously. They are a superb battery technology but just treat them with respect. I'm not attempting to charge these cells fully, just see if I can wake them up. If they do come back to life I'll pop them back in the vac to charge properly.

So what's safe? This pack is rated 14.4v at 2600mAh. It looks to be made from standard barrel type batteries each with a voltage of 3.7V and a capacity of 2600mAh. The data sheet for a generic cell of this type suggests a rapid charge current of 2.4A or a standard rate of 480mA. This is fairly typical of these cells, you can usually charge at a current approximately equal to the amp-hour rating. As a ball-park anything less than a tenth of the maximum charge can be considered safe as a starting point. To be extra safe I limited the current to 100mA and started with a voltage of around 10V, which should do absolutely nothing as it's less than the battery voltage. And it did! No amps at all. So there's not an obvious short anywhere. I edged up the voltage, no current flowed until I got to about 13V. After a brief peak it settled at around 50mA. I upped the voltage to 14.1 with 100mA flowing.

![](/wp-content/uploads/2024/02/img_5624.jpg?w=768)Gently charging the pack

Then I left the pack charging for a little while under constant observation. I placed it on a fireproof bench and had the power supply positioned so I could see the display wherever I was in the room. After about 15 minutes the current settled down to about 30mA. I'd expect a bit more at this voltage but I left it to see what happened. Plan was to charge for no more than an hour then check the terminal voltage to see if any charge was being accepted.

After an hour or so the current had dwindled to almost nothing (less than 1mA). After taking the battery pack off the power I checked its open circuit voltage. It was 10.35V. I would have expected more of an increase if the whole pack was simply discharged. This leads me to suspect a single dead cell. The other 3 could be recoverable so it may be worth splitting up the pack.
