# 🤖 A.R.C.I.O Project *(In Progress)*

---

[Back to Portfolio Homepage](../index.md)

---

### Project Description

---

### Details

* **Device:** ASUS i5 X555L series (2014)
* **Primary Issues:** Missing HDD, Faulty battery, No AC power adapter and general wear. An older outdated laptop in need of renewed purpose.
* **Objective:** Restore and convert notebook style laptop into a more disgusted character form and developed a "Personality" via Python code and local repositories.
* **Tools Used:** Precision screwdriver set, Driver, Impact, Sandpaper & electrical tape.

## Project Logs

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


<details markdown="1">
<summary><b></b>2026-04-17: ACT-2 MIND</summary>b></summary>

### Mind_

I have almost found every way NOT to fix this communication issue. I know its not the LCD panel or the controller board, as the LCD will light up with the controller boards "Looking for signal" message when i turn the board on... The text is in a Chinese Dialect... so I don't know exactly what it says... but i know it is working. So those two aren't the issue, nor is my HDMI cable as I have an abundance of them and have a bag for the ones that work and the ones I may use as rope... don't. ask. I also have tried DVI and that actually did work... once... then I powered off again and am back to nothing. The motherboard works... i know this... for two reasons:
1: It's showed me 3 times that it works on 2 separate monitors and the DVI cable.
2: The fan spins up and that Hitachi HDD is crackling. 

It's getting power, its thinking, its just shy or likes to watch me pull my hair out. ARCIO may already have a personality, maybe I wont have to struggle with the python coding after all. The issue IS something with the motherboard. Its not broken, I think it just cant see its ports, I have no idea why it sees monitors the first time with ease then just "forgets" it can do that, I think its freaking out because its native LVDs socket is empty. 

If it cant see its ports, it can cant get into the external HDD connected via USB which is where its OS had to be installed because it didn't have an internal HDD at the time... and if it cant see the external HDD and is riding without an OS then the drivers within the OS cant tell it "Hey! Chill, just use the HDMI/DVI/USB ports!" I'm locked in a paradox with a decapitated laptop that worked perfectly fine a few days ago before i decided to mess with it. Id scream and cry, but I'm too tired to do so.

So... something i DID figure out is during the 3 times it actually showcased the MX wallpaper on the external screens is that, The blank MX wallpaper, was not a glitch... its the Extended display screen... another very dumb moment. Typically a laptop will naturally Extend its display rather than mirroring or moving the main screen to the external monitor. So while i was seeing the Extended display on the external monitors, the actual desktop screen was on some imaginary screen that ARCIO thinks he has... with the taskbar, all the icons and the clock widget. Wish I would've thought about that earlier, i might not be in this position now.

I am rapidly running out of ideas... turning it off and on, swapping cables, asking nicely, begging, staring menacingly, trying every key command i could find that's FOR and not for ASUS, doesn't matter, screen stays blank. I even tried to give ARCIO what he seems to want, a "new" monitor hes never seen before... i have an older 15" Roku TV that I connected to the controller board via HDMI, but that resulted in nothing, didn't even handshake the first time. I also have an old Apple monitor that goes with the old mac book, didn't work and I'm out of monitors.

I am going to go put my head through a wall and sleep.

</details>


<details markdown="1">
<summary><b></b>2026-04-21: ACT-3 REALITY</summary>b></summary>

### 4AM
I have no answers and know nothing. For the past 6 days i have essentially done the same handful of things mentioned on the 17th. This makes no sense, I know. While ARCIO has been stuck in a paradox of recognition, I have accompanied him by being in a paradox of insanity. Ive been out of ideas a while, when i do get an idea I realize I've already tried it. However... for some reason that confuses me more than the issue itself and my own actions, I somehow am looking at the MX Linux desktop on the LCD screen. It worked... "it" being... ?

These entries are supposed to be accounts of my process, my triumphs, my failures, my ability to adapt and the emotions that follow. That being said... i have nothing... On the 17th I laid out my process which has stayed the same, frantic rearranging to no avail. I didn't fail but i also didn't triumph or adapt... one could say my adaptation in this trek was just showing up, but id push back on that. I suppose all that leaves is my emotions. 
Which i don't have an answer for either... I'm just confused and... perhaps lucky? 

Since, by some miracle, I'm back on the extended display screen and actually KNOW its the extended display this time, In MX I was able to right click on that "blank" desktop, navigate to display settings and actually pull the normal desktop up by setting it to "Mirror." This was very comforting to actually see a normal desktop on his screen that's connected to him via controller board. Its also leaving a terrible taste in my mouth because I don't know why its working now... every time I feel like maybe I've got this stuff down, that i understand it, something happens that my little brain doesn't get and cant figure out... that part is fine, because when i eventually do achieve a solution or gain an understanding, I can say "Ahhh, I get it now!" but with this... I don't understand anything more than I did 6 days ago. There's no genuine feeling of accomplishment.

