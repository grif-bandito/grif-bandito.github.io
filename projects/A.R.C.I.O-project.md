# 🤖 A.R.C.I.O Project *(In Progress)*

---

[Back to Portfolio Homepage](../index.md)

---

* **Device:** ASUS i5 X555L series (2014)
* **Primary Issues:** Missing HDD, Faulty battery, No AC power adapter and general wear.
* **Objective:** 
* **Tools Used:**
* 
---

### Project Logs

---

### Volume_001

<details markdown="1">
<summary><b></b>2026-04-06: Manifesto</summary>b></summary>

### Attempting the Impossible_

Today marks a possible decent into madness.

### Context_

At this time I am a little over a month into taking the Google IT Support Professional Certificate and a little less than a month into using Ubuntu as my primary OS. I'm on course 2 and have filled a notebook and a half with notes. Surely "Too many notes" is a thing, but I have never been quite as enthralled with anything quite as much as I am with this IT stuff. I've been known to be "tech savvy" but have been humbled several times just in that first course... the network section really was a challenge for me especially. The realization has hit me over and over, just how much of the tech I use daily... is so familiar yet so foreign. But I'm beginning to really understand. 2 months ago a terminal was fantasy thing only seen in movies, now I use one daily.

Bear with me here, I am 25 years old and ever since I was little I have always wanted a robot buddy. To this day, I don't know what spawned this "want" and I don't know why I have been emotional recently at the idea that I might actually be able to build one. This has been on my mind the past few days, I don't know if I'm naive, bonkers, maybe there is some wall that I'll inevitably hit or maybe its not as wild as I think... and it's a "duh, anyone could do that" type of thing... I am not a very confident person and have had a rough couple of years, trying to reset, heal and change for the better... so maybe it's just another spur of desperation... I have been trying to find purpose like a madman for a while... Music, Animation, CGI, Culinary, Video production, Carpentry, Mui Thai. I keep trying to find "My thing" but I just can't get myself to care or fall in love with these things, despite enjoying them. But I feel different about this... Maybe I have found something that I actually care about. Time will tell.

### Spark_

I have an ASUS i5 laptop that I got from a friend, who got it from a company that was going out of business, where they go it... I may never know. It's a 2014 X555L and missing an internal HDD, I had powered it on a few years back, saw what I now know is the BIOS (Basic Input/Output System) closed the lid and never really did anything with it. But I've always held onto old tech, even if it was "broken". 
I have no idea if it will power on, I have about 7 different AC Chargers... yet none of them work for the ASUS... strange, I know. A Google search and $20.32 later, the ASUS AC charger is on its way. 
Estimated delivery: April 9th.

So a bit of downtime before then... But the idea here is that the i5 will be the brain of a droid, a robot buddy, ideally one smart enough to teach me how to code, play chess and have a bit of personality to him. No... I dont know exactly how I'm going to do this, but I have a few ideas and 2 days to think of some more.

</details>


<details markdown="1">
<summary><b></b>2026-04-08: Input/Output</summary>b></summary>

### I/O_

Well, the AC charger arrived a day early and the lights are on! The ASUS booted up and unlike the sticker suggest on the bottom of the laptop, it is not running windows 8. The ASUS doesn't have a way to store an operating system to get past the BIOS, lacking that internal HDD. However, I have an external HDD (500 GB) that has no name... it just says 3.0 on the top of it and nothing else, but at least we know its fast. Typically i wouldn't want to run anything, let alone a full OS off of an external drive, but this project is about "Working with what you've got."
So, I'm going to use the the unnamed external USB 3.0 HDD as the Droids base memory storage. I've turned the HDD into a Ventoy, which just makes it a boot loader so the computer can boot into it and see the ISO (optical disc image) file for the OS installation. The OS of choice is MX Linux, Its lightweight and has a simple, sort of "older vibe" that I think matches the ASUS. This was a pretty straight forward process as i have been swapping Linux distros on my dell xps 8910 to try them out and learn the process as well as had swapped my lenovo think pad's windows 11 for Ubuntu. Operating system installation has become a pretty familiar process over the past month. The ASUS was booted up and running MX Linux in no time.


### Growth_

