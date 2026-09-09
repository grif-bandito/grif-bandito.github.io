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
