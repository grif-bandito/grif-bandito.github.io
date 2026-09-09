# 🖥️ Archiver A-82 Media Server *(In Progress)*

---

[Back to Portfolio Homepage](../index.md)

---

### Project Description



---

### Details

* **Device:**
* **Primary Issue:** 
* **Key Solution:** 
* **Tools Used:** 

### Project Logs

---

### Volume_001_Inkling

<details markdown="1">
<summary><b></b>2026-05-13: DVD Ripping</summary>b></summary>


### Project?_

I don't have a definite plan yet as to what I'm doing for this project or even if this IS a project. More of a feeling fueled by curiosity.

From the ARCIO project, I've had some various bits of hardware laying around from the ASUS laptop, one of which is a DVD drive. It's a tad flimsy but it does work. I got a SATA to USB 3.0 cable for it
and have built up a folder of a few movies. Just some "old" DVD's I have in a box that I haven't opened since I was much younger. I downloaded MAKEmkv and just got to work ripping DVD's on my Lenovo laptop. Stacking up ~15 beloved movies from my childhood. They have a bit of grain, but man, this process awoken something in me. 


### Nostalgic Nirvana_

Though the process was a bit different from when I was younger, the feeling was very much the same. Popping the first DVD into the tray, spinning it up in MAKEmkv and watching the progress bar fill for about twenty minuets. Opening the raw .mkv file and watching a slightly grainy IRON MAN stumble around, was such a joy. That was the first DVD I ripped as it was one I had watched over and over as a kid. This felt special, not just the movie but the process as a whole, It was tactile and required patience. I haven't watched all 15 of the DVD's I've ripped, but I want to do more.


### Archiving_

Outside of very much enjoying the process of "Archiving" I've been making a slow but meaningful run at moving away from streaming services. I had wanted Ghost to be able to store and play music, similar to a google home or Alexa. I ultimately killed that idea... I just need her to stay a dedicated Documentarian for now. But I have moved away from Spottily entirely and now store music locally and have backups. I use metro on my phone and Tablet for my music, its very enjoyable and its neat to purchase and album and listen to it independently without seeing how the artists numbers.

I plan to do something similar with movies and shows, I think it would be cool and efficient if all my favorite media was in one place and no streaming service could control when or what I want to watch. It would be MY streaming service. I don't entirely know how yet but I have a few ideas and am overall just enjoying the process.


</details>



<details markdown="1">
<summary><b></b>2026-05-17: DVD Recovery</summary>b></summary>


The past few days I've embarked on a journey, a rough journey as it has largely ended in failure, but I've learned a ton and had fun.	

	
### A spark of fire_
	
Digging through the movies in the dusty box the other night I had come across 2 disks in particular that I couldn't get MAKEmkv to register, I was bummed, but its a familiar feeling. As a kid if a DVD didn't work I'd put it back in it's plastic case, morn it, then put it back on the shelf and find another DVD that did worked. I may still be a primitive ape, But now... I've entered the stone age.

	
### Monkey see, Monkey do, Monkey dd res-cue_

I downloaded ddrescue, which is a data recovery tool that functions entirely through the terminal, its pretty neat. It's automated, you can set flags to hone in what exactly you need it do and it will get to work recovering what it can, skipping and or retrying bad sectors and even reverse passes. ddrescue even keeps track of the progress so if it stops or the DVD is removed, the progress remains. It's very cool.


### Notes From My ddrescue cheat-sheet_


* **Start recovery on disc:**

		sudo ddrescue -n -b 2048 /dev/sr0 /home/username/Desktop/dvd_backup_MOVIE.iso /home/username/Desktop/dvd_backup_MOVIE.log

* **Skip ahead 100MB if stuck:*

		sudo ddrescue -n -b 2048 -i 1140MiB /dev/sr0 /home/grizzy/Desktop/dvd_backup_MOVIE.iso /home/grizzy/Desktop/dvd_backup_MOVIE.log

* **Retry after finished:**

		sudo ddrescue -d -r 3 -b 2048 /dev/sr0 /home/grizzy/Desktop/dvd_backup_MOVIE.iso /home/grizzy/Desktop/dvd_backup_MOVIE.log

* **Reverse flag if forward run doesn't make progress:**

		sudo ddrescue -R -b 2048 /dev/sr0 /home/grizzy/Desktop/dvd_backup_KFP.iso /home/grizzy/Desktop/dvd_backup_MOVIE.log