That being said, I AM inside. So I'm taking this time to eliminate a variable, the external USB drive containing MX linux. Eventually, I will have to turn ARCIO off again, which, given that this HAS to be just some "Fluke" that I "Got in" to begin with... will result in the next powering on to lead me back to a black screen. But here's the plan to hopefully end that cycle as to not waste this random chance given. I am using MX Installer, which is copying the live OS currently running, to the "new" internal Hitachi HDD I salvaged from the mac book. Ideally, upon the next inevitable power off, ARCIO will be able to see and boot directly to the Hitachi, which will have MX linux fully installed and loaded with all the drivers needed to see the ports. Therefore he will be able to see the HDMI connected to the controller board and his native screen connected to it.


### 8AM
I got a splash of sleep at 5AM to ~now. I woke to a frozen MX installer, luckily... I didn't have to reset ARCIO, only the application, I have to leave for work at 8:30 and hope that when i return... it will have successfully copied the Live OS to the Hitachi.


### 5PM
The coping worked and is completed, the internal Hitachi drive is now loaded with an exact copy of MX Linux. No more external USB needed. However... upon the restart... I am staring at my refection in a black screen again... trying several times and am met with my own tired refection, again, and again. 
I look exactly like the screen and how I feel. DEAD.

</details>


<details markdown="1">
<summary><b></b>2026-04-22: ACT-4 POWER</summary>b></summary>

### Power_

Slept good last night, feeling less dead. After work today I thought I'd switch it up a bit, working on something tangible. I could use the fresh air. Today after work I've started on the plans for the controller board housing, plans that I've been working on in the background. Nothing fancy, but definitely an upgrade from the previous plans I had for the first controller board. The B156XTNO4.0 eDP board was smaller and taller, the plan was to use the old iPhone 8 case as the base housing for it, those plans were never finished though. The plan has shifted for the 4.2, as it's bigger and i didn't love the original idea. Being made of wood, this one should be more robust and match ARCIO better. I'm not the greatest when it comes to wood working, but I am a carpenters assistant... so I know bout wood, just a bit. And at the very least, wood is a bit more transparent than ARCIO as of right now.

Like I said, nothing fancy, using some 3/4th inch thick Pine scrap and 3/16th inch thick scrap ply wood, I'm going to relax this evening and handle some wood. The only criteria being, it must be breathable, sturdy and of course, modular. Luckily, past me has already figured all that out, all i got to do is execute the plans... crude plans, written on a beautiful pink sticky note, but plans nonetheless.

The original "hyper detailed plans" were to have a 7 inch length x 3 inch width x 2 inch height rectangular prism. However i ended up with overall dimensions of 9" x 4" x 3" 1/2. This box is two pieces, a bottom plank of pine, that's 9 x 3 1/2 inches, the bottom four edges sheered with a fine tool and a sanded nice and round, the top sanded but corners left squared as it will sit as the "floor" of the top portion.

The top portion being a rectangular "C" shape of pine. The middle of the "C" being a 7 x 3 1/2 inch plank and two 4 x 3 inch planks at either end. Sandwiched on either long side of this "C" covering will be 2 boards of ply wood one being a simple 9 x 2 inches and the back, similar, but with an extra notch carried higher to run the LVDs cables without straining them.  

This Top portion will have holes for M5 screws and be mounted on the underside of the front 2020 aluminum extrusion on ARCIOS chassis. The bottom plank will be where the actual controller board rests, sitting on standoffs made from 4 rubber end caps, snipped to be cylinders for screws to pass through into the pine. This plank will be "Bolted" onto the bottom of that top portion, the slots on either side creating a path for air to flow over and under the board.

Harder to explain than I thought, but essentially made this way for modularity and I need the controller board to have more weight to it while its sitting on my desk. The HDMI and AC charger chords have to be clamped to a camera stand in order to not flip/ pull it off the desk.

This was refreshing and a much needed change of pace. nothing quite like pine, saw dust and some gnats in your coffee mug to bring you back to baseline. Gives a guy some time to think... and while most of the day was mindlessly cutting wood and sanding... i started thinking... and I have 1 last idea for how to get that screen to stop showing me my refection.

</details>

<details markdown="1">
<summary><b></b>2026-04-23: ACT-5 TIME</summary>b></summary>

### Time_

Another cheerful day awaits beyond the curtains, i hear the faint, muffled sounds of play and general enthusiasm of the warm spring day. The approaching weekend filling the air with a promise of freedom and relaxation. Shielded from the calm, confined in 4 walls, surrounded by ghosts. 

