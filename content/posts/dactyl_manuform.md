---
title: "Dactyl Manuform"
date: 2022-07-26T20:20:20-05:00
draft: false
author: "Shem Sedrick"
tags:
  - keyboards
  - soldering
  - ergonomics
keywords:
  - keyboard
  - handwired
  - dactyl
  - manuform
description: "Keyboard #2: Further learning"
showFullContent: false
---

# Dactyl Manuform

I've been wanting to build a Dactyl Manuform for a while. Since diving into
mechanical keyboards, I've been particularly interested in the ergonomics of
typing. The [Dactyl](1) is an interesting keyboard for a couple of reasons.
* It's is parameterized. This means you can change a few inputs and get a customized keyboard.
* The concave nature and thumb cluster improve ergonomics.

I've been daily driving the my [handwired planck](/posts/handwired-planck) for
about 2 years now and have really liked the keyboard. It's been rock solid with
one exception: I have a bad wiring on the Raise key which sometimes means the
key doesn't get recognized. ¯\_(ツ)_/¯

And so it was time to build a new one. Because that's just how things go when
you fall down the keyboard rabbithole.


# A Handwiring Guide
When I set out to build the Dactyl Manuform I also wanted to contribute back
with as comprehensive of a guide as I could. It's a common issue for people
looking to get started. Hopefully this can help others looking for resources.

## Parts

## The Diodes
I start by wiring the diodes to the switches. The trick is to bend the diodes
into a loop to allow the solder a good hold. I actually used a switch for bending.
{{ $bending := .Resources.GetMatch "bending.jpg" }}
{{< figure src="{{ $bending.RelPermalink }}" alt="Left half with rows soldered" position="center" caption="Left side rows" >}}

You can bend the diode around one of the contacts on the switch. I used my finger
for the intial 180 degrees and some pliers to get it the next 90. Do this for
each diode.

{{ with $image := .Resources.GetMatch "placing_diodes.jpg"}}
{{< figure src="{{ .RelPermalink }}" alt="Left half with rows soldered" position="center" caption="Left side rows" >}}
{{ end }}


[1]: https://github.com/adereth/dactyl-keyboard