## Flag cheat sheet_

​-b 2048 (Sector Size): Non-negotiable for optical media (DVDs/CDs). Forces the software to match the physical sector size of the disc, preventing bad math under the hood and keeping the hardware aligned.


​-R (Reverse Pass - The Secret Weapon): Forces the laser to read the disc completely backward (from the outside edge inward). Essential for multi-layer DVDs where Layer 1 reads in reverse, allowing you to bypass a front-end crater and claw back data from the rear flank.

​-p (Pre-trim): Tells the laser to focus strictly on the borders where good data meets bad data, shaving the edges of a scratch sector-by-sector rather than blindly diving into the center of the crater.

​-r 3 (Retries): Tells the software how many times to aggressively re-try reading a bad sector during the scraping phase before giving up. (Best used on tough discs that aren't prone to hard-freezing).

​-E 100Ki (Max Error Rate): Acts as a safety valve. If the drive hits a massive dead zone and starts logging errors faster than 100 KB per second, ddrescue will forcefully skip the rest of that rough block to keep moving, preventing the drive firmware from locking up.

​--timeout=10s (Total Stall Timeout): Tells the entire program to exit if it goes 10 seconds without finding any new data. (Useful for automated scripts, but will stop the run if you start right on top of a massive scratch).



## ddrecue output x ffmpeg_

If all goes well by the end of this process you'll have a 100% recovered .iso saved to your computer. However... I was unsuccessful in seeing a fully recovered 100% clean .iso, but I got close.

See Log [2026-05-17_Kung_Restore_Panda] for details about the 4 recovered discs


Once I had a ~100% recovered .iso from ddrecure, I verified what i'd gotten in VLC media player. Checking for significant frame drops, artifacts and audio clarity:

* **Check in VLC:**

		vlc /path/to/MOVIE.iso

Then opening up ffmpeg, which is terminal based video trans-coder at heart. It's pretty powerful and can be used in many different ways but for my purposes, I used it to repackage or "remux" the raw MPEG2 files within the recovered .iso into an .mkv container.


* **Remuxing an .iso into an .mkv:**

		ffmpeg -err_detect ignore_err -i "dvd_backup_MOVIE.iso" -map 0 -c copy "MOVIE_movie.mkv"


Because remuxing takes all of the MPEG2 files on the DVD.iso and joins them into an single .mkv... I also used ffmpeg to trim the .mkv as to get get the movie by itself. Otherwise I'd have essentially a video of a DVD menu, then the actual movie, then credits and then various trailers and stuff tacked on at the end.

* **Trim with:**

		ffmpeg -ss 00:00:00 -to 02:00:00 -i MOVIE_movie.mkv -c copy MOVIE_movie.mkv


And now I'd have a recovered copy of an "unreadable" disk to enjoy. "easy peezy"

</details>


<details markdown="1">
<summary><b></b>2026-05-17: Kung Restore Panda</summary>b></summary>


A brief overview of my recovery attempts...

### League of Extraordinary Gentlemen_

A movie I have not seen in a very long time, but I have fond memories of watching it as a wee man. This was my most successful Recovery attempt. 99.79% recovered. ddrecuse clocked 24 hours 07 minuets and 30 seconds of total runtime... Unfortunately as of right now the .mkv file of LEG has no audio... I'm guessing that's due to something I messed up during the remuxing phase as when I checked the initial .iso in vlc it did have audio. So I believe it's still fixable. Admittedly it's not super clean, fairly rough on the overall quality, but I'm pretty happy with it.


### Kung Fu Panda (Fullscreen)_

A movie I very much enjoyed and one that I had re-watched last year for the first time since I was a kid. It was still great, It's truly a masterpiece.

This was a weekend event... I ran this KFP disk through ddrescue on Friday before I left for work and it hit a snag sometime in the day, getting stuck around 20%... thus begun me spending the entirely of my weekend battling this disk... in the end... I lost... the disk failed to fully be recovered. I only managed to recover 47.6% ...Which is rough because most of my time spend was after ddrescue failed at around 38% ...so most most of my time was fighting for that last 9%. ddrescue's up-time for this disk was 46 hours, 03 minuets and 49 seconds. That's roughly 1.03% per hour... 

Keep in mind this is a Full screen DVD copy of Kung Fu Panda... not a sleek blueray nor even an immersive widescreen experience.

I regret nothing.

</details>


<details markdown="1">
<summary><b></b>2026-05-19: Archiver A-82</summary>b></summary>

### Unstable Stack_

My current physical setup with the DVD drive is a tad unstable. But it has gotten me this far... archiving around 20 movies and surviving 70 hours of ddrescue up-time. 

Up until The Battle of Kung Fu Panda, I've had the drive sitting on the desk, but when I started clocking continuous hours of disk recovery time, I noticed the bottom of the drive was getting
extremely hot. So I "built" a simple little rig, Setting the drive on a small cardboard box with a 5V fan underneath blowing cool air through holes I cut in the bottom & top of the box. The cool air blowing directly onto the bottom of the drive has kept things cool and seems to have sped up my DVD rips. Nothings is joined, just stacked, it's functional and has solved a problem... however, if I accidentally were to topple this stack while a DVD is spinning at 5400Rpm... I may die, But even more heartbreaking, It would destroy the disk and the drive.
 

### Flaws & Fixes_

* **Eject button**
One of the most annoying things about this drive is the eject button, its essentially flush with the face plate of the drive's tray. Its hard to press and I often cant press it in deep enough to make contact with the membrane switch. A simple fix could be tacking a bit of extra plastic onto the existing, flush button.

* **Indicator light**
The light is behind the face plate, but the face plate has zero transparency or bulb to let the light through... this drive was originally in the ASUS laptop, but the laptop has no bulb of any kind to allow the light to be seen. Strange. Now that the drive is out of the laptop, the light CAN be seen from above, however it is tucked down into the plastic and difficult to see. I cannot always hear if the DVD's are spinning up as I have the fan going to reduce the drives heat as well am typically working on something else with headphones on while the drive works, it would be nice to have the light, this would give me the ability to check on the drive at a glance. A simple fix could be channeling that light with a piece of leftover plexiglass from the Surface Book Project to act as a fiber optic tube of sorts.

* **Face plate**
The face plate has an odd shape, meant to perfectly aligning with the beveled edges of a laptop, now that its free from its original enclosure, changing this may aid in getting it settled into a new chassis as well as fix the above two issues. Though changing this has stumped me a bit... I could make a new face plate out of wood, though it would be small and very difficult to work with... but the more pressing issue is attaching it. The original face plate connects in a very specific and perceive way. It's too small of an area for any sort of screws or fasteners. Glue sounded like an easy fix, but wouldn't be very durable, not to mention there isn't a ton of places that I could get a meaningful amount of glue on. the edge of the tray where the face plate attaches is "porous" and just behind that is the laser and delicate circuitry... so I'm stumped for now.

### Practical

* **Cooling**
This drive will heat up, and fast. Having it suspended along with cool air being blown directly on the bottom seems to completely fix this, it hasn't even gotten warm since I've adjusted to this setup. So withing a chassis, which will be made of wood, I'll need to do the same. 

* **Stability**
Given that the drive is currently resting on a stack, when the tray is ejected, it wants to tip and topple over. Obviously once mounted, this will be solved. Mounting a DVD drive is a tad tricky... The drive itself has a single native hole that I can pass a small screw though, its largely dependent on a bracket that is designed to sort of clamp the drive down against standoffs that were in the tub of the laptop its designed for... may have to bore out some holes for better screws and shim something up to get things even.

* **Pinching**
This is the biggest culprit when clamping a DVD drive, if the drive is pinched it will fail, scrape the disk and maybe just cease to exist. The bracket for the drive is awkward, but is designed to evenly hug the drive as to avoid this... hence why I'd like to use it... not sure how yet.

### Design Choices

* **Window**
Foolishness, but I think it would be cool. Cutting a small window into the metal of the drive so I can watch the disk spin up. As long as I don't compromise the structure of the drive, or have too much light conflicting with the laser, this should be fine. Unnecessary, but neat.


### Archiver 82_

There are complications with getting this DVD drive locked into a wooden chassis along with the 5V fan, I'm just going to keep mulling it over and see what I can come up with. I have decided a name for the drive: Archiver A-82 a reference to Archive 81, which is ironically a show that can't really be archived as no physical disks were printed... And to pay a little homage to my first project,  the donor of the drive, the ASUS laptop aka A.R.C.I.O. Also, it sounds neat.

</details>