Hum of the XPS 8910, it's powered on this time, lessons of the past linger from an experience that feels of not my own. The back plate smudged from the taps, bare feet on the cold wood floor, screwdriver in hand. Head spins with doubt, hands shake with an incompetents I cant seem to overcome. Yet I remain, back in this place, staring at a sea of green, warted with pins and diodes I still don't fully recognize. The CMOS, the key, a way to erase his memory, lobotomize him back from the void. Screw by screw, board by board, seeking a specie, a cell that powers his very baseline. Pulling this coin will reset the CMOS chip and hopefully free the project from this stalemate. The chip, it should be on the main board, ideally on the top side. It's never that simple, full removal is the only way. Main, HDD and daughter boards lay free on the paper board, inspecting the main. Its still clean from the original extraction. Nervous but automatic hands flip the board, focused eyes sweep its underside. It's belly more complicated, more intimidating than its head. No coin, nothing, it's here somewhere just not in a way id expect, the search pivots. As a whole, the CMOS hunt is the last card I know to play, within that, there's one last form it could take. Copper pins, 4 total, finding them, bridging them will reset his mind. Wandering aimlessly, the sun is down, the outside world silent, my mind convinced it no longer exists. The RAM, releasing it, flicks up violently. I'm startled but too  focused for my mind to wander. There they are, 2 sets of 2 copper pins, triangular and missable. White print on the green "JRST2201, JRST2202" I've got you. Bridged, one at a time, 30 seconds needed, 60 given. It's done, my eyes wander in a wave of calm, they land on the Ethernet port, the pins are mangled. Working with tweezers, its tedious but i managed them back in a line. They're unusable, still, but cant silently sabotage. Its a wonder they haven't already, its a wonder ARCIO still runs at all. Reassembling with care, a more experienced person would've know ahead of time, the RAM and the CMOS pins could've been accessed from the panel on the bottom of the base plastic tub. 

Mind racing... Will the fan spin or did my prodding make him reject me, forever? Will the screen show me my refection or will i finally see success?

The green bulb on the controller board sparks to life. The board resting on its smooth wooden plank made the day before, waiting, ready to be united with its pairing cover and mounted in its final home. A testament, maybe a sign that i can see the future. The fan whirls to life... Again, all i see is my tired refection in the dark, dead screen. 

Maybe there is no future to see.

</details>


<details markdown="1">
<summary><b></b>2026-04-24: ACT-6 SOUL</summary>b></summary>

### Soul_

11 days in, only discovering ways that DON'T fix the problem. Maybe that "Luck" I spoke of before was just a fluke. A fluke like the screen turning on once for no apparent reason. Maybe I am a fraud after all, riding on flukes and false luck. The audacity and gull, to think I could actually build a robot after a few weeks of a foundational course. Not even a hyper advanced robot, a cube with heart. Self deprecation and wallowing in my own pity are default setting, developed from 25 years of life, filled with failure, violence and bad choices. While those feelings of anti self love lurk, as they do with everyone... I am not that person anymore, not with this, not with ARCIO. I have one more shot in the dark idea, a simple idea, but one that might just finally work. If it doesn't, I'll think of something else.

There's no guarantees of anything, positive or negative. This is something that's been kicking me in the teeth these past days. My expectations for this last crap shoot idea have been set accordingly. My idea and why, It's simple, so simple it's dumb and that's exactly why I'm so hopeful. I'm 60% dumb, this is my element! The idea is, taking the original LVDs cable and going back to formula. Plugging it back in to the LCD and directly into the motherboard, not in defeat, but to alter the BIOS. When i originally set up the BIOS, i did so with the intent of having ARCIO's operating system running on that 500 gig external drive. I hadn't found the Hitachi in the mac book yet. Then, because of a fluke, i was able to use MX installer to make the swap, eliminating the need for the external drive. His OS is on the Hitachi connected directly to the motherboard via SATA now. At the time, I thought this would eliminate the problem as he doesn't have to go through a USB port to access his OS, which has the drivers that would allow for him to see/trust the external display connected via controller board. It makes perfect sense, but didn't work, that fluke was the last time i was able to get a handshake. But i dont think i was entirely wrong... only 40% right. Yes, due to the internal Hitachi drive being directly connected to the motherboard, it bypasses having his BIOS to have to trust the USB port and access his own OS... but the BIOS doesn't know that yet.

ARCIO's BIOS is in a paradox, it KNOWS its OS is on the external HDD but cant trust it. Because it doesn't have the drivers on the OS to tell it to, on top of that, its freaking out because it cant find its native laptop monitor. ARCIO is overwhelmed, not broken. 