My 2 ideas have blossomed into a a pretty solid plan. Now... as mentioned in the Manifesto, I'm still very new to this and admittedly don't have the knowledge or experience to really build out a software or hardware system as complex as needed. The extend of my soft/hardware experience is installing OS's, Fighting Premiere pro for 8 years, and Installing RAM sticks on my Dell a few years back. Given that, I brought all my theories and ideas onto Google Gemini's desk, Gemini has validated the plan and helped me carve out the more nuanced technical details. This felt a bit strange as I tend to pride myself on "Doing things independently" and "Being self taught" though that may be the main culprit as to why my ideas have always ended up being half baked and ultimately fail. Pride swallowed and I asked for help.


### Blueprint_

A working ASUS means we have a brain, now we need a body.
I sketched out the plan and ingredients for everything I need, essentially I want to make an wire frame cube, the ASUS's bottom tub will sit inside upright, horizontally and the screen will be mounted atop the cube. Both will need to be modular, because i have a feeling it wont just be "Set it, Forget it". Not entirely sure how I'll secure them without a permanent fix, but we aren't there yet. I have a 1080p web cam with a built in ring light that sort of looks like an eyeball, I intend to mount this to the "shoulder" of the cube, this will be his eye. An external webcam will definitely be higher quality for things like Facial recognition and identifying objects, two things I want to program him to do... but again... that will be later on. Another "Dilemma" and the reason we cant have robots living with us out on the streets is... power. The idea was a cordless battery powered bot... but I don't think that's going to be sustainable and I am on a budget here. So, the droid will be wall powered for now, it will be a solid MVP and... since its a laptop, if the power does go out, he can run off of his internal battery for a bit, or at least be safely powered off after an outage. Pretty cool.

The focus now is, getting inside the laptop and checking out the motherboard... I hear the rattle of some potentially loose screws which could short or damage the motherboard. What I'm looking for in particular right now is actually in the screen portion, In order to separate the screen from the base and still have them communicate when mounted apart in the chassis, I need a specific LCD controller board which I can plug into the LCD via eDP (embedded display port) and then via HDMI or DVI connected to the motherboard. This will be the Brain and the face. So ill need a model number for the screen which should be on the back of the LCD itself. Tomorrow will be the day I get into the guts. I'm quite nervous about dealing with the motherboard and raw LCD panel, but finding that part number will unlock the next door. 

</details>


<details markdown="1">
<summary><b></b>2026-04-09: B156XTNO4.0</summary>b></summary>

### B156XTNO4.0_

If I were wearing boots, I'd be shaking in them... Though today is definitely a day where being barefoot will actually help. The plan of course is to get to the LCD panel and get that part number, to do that is going to require quite a bit more than what I'm qualified to do, which is basically nothing.

### The Bezel_

Removing the bezel was intimidating, there were only two screws holding it in place, they were hidden under two small stickers on either side of the bottom of the bezel itself, that part was straight forward. Peeling the flimsy plastic bezel off, was very concerning. It felt like it was going to snap, but eventually popped off in one piece. Looking at the raw LCD panel its, held on by 4 screws and has a cable plugged in at the bottom, this is the eDP, its pretty cool to see it in person, its replacement will be one that connects to a controller board. The native eDP, however, splits into two paths coming from where it plugs into the LCD. If looking at the ASUS head on, one part of the split goes left and wraps all around the LCD panel and leads to the top camera board. The other split goes directly down into the base of the laptop... where the motherboard it. Obviously it would... the motherboard and LCD panel have to communicate somehow... still... very nerve racking.

### First Contact_

Taking the keyboard panel off of the base got the heartbeat pumping pretty good, the sweat glands where having a hay day. It was far more secure than the bezel and popped off with quite a lot of enthusiasm, too much enthusiasm dispute my efforts of a slow, easy release. When the keyboard panel finally popped off, it yanked a cable out of its ZIF (zero insertion force) connector, i fully thought i had killed the project before it began, but was wrong. No damage was inflicted on the motherboard aside from me staring at it for a few minutes and making it uncomfortable. Seeing a naked motherboard for the first time, one that i am responsible for... was a wild moment. It's impossibly complicated, has so many fragile pins and diodes, contains so many little elements I dont understand. I don't need to yet, so I reeled myself back in. My only task in this moment is to disconnect the LCD panel from the motherboard safely. I had turned my Dell XPS 8910 around and am using the back metal plate to ground myself, probably more than needed, And yes, i am barefoot on hardwood flooring. As I've said and will continue to say, I am so far out of my depth, I want to be as safe and respectful as possible. This is the future brain of my robot buddy of course. The cable that was yanked out upon the pop of the panel, was the keyboards ribbon cable and there was one other cable that remained, the track pads ribbon cable, I grounded my self on the Dell... a few times then carefully flicked up the ZIF's hinge and set the keyboard panel aside.

