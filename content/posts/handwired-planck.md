---
title: "Handwired Planck"
date: 2020-04-08T07:30:25-05:00
draft: false
author: "Shem Sedrick"
tags:
  - keyboards
  - soldering
keywords:
  - keyboard
  - planck
  - handwired
description: "My adventure into handwiring a keyboard"
showFullContent: false
---

# Handwired Planck

A foray into handwired keyboards


### Why the Planck
This isn't my first custom keyboard. Nor will it probably be my last. But this is the first time I did the wiring myself including setting up the microcontroller.

I started into keyboards by buying a Magiforce 86. I got it as a Drop (back then it was called MassDrop) and started out with Cherry MX Brown switches. It was a good board, but I found the browns to be a bit mushy. That, and I had started to get some strain on my wrists from the mouse and keyboard.

I then dove into [/r/mechanicalkeyboards](https://reddit.com/r/mechanicalkeyboards) and researched the various types and styles of keyboards. Split keyboards, ortholinear keyboards were the most interesting to me. I decided to try out the [Levinson](https://keeb.io/collections/frontpage/products/levinson-lets-split-w-led-backlight).

I thoroughly enjoyed my split Planck. It's been a great keyboard for everyday use. Keeping everything within 1 movement from home row as much as possible has great benefits.


### Into handwiring
I have always had a desire to better understand electronics and computers. They fascinate me. So naturally I wanted to get a little deeper into how [QMK](https://qmk.fm) and keyboards work.


### Parts Assemble!

I collected the initial parts. I got [Kaihl Speed Heavy Switches](https://drop.com/buy/novelkeys-x-kaihua-kalih-speed-heavy-switches), the Burnt Orange variety. I prefer heavier switches and wanted to try out the Speed switches because of their quicker actuation.

I wanted a fairly minimal design, so I got [PCB plates](https://keeb.io/collections/cases-plates/products/levinson-keyboard-case-plates) from keeb.io. I was a little worried that they might bow when typing on them, but that hasn't been the case for me.

I wanted to try out XDA style keycaps and really liked the [Mito Canvas](https://mitormk.com/portfolio/xda-canvas-round-2-2018/). I got those in another Drop.

Once I got all those parts, I couldn't help but plug the switches into the plates, pop on the keycaps and enjoy the view. It's only so satisifying to have all the physical parts put together though, so now I needed all the electronics.

I got some [wire](https://www.amazon.com/gp/product/B07BWC596B) and some [diodes](https://www.amazon.com/gp/product/B079KJ91JZ) back in 2018. As soon as I got them, I soldered all the diodes to the switches. To solder the diodes, I bent all the diodes on one side against a book. After making a loop on one side with a pair of needlenose plier, I set that on the left pin of the switch and applied solder to get it to stay.

Then, as it always does, life happened and I got busy. This project fell by the wayside until March of 2020.

### Wiring things up
With a sudden event that forced most people to work from home, I now had a bit more time on my hands. I also forgot to bring my keyboard home. Typing on the Macbook keyboard reminded me why I got into keyboards in the first place, and I decided to finally finish this project.

I started by soldering the left side of the board. I started with the rows:
{{< figure src="img/handwired/left-side-rows.jpg" alt="Left half with rows soldered" position="center" caption="Left side rows" >}}
