# CosmicWatch Desktop Muon Detector
This fork is my taking the CosmicWatch Desktop Muon Detectors V2 made by MIT and then showcasing my journey on adapting it and helping people with the issues they may also discover as they try to build this from home. 

Original Sources: 
Website: http://www.cosmicwatch.lns.mit.edu/

YouTube tutorial: https://www.youtube.com/watch?v=e4IXzNiNxgU

Paper: https://arxiv.org/abs/1801.03029
![Muon Detector](Pictures/Detector.png)

With there being a greater importance in being able to do projects at home due to many lab facilities not being available, I found this journey on building a muon detector at home to be quite a valuable experience in teaching me how to handle such a complicated project without aid. Due to how valuable of an experience this was for me, I decided to write this documentation of my work on it in order to help guide others in building a muon detector too. The design that I used is MIT’s Muon Detector (https://github.com/spenceraxani/CosmicWatch-Desktop-Muon-Detector-v2), which although was an amazing design in terms of making it be possible for students to make their own detector, it had many faults which I address in this document. 

# Obtaining Materials

I first began with obtaining all of the components of the muon detector as guided by the documents on the muon detector github. Immediately I noticed the fact that the cost of many components was greater than what was listed. An example being the cost of the photomultiplier, which was greatly hiked up due to the fact that the original company that they bought the component from was bought by a bigger one. Despite the fact that the item is listed as being 48 dollars on the sheets, it is currently 91.41 dollars instead, having increased almost by 50 dollars. 
Because that company was the only readily available company that would make photomultipliers at reasonable prices, once it became acquired, the larger company was able to greatly increase the price without much competition, which is something that unfortunately happens quite often. And that is not even accounting for the cost of solder, other equipment that was needed to make the detector properly, such as suggesting a desoldering hot gun in order to polish the scintillator plastic. 

![Photonmultiplier](Pictures/Photonmultiplier.webp)

The instructions state that one should use a desoldering hot gun in order to polish the plastic scintillator, and I had wanted to buy one, but unfortunately all of the ones that were at affordable prices were of low quality. With a low quality air gun where the temperature of the hot air cannot be properly regulated, one could easily burn the scintillator, and considering the already high cost of this project, this would be quite discouraging. Due to this, I decided to buy some plastic polishing sprays and mixtures, which ended up working just as well to get rid of all of the scratches, but it did take me a bit to find the mixtures that worked best with this kind of plastic. 

Another problem with a heat gun is that it’s easy to burn the scintillator without proper experience, while polishing at least can be done slowly while checking the progress. Of course, that does not mean that the whole polishing process went without any issues. Whilst polishing one of my scintillators, it slipped out of my hands and fell off the table. Not only did I have to chip away a large portion of the corners that became cracked with the fall, but I also had to spend much more time polishing it to ensure that the scratches would not affect the detector. I encourage you to take the polishing process carefully and to not worry about the speed at which you are doing it, cause a slip could end up ruining your whole scintillator. 

Before completing the first one, I decided to start building the next one since I would want to have both either way. On my second trial, I noticed a disparity between what was being written and what was actually needed, with the components sheet asking for more components than were actually needed to build the detector. I found this out by noticing that I had parts left over even when I didn’t buy them for two detectors. At first I had thought that it was in order to ensure that fragile pieces would be bought in bulk, but it appeared to be more of a mistake that slipped through the cracks because only certain not particularly special parts such as resistors and conductors had this mistake. Keep in mind that at the end of the day, this is open documentation that was made by college students, so some things will not always be perfect. 

# Building Process

In terms of the actual soldering process, it all went pretty well as long as you are comfortable with SMD soldering. Considering that I had no previous soldering experience, I decided to first buy two practice sets in order to ensure that I would not mess up the soldering on the actual project. TH means through hole, which indicates to parts that you solder through a hole, and SMD is a surface mount device, which indicates to parts that one needs to solder directly on the surface. Starting the process with a fun and simple TH project helps introduce you to the basics whilst giving you gratification of being able to immediately use it afterward as long as you follow the basic instructions. Although the code that it executed was much simpler, the enormous amount of little parts that it required you to solder in succession, as well as learning about parts which needed to be soldered in the correct direction all ensured that I would not be making such mistakes in the final project. You are free to try the final project without such preparation of course, but I highly recommend it as some of the parts in the muon project can be quite expensive and it would be a waste to throw them away just like that because of bad soldering. 

Considering that there are several parts in the muon detector that are sensitive to static electricity, in order to ensure that I would not break those parts by conducting static electricity to them, I made a grounding lanyard (although the same exact thing can be done for a wrist band instead). I started off by wrapping the lanyard with aluminum foil, and then attached one side of an alligator clip to it. For the other side, I removed the plastic from the wire, and then wrapped it around the metal part that attaches the iron solder to the main device. Considering that the heating device then goes to the outlet, this ensures that all of the static electricity that I may gain goes out of me through the lanyard. 

Unfortunately, while wanting to test the OLED, I noticed that no matter how many different ones I used, they simply were not turning on. I decided to test out the arduino to check if there may be something wrong. I connected it to the computer through a breadboard and attempted to run a light flashing program (https://www.arduino.cc/en/Guide/NANOEvery) but could not get it to work or connect to the arduino. Thinking that the issue was due to the program, I attempted to run another one that was specifically made for the OLED which did not function either. Taking a deep dive into the program, I found out that through downloading CH340 where it was already installed on the computer, it interfered with the program. The original MIT design was before a newer Mac OS was released that had a built-in serial driver, which is why in its instructions, it says to download it whereas one should not with a version later than macOS 10.14 Mojave. In this situation, I used another computer to run the program, but it still wouldn’t work. Uncertain of what was ultimately causing the issues, I decided to look into the manufacturer to find out that the amazon version of the Arduino Nano was in fact a fake and usually would not properly work (one review being: “I have read more websites on what to do to fix this. Yes, I uploaded and installed the CH341 driver. Yes I have tried the 328p processor with the new and old bootloaders. Fact is, I can't upload a program into this Nano. Without a program, it just plain won't work and there appears to be nothing I can do about it other than throw these away and use some other kind of board. Live and learn”), which explained the issue in connecting to the arduino. The creators of this project most likely decided to go with the amazon option in order to decrease the price as on the original website, only one arduino costs 20 dollars where on amazon one could get at least 3 for that amount. 

![Breadboard1](Pictures/Breadboard1.png)
![Breadboard2](Pictures/Breadboard2.png)

Eventually I was able to fix this issue by installing the FTDIUSBSerialDextInstaller_1_4_7 driver, and finally, I was able to get the proper arduino working not only through a simple led program, but also through an oled program. Wanting to make sure that the oled would then work in the arduino itself, I went through the extremely tasking process of needing to take the already fake arduino out of the pcb, and then solder the new one in. Fair to say, make sure to check your arduino before soldering it because soldering it is an incredible pain. Finally I uploaded the code for the oled into the arduino on the pcb, and the proper screen with the muon count came up! 

# Current Status

Following that, I finished constructing the scintillator, and when testing its ability to detect muons on the oscilloscope, it functioned and detected muons at the average rate that the project said it should, which was a great success. Unfortunately, once I plugged it into the rest of the muon detector, although the OLED screen would show up counts sometimes, there would often be times where a muon would be detected on the oscilloscope, but would not show up on the OLED screen. Considering that it was the smaller signals that were not coming through, there must have been an issue with the soldering of the signal amplifying parts of the PCB. And indeed when I started checking the soldering of all of the parts, I noticed that with some of the small parts like the LT-3461 DC-BC Booster and the LT 1807 Op-Amp, the legs were not soldered well to the PCB. It is only expected considering that this was my first SMD project following the practice soldering, and I noticed that when I proceeded to make a second one, the parts were much better soldered. I am now working on fixing these mistakes and figuring out what exactly went wrong in order to be able to have the main PCB function as well, but I still can detect muons using the scintillator.  

![Muon Signal on the Oscilloscope](Pictures/oscilloscope_muon)
![Oscilloscope and Muon Detector](Pictures/oscilloscope_full)