### The eDP_

Disconnecting the eDP from the motherboard, is a great way to give yourself a mini heart attack, its small, covered in tape and impossible to get a good grip on. It is also very snug in its socket, its a friction fit of sorts, eventually it slid out. With the eDP disconnected from the motherboard and tucked back, as to not damage the board, I was able to unscrew the top portion of the laptop. The hinges are screwed to the bottom tub under the motherboard, dealing with all that isn't the focus right now, so I covered the now screen less motherboard back up and Set it aside. I began to unscrew the camera board at the top of the screen and fully dislodge its long cable from the plastic housing, taping it to the desk and keeping it out of the way. Finally, i could unscrew the LCD panels 4 screws and see whats on the back. The raw LCD panel is so fragile, essentially just a pane of glass. With care and a slow speed i pulled it out and set it face down on an upside down X-acto board, offering a soft foam pad for the LCD to rest on. 

A similar process to the eDP motherboard socket began again with the LCD panels eDP socket which is on the back of the panel. Its the only open slot in a plastic sheet covering of the LCD's "motherboard" that has big red letters that read "DO NOT TOUCH!" If i were to peel that covering off and touch that board, it could result in streaks on the screen, so ill take that advice. Now that the eDP is out of the way... for one I can regulate my heart rate and two... I can read the part number etched into the thin metal backing of the LCD panel... B156XTNO4.0.

LCD Controller Board eDP 30-pin - Estimated Arrival: 2026-04-13

</details>


<details markdown="1">
<summary><b></b>2026-04-10: A.R.C.I.O</summary>b></summary>

### What's to come_

I went ahead and ordered some items for the chassis, possibly premature as i currently have a "decapitated" laptop and much to do before i can seat everything into the body. I am optimistic, excited and want to stay busy. The controller board arrives on the 13th and the other items may be here a bit sooner. I have 16 2020 aluminum extrusions on the way, 8 black and 8 silver, another AC charger for the controller board and some extra M5 hardware screws and T nuts on the way... sitting under around $100 in total for the project, everything else, i hope to build myself out of wood. I think the mix of the sleek aluminium and scrap wood i have loads of, will make for a pretty unique body for the bot. Almost evrything i buy i tend to mar up a bit with in the first few hours of owning it, often why i resort to making things. When i cant make it i get something second hand. This has made me, as Niko Pueringer would say: "Embrace the jank."

I have also decided on a name for the ASUS bot... 

### A.R.C.I/O_

* **A** = Aluminum- Due to his aluminum frame

* **R** = Remote-   Due to him being entirely offline, running on his own independent python code.

* **C** = Computer- Due to, of course him being made from an ASUS laptop.

* **I/O** = Input/Output- In reference to the "Heartbeat of the machine" I am aware hes technically Just 1's and 0's but I still see him as a life, as someone, not something.

Yes, the name may be a bit "jank" in explanation, most things are... however I think it has a good sound and keeping the "A" from ASUS feels right as he was built from one. The "A" also giving him an alphabetical hierarchy as he has never anyone's first choice, the company my friend got him from as they were going out of business and ridding themselves of the spare parts, my friend giving him to me as he didn't need him, and me powering him on once years ago then shutting the lid. ARCIO he shall be...

</details>


<details markdown="1">
<summary><b></b>2026-04-10: Extraction</summary>b></summary>

### Foreplay_ 

The Dell's metallic grounded backing, the electronic socket set, cardboard and some plastic tins. Myself, clean and prepped to use these tools to negotiate with my first motherboard, yesterday was an exchange of pleasantries, today was intercourse. 

### Intentions_

I plan to keep the bottom tub that houses the motherboard as its already designed to keep it, secure, and protected. However, I want to modify it slightly to help the board breathe. I want to drill some holes in the bottom of the tub where the fan will be able to intake fresh air. The top keyboard layer, will be kept as well... I want to remove the keyboard and track pad themselves and leave those areas open, potentially covering them back up with a mesh or modified plexiglass, ideally this will create a wind tunnel and overall more open space for the CPU and GPU to directly dissipate heat. These too pieces that sandwich the motherboard will be standing vertically, resting on the long edge, opposite of the hinges when in the chassis. In order to do this, i must fully remove the motherboard and company.