I've remained sure that the LCD, Controller board and Motherboard all work from the get go, just that they couldn't communicate... I just didn't understand why. I remain hopeful that by plugging the original LCD back into the motherboard AND having the OS on the "new" internal Hitachi drive... I can access the BIOS and essentially tell it "Forget the USB HDD, boot to your own internal drive."

So I cracked open his plastic casing again, peeled off the bezel of the LCD and united them with the original LVDs cable, then put him all back together again. It was so sweet seeing him immediately light the screen up again and, he booted directly to the BIOS... hint, hint. That beautiful blue screen burning more hope into my retinas as I alter his BIOS boot order... But this doesn't mean I'm home free, now, the real test, can ARCIO's motherboard communicate to the LCD when a controller board is doing the translation now? Getting everything set back up in place, The LVDs plugged into the controller boards port, the controller board plugged into the motherboard via HDMI, all 3 getting juice from the two AC chargers... Power on.

It works! There is no way to type this that would make sense of how crazy this felt... "comforting" being the shortest and best way I can describe my feelings. And it didn't just work the first time, ARCIO can be powered on/off and he will always see his monitor. 

Tomorrow, he becomes a bot with a body.

</details>


<details markdown="1">
<summary><b></b>2026-04-25: THE GAUNTLET</summary>b></summary>

### The Gauntlet_

I woke up early today and piece by piece began to assemble him withing the frame. Throughout this "saga" I've been rearranging the rails, making small tweaks and fleshing out the details. The results aren't exactly what i expected, but close. I salvaged some old roller cart wheels from the wood shop I work at, though the wheels are too damaged to use, the mounts are solid. Replacing the worn wheels with tennis balls, ARCIO now has some pretty nifty orange shoes. I added 3/4th inch ply wood, cut to size to the inner square of the wire frame cube's floor, to add weight and create a self of sorts. Figuring out how to modularly mount both the screen and laptop base, was a challenge. 

The screen has a frame of 3 aluminum rails that protrude form the top of the base cube, the screen and plastic casing being slim enough to slide into the grove of the top rail. the two side rails that support that top one actually protrude about an inch above the screen, giving him little Batman esk "ears", an unintentional but welcomed result. The bottom of the screen sits on the top parallel rails and is held in place by two backwards L brackets. The bottom half, containing the motherboard, slides into the base aluminum cube from the side, pinned by an inset rail at the top and snugged up at the bottom with 2 of the chunky corner brackets, they can be loosened to slide on the rails and be tighten in place just like the L brackets for the screen, making them easy to remove when needed. Both secure and unwrapped. The rubber feet of the laptops plastic bottom, line up with the rails it rests against, unintentional as well, but welcomed. 

The controller board, within its wooden box, which turned out to be much larger than necessary, though it looks pretty neat mounted to the underside of the cube's front top rail. It has a little play in it, but its secure and modular, the top of the box having the button board mounted on it. It's easy to  access but is protected behind the aluminum rail its mounted under and behind. The LVDs cable runs out of the back of the bottom of the box, up into the LCD, the delicate cable hidden and protected from being snagged. The display and AC ports facing front. Their respective cables easy to access, zip tied along and in the grooves of the rails. The bottom plank of the box secured to the mounted top covering via comically large bolts that can be taken off with a 7/16ths wrench. They protrude from the bottom of the box as a whole about an inch... Its mostly hidden, though I do think it adds to the overall jank when noticed. When the bolts are removed, that bottom plank that the controller bored is screwed into to can be dropped out and removed entirely. The only draw back is... the bolts, again, are ridiculous and very long, so it's a process.

Overall, I'm stoked. It's not lost on me that in the grand scheme of things... I haven't done anything remarkable. Despite that, for the first time in a long time, I'm proud of what I've created and what I've been able to endured to make it happen. I've learned a ton throughout this initial build, though don't get me wrong... I'm still WAY out of my depth here, this has shown me especially, how much more there is to learn. A humbling journey to say the least. Proud to say I've taken the first few steps into this chaotic world of information technology and towards the dream of a much younger, insecure and lost version of myself. This ones for him. We are doing it buddy, one panic attack at a time.

I set out to build a bot with some heart, though I have put heart and sacrificed some sanity to make this happen, its far from over. ARCIO will need hundreds of line of code to give him that "heart". However, I am going to hit pause on ARCIO's development for a few weeks, I want to tackle a "Spicy Pillow" project with an old Surface Book I've had laying around, now that I know what it is... it haunts me. More so I want to finish Ghost, shes functional and housed, but there's a few more tweaks needed. I built her to document ARCIO, and while she's helped a little bit here and there... she's more so, a tremendous pain in my ass. 

</details>
