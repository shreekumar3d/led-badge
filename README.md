# LED Badge Programmer

This project consists of a set of tools to program off-the-shelf LED badges based on a "HDSMART" controller. The badge I have is a low cost model with a 44x11 LED matrix, memory for 3 messages that can be shown in many ways, built-in rechargeable battery, a micro USB interface for programming the badge and charging, and comes with in-built Windows tools for programming.

Linux support for this badge ? None.  Would I boot an entire OS just to program an LED badge ? Of course not.

There are tools available for other badge make/models, but they don't work with this badge. Hence this project. I certainly plan to look at other projects, and apply their learning here.

# Goals of this project

First and foremost, I need a functional programmer that can send text and/or graphics to the LED badge.  At the very least, that means reverse engineering the custom USB protocol to a minimum level and writing simple command line tools that can speak the protocol with a desired input.

Second, the project is being developed at a hackathon (FOSSHACK 2023).  Folks involved in hardware and/or embedded etc are less in number, and if somebody does get interested (LEDs attract!) - then they should be able to jump in and use this knowledge in another project - to reverse engineer another badge, or write a better protocol perhaps or anything else.  So, doing a good job of documentation is an important thing.  Readable, reliable, simple code trumps tricks.

Third, and if I get to it come the niceties.  The badge supports various things like bitmaps, animations, and miscellaneous features. These will be implemented last.  Reverse engineering the entire protocol will take the highest priority followed by making any nice UIs to make it easy to use.

# Why this badge

LED badges are a fun way to introduce yourself and make new friends! It could up your geek factor too.

Making one for yourself can be satisfying - if you have all the skills that is. But I know from experience that you can't beat a Chinese factory in terms of costs of these things. If you're looking to give out many badges, it's likely you'll gravitate towards the cheapest option.

Thus, I purchased a few LED badges while looking for an upcoming Barcamp un-conference (aside: next edition of this kickass event will be happening on May 13th - more details [here](https://barcampbangalore.com/bcb/)). I had purchased a model during an earlier visit to China - back in the days when the mini USB connector was the most common (and cheap connector) around.  I had been using this with some python scripts under Linux, and wasn't expecting anything different this time.

But boy was I surprised. Tooling had significantly changed - actually, _improved_, I should say.  Earlier badges had custom drivers, or used USB serial drivers.  The new badge shows up as a USB mass storage device with an installer on it. Sweet!  But again I don't use Windows mostly now, so I can't use that software.  It's widely available, and I have a few of those.  Can't throw them away, got to get them to work now!

# The road not taken - open hardware approach

Any number of badges have been built - this topic has been beaten to death just at open hardware conferences.

For badges with LED arrays, IS31FL3731 is a popular choice, used in various off-the-shelf modules such as a Pimoroni Scroll pHAT HD.  I have experience directly programming this chip as well - [this hackaday post](https://hackaday.io/project/42944-kite-open-hardware-android-smartphone/log/92733-can-your-phone-double-up-as-your-name-badge) has the gory details on how I made my own phone with name badge years ago!

Making a functional 100% replacement badge requires putting together various pieces

 1. microcontroller
 2. LED array driver and LEDs
 3. battery charger circuit, rechargeable battery
 4. buttons for interaction
 5. firmware for microcontroller
 4. PCB
 5. casing

Most projects don't incorporate all these elements primarily to work around cost & logstics issues - typically the battery and/or casing isn't included, as these are difficult to do at small volumes.

Putting together an LED array isn't cheap - e.g. 44x11 LEDs is 484 LEDs - meaning 968 joints to solder.  To get this itself done economically you need a very high volume of production...