### Time To Tango_

Upon taking that plastic keyboard covering off a second time, we are missing a few things... for one, of course as mentioned previously, no HDD. We are also missing a battery entirely, one can always be bought in the future, no big deal. this is actually more helpful than hindering right now. A battery-less motherboard in which i have already held it's power button down upon the unplugging of the AC charger, is void of all juice, making it far less likely to short. No battery in attendance also means, no battery to remove. There are also a few screws missing and wandering. The motherboard is secure but I'm sure annoyed at its current state of disarray. Certainly my inexperienced hands and nervous eyes do not easy the board. I move slow, no tools in hand, hands in lap, observing, counting, planning my first move.
"How many screws?... Eight... Are you sure?... ...Ten... Can you get to them all?... yes."
"How many Components?... Four. What are they?... Main motherboard, HDD board, Daughter board, CD player and the antenna wire."
Screwdriver in hand, one screw at a time, i begin. The antenna wire is taped off to the side on the cardboard I have laying over the desk's top. It was woven in the LCD's plastic housing originally. After a tap on the grounded metal plate of the Dell, The CD player was removed first, it wont be used for ARCIO but my mind wandered a bit of how I could use it later. Another tap, Then the daughter board, then the HDD board which rests over the main board seated on pins, The HDD to SATA ribbon cable set aside with the two smaller boards. My palms sweaty, another tap, Carefully I lift the main motherboard setting it gently aside... staring at the empty base tub, only adorned the metal hinges. 

I cleaned up a bit, blowing the dust off and brushing the boards with a soft fine, paintbrush. Tucking the boards in with more cardboard, they'll remain naked but covered on my desk as i prepare the the plastic tub to be more breathable before their return.

### Fabrication_

It was nice to step outside and into the shed, plastic tub in hand, free from the fragile components of the motherboard. While now I'm surrounded by the typical grime of a shed, away from the delicate green of the PCB and the clean environment require to maintain its health, i still need to be careful. Slow and steady as to not crack the plastic shell while i drill out the venting holes. I marked out a grid for the holes, i already had marked down the area where the fan sits before the extraction to ensure my modification would be useful. 22 holes in total, 10 larger ~3 mm and 12 smaller ~1 mm in diameter, Staggering them into an appealing pattern. This ended up being a bit more of a mess than a clean cohesive layout. The drill bit was wandering on the plastic, despite using some pressure and starting small, boring the holes to be larger... But i did my best to make it somewhat result in a "nice" pattern of sorts. The only real stress here after avoiding fractures was the rough edges, large bits of plastic plagued the holes. It took some time, but at the cost of scrapping up the surrounding area of the plastic on both sides of the tub, the sandpaper did its job. I cleaned the area and the tub as a hole with alcohol wipes and repeated the process a few times, Sand, wipe, repeat. The keyboard covering had to be gutted as well as its components aren't needed, removing the keyboard and track pad until i was left with a squarish hole where the track pad used to be and a grid of cap key sized holes. The keyboard covering and its components were held together with plastic rivets that left a mess of uneven plastic... so a familiar process ensued, Sand, wipe, repeat.

I ended up rinsing both out with water and a bit of soap, just to make sure they were clean and removed the Intel sticker on the keyboard covering. The controller board wont arrive until the 13th, so I can set these aside and let them dry.

</details>


<details markdown="1">
<summary><b></b>2026-04-11: Lucky Fool</summary>b></summary>

### 10pm

Yet again I'm brewing coffee. I am showered and back to being barefooted on the hardwood floor beneath me, the Dell faced away, ready to ground me. After giving the now crudely vented plastic tub housing those last few look overs, it was time to start putting everything back into place. I have taken it out, I should be able to put it back in. Though it has no screen, I'll be able to power it on tonight and if that fan spins... I'll know I'm still in the game. Technically I could leave it for now as i dont have a controller board or frame yet to further the project, but its far too unsettling to have a naked motherboard laying on the desk, protected only by cardboard. Just three pieces to worry about, not including the screws and HDD to SATA ribbon cable, The main motherboard, HDD board and the daughter board. The process of re assembly was swifter than the extraction, however, i didn't feel any less nervous. Surely i was calloused a bit, having removed it before... but the heartbeat and sweat glands acted as if this was the first time all over again getting intimate with the delicate PCB. Tap the Dell, breathe, set in place, deja vu set in.

I finally get the pieces in place, screwed tight, but not too tight, sitting back with a sigh of relief... my bare feet feel the prongs of a plug on the floor... i peak under the desk and follow the chord to the back of the dell... it wasn't plugged in. I panicked and plugged it in as if that would right the wrong, was done was done, i had already completed the reassembly, manipulated the PCB with unclean hands. 30 minuets ensued of uninterrupted silence, damp eyes and just staring at the boards, they're clean, secure in place... they appear fine... but i know a truth. I most likely shorted them out in the reassembly process with my un-grounded hands. It felt so unfair, i felt so incompetent. Toying with the idea of just going to bed and pretending none of this happened, but i had to know. I was certain I just lost. The feeling of "It's over before its begun" infected my thoughts for the second time, it seemed like I had given ARCIO his name just so it would hurt more when id inevitably fail him, a type of self destruction I've learned to perfect.

I hit the power button and the fan spun up. ARCIO is alive. Relief washed over me but that feeling will never leave me. I messed up and got lucky. The only reason I didn't short the boards out is the fact that there was no battery to connect... the only danger of a short came when i plugged in the AC charger. That's just a theory, but i think its pretty sound. This still gives me comfort in a way, these bare boards are less fragile than i thought, battery in play or not. ARCIO survived this act of stupidity out of pure chance and maybe a splash of grace from the robot gods... I need to be more careful. 

</details>


<details markdown="1">
<summary><b></b>2026-04-12: Bones</summary>b></summary>

### Bones_

The 2020 aluminum extrusions and hardware arrived today. The 2.5 x 5.5 mm AC charger for the controller board arrived today too, but I've set that aside for tomorrow. The 2020 rails are 300 mm in length and 20mm thick, this was concerning to me yesterday before i got them. 20mm seemed very small and was concerned they'd be flimsy. Holding them now, they are not, these are sturdy and definitely going to make for a good frame, these rails, the wood, and hardware should amount to a pretty weighty chassis, estimating ~15-20 lbs. This is good as id rather ARCIO have a robust build.

Unboxing the rails was a surprisingly messy process, each of the 16 rails is in its own plastic sheath and has a bonus of tons of little metal shavings... that get everywhere. Wiping each of them down, seeing them all cleaned up... they're very nice, both the black and silver have some sort of anodized coating. lets see how long before i scuff them up.

Some deep insight via "research" convinced me that these 2020 rails were essentially "big boy Lego" and I was pretty stoked to build some easy, modular, good ole Lego. It has been a while. Though this is only half true, while these are modular, they are a pinch of a pain and a bit confusing to my monkey brain. My struggle may have been to the fault of my own as I've interlocked them in a pinwheel assembly of sorts. Seemed clever, as it should be more structurally sound... but will make it more tedious later if I change my mind, which I do often. In the first attempt I actually used the smaller, inline rail, L brackets. Which made for a very rickety and jank square... it took me longer than I'd honestly like to admit to figure these guys out. But after some head scratching and a few deep sighs I got things rolling. Attempt 3 as we wont talk about attempt 2... I made two square faces in that pinwheel layout then interlocked them with 4 cross braces, each corner adorned with the chunkier corner brackets. This worked well, seems sturdy and was pretty fun despite the shockingly steep (for me) learning curve there at the start. With this wire frame cube using 12 of the rails, I have 4 left over to figure out how I'm going to mount the screen... not entirely sure how I'm mounting the motherboard within the cube either... but it does fit.

</details>


<details markdown="1">
<summary><b></b>2026-04-13: Monday The 13th</summary>b></summary>

### Woke up stoked, ended up joked.

The controller board arrived early this morning, finally getting to unbox it with the LCD panel close by was exciting after waiting all day, knowing it was at home. Pulling the controller and button boards from the crisp anti static bag felt real, like I was some professional. Bringing the 30 pin eDP to the female port on the back of the LCD, only to realize something is wrong... this new cable is smaller than the port it's supposed to be destined for... I messed up. It took some mental calibrating, frustration management, navigating confusion and frantic research to fully understand what I had done to put myself in this place of incompatibility. For the time period of this ASUS laptop, the 30 pin eDP WAS the typically cable used... for a typical laptop. However my particular ASUS was just outside of typical. For laptops with touchscreens and/or higher refresh rates, a different type of embedded display port was used... LVDs (Low-Voltage differential signaling). No, my ASUS X555L doesn't posses a touch screen... but it dose require an LVDs due to it having a higher refresh rate... I ordered the completely wrong controller board and there's no way to make it compatible. It took even longer to figure out why the part number i pulled directly from the back of the LCD panel was wrong, how could it be? it was literally etched into the thin metal! Turns out... that's not the place to look for specifics... the part numbers etch on the actual components are more general. This makes sense as it would be a hassle and a waste to make every variant its own special etch metal back plate. The place to look is the white sticker... and in small print I saw the correct part number... B156XTNO4.2... I was off by .2 The general part number being B156XTNO4.0.

I eventually found a controller board for B156XTNO4.2 on eBay... it will be here April 15th.

</details>

---

### Volume_002

<details markdown="1">
<summary><b></b>2026-04-15: ACT-1 SPACE</summary>b></summary>

### Space_

It's been a touch "slow" lately, having to wait on the controller board after the realization on the 13th. Not to mention the scare that happened on the 11th, getting lucky. My mind has wandered a bit, looking for a contingency plan in case my luck runs out. I'm staying busy in my off hours, sleeping less, contiguously rearranging the 2020 rails and looking forward of how i may ground the cage as a whole, getting closer to something viable. Thinking through how i can mount the controller board once it arrives as it will need housing, assuming i got it right this time as a 40 pin LVDs. As far as contingency, i spent a some time poking and prodding and ol mac book pro I've held onto... trying to get it too boot up, with no luck. Its old enough to have an intel chip inside so if i am able to, it could be a replacement brain for ARCIO if things go sideways. I set it aside for now, but after opening it up i discovered its internal drive is a 300GB Hitachi, with the exact SATA port to match the ASUS... so at the very least I've solved one problem... through sheer chance again. It fits perfectly inside the ASUS. The documentarian, Ghost is also keeping me busy as she still needs work, though shes somewhat helping keep the timeline in check, lacking reliability less and less. More so now its figuring out her Python code, ill eventually need a similar yet more complex script for ARCIO. 

The process of obtaining the Python code... a point of conflict for me. I've watched and followed along with some videos of a YouTube channel called "Programming with Mosh" trying to understand how to write and understand Python. Working in Visual Studio Code, writing nonsense i still dont understand. Google Gemini ultimately having to be the producer of 99% of my code... this has troubled me deeply. I feel like a fraud, trying to convince myself, Gemini is just a tool...  When building a deck, few if any, would turn each screw into place with a screwdriver in hand... that would be primitive and slow. The obvious being to use an impact driver, this would improve efficiency tenfold. Clueless as to if that analogy is accurate or me just trying to cope. 

The new controller board has arrived and the sun is going down. I have the motherboard in its hollowed out plastic base, the LCD panel laying on the upside down X-acto board and the controller board resting atop an old iPhone 8 case, the switches for it resting on the box they came in. My revelation on the 13th paid off, the LVD's seats into the LCD panel, perfectly... spent a good while unsure if it was in correctly... I'm even more untrusting of myself today given the recent thoughts and mishaps. I hit the power on both... the green light on the controller board sparked to life... the fan on ARCIO whirred up... The LCD blinked to life. I was looking at the default wallpaper of  MX linux OS i had set up days ago... but something was off, no clock, no task bar... so i reset. powering both off and back on... The Greed LED, Fan whirring... the LCD remained blank this time. 

I had been here before the day prior... I had connected the motherboard to my Crua monitor just to see. This very same default MX wallpaper, void of the clock in the top right corner and taskbar at the bottom. I did the same thing twice, thinking it was glitched... Both times resulting in the same... a blank screen after that initial boot.

 I took the HDMI in and out, pulled the AC charger on both the controller and mother board. Holding the power button down for 10, 30, 60 seconds... nothing. Even swapping back to the Crua... nothing i did resulted in seeing that screen ever again. I know it works... the fan is spinning and its shown me the MX wallpaper twice now... but only on the first boot for both the Crua and LCD screens. Its like it sees the external monitor only if its the first ever time its plugged into it, does it expect me to buy it a new monitor every time i want to turn it on?

I'm out of ideas and going to bed.

</details>
