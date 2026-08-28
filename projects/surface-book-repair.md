# 🛠️ Surface Book Hardware Repair & Repurposing

[Back to Portfolio Homepage](../index.md)

* **Device:** Microsoft Surface Book 1
* **Primary Issue:** Severe Li-ion battery swelling expanding behind and bulging out the display panel.
* **Key Solution:** Safe battery discharge & extraction, custom plexiglass cover installation, modified airflow cooling, external display routing.
* **Tools Used:** Precision driver set, plastic spudgers, Deck of cards/debit cards, isopropyl alcohol, rubber straw, 5v fan.

### Project Logs

<details markdown="1">
<summary><b></b>2026-04-24: Introduction</summary>b></summary>

### Tempting Fate_

Several years ago I put my surface book 1 into a backpack along side an old Mac book pro, its the retirement backpack that I keep in a cool (temp) closet as both don't work. I attempted to juice up the mac book a week or so ago, no luck, i set it aside. Working on the A.R.C.I/O and Ghost projects was more than enough to keep me busy... but i have some downtime... Ghost is functional but wacky and A.R.C.I.O is built but needs to be programmed. I've done a lot of hardware integration lately and wanted one more fix before I clean up, reset and sit down to code. What spawned the surface book's retirement was that the screen was bulged out and was getting super hot upon being used, eventually it cracked a bit flickered off. Now... keep in mind this was a few years ago when i thought computers were magic, because the screen was bulged, i thought the screen was the issue... for for a while after the screen flicked off and on a bit... all that changed was my dual monitor set up went down to a single monitor setup. I'm unsure how long i used the surface book after the screen was stuttering and bulging. But i did... i just went on using an external monitor like everything was peachy. Knowing what i know now... its truly a wonder I'm not dead.
	
### Spicy Pillow + Magnesium_ 

Spicy pillow, a term that makes any sensible person clench. The screen was not the issue of course, the real culprit here was the lithium ion battery inflating due to a build up of gas via electrolyte decomposition. The electrolytes being the gel, liquid or solid "go-between" for the positive (cathode) and negative (anode) terminals withing the battery, allowing ions to travel between and present a charge. A spicy pillow such as the one I've been unknowingly living with for years, is dangerous and upon the irritated chemicals coming into contact with air... it ignites in a thermal runaway... this is bad enough, but in the case of the surface book... it gets worse.
The surface books body or chassis is a magnesium alloy... containing Aluminum, Zinc, silicon and yes... ~90% magnesium... which when ignited is virtually impossible to put out. The saving grace is that the chassis is for one an alloy but also, magnesium is much harder to ignite as a solid unit. For the alloy chassis to ignite it would need to be exposed to a temperature of 1,202 degrees, Fahrenheit, its melting point. A spicy pillow upon igniting can reach temperatures of over 1,000 degrees, Fahrenheit in seconds... not the most comforting ranges. Now... the chances are low of a magnesium fire taking place in the surface books chassis... but they are not zero. It entirely depends on on the batteries heat and how concentrated that heat is... magnesium is a great conductor, let's just hope my spicy pillow isn't in a "scorched earth" mood. Now, why the battery was decomposing could be from a age, a chemical reaction, or the fact that i had it plugged in at 100% juice for its entire life... who knows, an even bigger mystery is why it decided not to erupt already.

### Theories_

The most likely cause of the inflation was heat, as the surface book's screen is detachable and can be used without the keyboard base. Meaning that the CPU and GPU are housed in that top tablet portion, behind a 3000 x 2000, 4k display... all three of these generate a massive amount of heat. The edges of the screen/tablet does have a vent wrapping all the way around its edges and should have a fan inside... but clearly that was not enough. My best guess is to why the lith-ion battery didn't go "supernova" was do to the screen bulge, which if looking at the screen of the laptop, on the right side, had bulged + gotten hot enough to melt the adhesive creating a gap that i could fit two fingers in at the time... don't ask me how I know. This would allow some airflow to keep this a bit cooler than if the screen hadn't broken the adhesive and remained sealed. Lucky me.

### Years later_

Upon pulling the surface book out of the retirement backpack... I've noticed that the screen is, of course, still cracked slightly. More interestingly, its no longer bulged... which is good and bad... good because its not currently under pressure and bad because its in "sneaky mode" and doesn't look like a threat... but it very much is... it's just dormant and but the chemicals remain volatile. Pick your poison, I'd rather not battle an invisible threat... but here we are.

### The plan_

I am going to attempt to salvage the screen, get to the battery and ideally remove it without dying... maybe I'm asking too much. From what I've gathered, Surface books are notorious for the the adhesive that holds the screen in place. If I were to have taken this to a repair shop back in the day, they would have most likely refused to help, even Microsoft didn't want to mess with it. Microsoft would simply take the damaged device, send it to a "specialized" facility and potentially salvage what they could, or maybe just chuck it into the sun... i don't know. The surface book is a robust, beautiful laptop and the screen is gorgeous, not to mention the detachable element and the mechanism that makes it possible, its a feat of engineering and a lovely design. It's funny that even its creators reject it, Like Frankenstein rejecting his greatest Creation. A beautiful laptop, yes, but it was designed to fail, made to be disposed. This is common today and something that bothers me to my core. I'm going to try and save this machine and the screen that dooms it... though the typical way these are fixed is via breaking the screen and am prepared to do just that. I'm aware that my chances of saving the screen and safely removing the battery are low given my experience... I figure if I'm careful enough and still have some luck up my sleeve, i can beat the odds, I gave myself an 8% chance of success, Google Gemini gave me 15%.

</details>


<details markdown="1">
<summary><b></b>2026-04-24: Get In, Get Out</summary>b></summary>

### Get In,

In order to bump the odds up just a hair more, I am going to take what I've learned with the A.R.C.I/O (RCO for short) project and apply it here. I need to make sure that the UEFI (unified extensible firmware interface) settings are set up correctly so that i wont be locked out once the screen is removed. When working on RCO I didn't set up his BIOS (Older, simpler version of UEFI) correctly... resulting in me having to plug his LCD's LVDs cable directly back into his motherboard so i could get back into the BIOS and set it up to work with the controller board. There is no controller board in the Surface books case, but if the UEFI setting aren't set up right before i pull the screen off, which will most likely break... game over, I lose. So i need to test fate, once more, before I test it a 3rd time. I have a list of settings i need to toggle and am going to boot into the surface books UEFI. I have a spare 5v USB fan that ill have on full blast against the back of the surface book where i think the battery is and am going to ideally do this as fast as possible and hope i don't wake the baby.

### Settings_

* **Secure Boot:**
Disabling this will void the typical handshake needed from Microsoft while trying to run an alternate OS. Windows 10 is obsolete and intend to switch to a Linux based OS anyways.

* **Boot Order:**
A list of boot devices that the laptop prioritizes, by moving USB devices to the top it will force the computer to see and boot into the USB drive ill plug in later to install the Linux OS.

* **Detach Logic:** 
Ensure the Surface book doesn't panic if they screen is missing or detached. I dont plan on detaching the scree from the base, just to be safe.

* **Bitlocker:**
I wanted this out of the way as its a pain and I dont have my key. Not in the UEFI, in Control panel > System and security > Bitlocker Drive Encryption. This was a bit worrisome as there is no progress bar or load time, i hit "disable" and was brought to a screen that read "Decryption in progress" there was no definite "okay, you're all set!" I waited a few minutes while the screen got hotter. I'd assume it fully disables after a reset though.

* **Trusted Platform Module (TPM):** 
A quick check, the TPM is a chip on the motherboard that, upon noticing any tampering with the hardware will activate the Bitlocker. This doesn't really matter with bitlocker being disable, TPM is essentially a gun with no ammo. Disabled it anyways.

### Get Out
This was a nerve racking run, the screen was getting warm, but, was a success!
Though truly i wont know if this was a success until the day comes, but at least we have gotten a few hurdles out of the way.


### Suction Cup Logic_

Not 100% sure if this even makes sense, but it's an attempt. It's late and I'm going to bed. But I have 12 large suction cups ~3 1/4 inches in diameter. They're from a Kickboxing bag that has a weighted base. 5 of those suction cups will fit on the surface book's screen, 4 at the corners and one in the center. Tilting the screen forward and laying a fold able X-acto knife pad with the soft foam bottom facing up, laying over the keyboard and hinged leaned against the surface book screen, creates a triangular prism of sorts. Possibly, the 5 suction cup's weight and the tilt of the screen will have gravity do some work in pulling the screen off, hopefully falling safely onto the mat. If this works, great! If not, hopefully it does something to help release the screen as tomorrow I will be taking a hairdryer to the edges and attempting to release the adhesive and ideally not excite the battery. 

</details>


<details markdown="1">
<summary><b></b>2026-04-25: Faceless</summary>b></summary>

### Thermal De-bond_

Upon waking up and checking the suction cups, the only thing that happened was one of them fell off. While the screen didn't magically get removed via Suction + Gravity... technically, there's no tangible evidence to suggest that it didn't help a little bit. It cost nothing and was working while i slept, ill take it as it is, worth a shot and couldn't have hurt... unless the act of pressing the suction cups onto the screen actually mushed the screen against the adhesive more so... possible. Either way the screen is still locked in place and i have to resort to adhesive's foe, heat. Using a hairdryer with a flat, wide nozzle attachment i applied heat to the edges of the screen. Using several rows of tape directly on the screen with a cardboard piece taped over top and centered. The cardboard will keep the heat off of the internals and allow me to focus the heat more so on the edges. The tape underneath will keep the screen from shattering everywhere in case it does end up breaking, the objective is to avoid that and salvage the screen.

### Faceless Reality_

Upon applying heat and trying to gently pry the edges for ~hour... I have gotten no where. The screen hasn't released nor has it cracked anymore than it was already. I was being gentle, trying to salvage the screen. If I'm too rough, the fractures that the battery made in the screen long ago will grow. Worse case, they could puncture or tear the battery. Alternatively, If i continue to be gentle and apply more and more heat, the adhesive may release, but the fracture points are not going to come off easily and most likely still shatter as they are small sections held on by adhesive with no structural integrity from the rest of the screen pane. On top of that, the more heat i apply, the closer i get to exciting the battery and starting a magnesium fire.
My risk assessment is telling me that the screen needs to be sacrificed. We planned for this... the UEFI setting and bitlocker. I knew going into this that the overall chance of success was low and that salvaging the screen was near impossible. I do think that if the screen wasn't already fractured, i could have MAYBE gotten it off in one piece, though it may have taken a while.

### Face To Face_

Took a bit of time, but i was able to peel the screen off in mostly one piece, the adhesive bound edges would either shatter or remain stuck to the magnesium chassis. The tape and Cardboard did a very good job of giving the screen more structure. 

There it is... the dormant spicy pillow... its different than I expected, it doesn't have a scary face or demonic horns. It's actually just 1 of 2 cells. Turns out the surface book's tablet portion's battery is two separate but joined cells that lay flat against the magnesium chassis. With a view from head on, the batteries live in the upper center of the frame, behind the motherboard but remain visible. The left cell is smooth and healthy. The right cell is slightly wrinkled from the expansion years ago, eventually it settled back down to twin it's sister cell, but the scars remain. Fear comes from the unknown, and seeing the cell now, face to face, it unassuming. While I may be out of my depth, I'm not a fool, I know it's just as, if not more dangerous now than ever. I am nervous, my shoulders are tense and will remain tense as long as we are in the same confined space together. I am afraid, but not because I don't understand it, I know the "Why"... I'm afraid because I don't know the "If or When."

</details>


<details markdown="1">
<summary><b></b>2026-04-25: The Siege</summary>b></summary>

### The Siege_

Face to face with the disfigured cell, yes, but still a far cry from being able to begin the removal. 
Looking at the internals, The motherboard is actually upside down, it would be facing away from the screen and looking at the inside back wall of the chassis, pretty cool and I'm sure it was partly designed this way to get around the fact that the screen "has" to be broken in order to get inside. The motherboard being upside down would protect it from the small, inevitable glass shards. Maybe it's not as "designed to fail" as I previously thought. 

I have worked on one motherboard before this, the ASUS being my first. My concerns with the ASUS however, was due to it being a totally new thing for me. I was so worried I'd short it out or break something. Motherboards are less scary now as I know they're more durable than previously thought, so long as I'm respectful. The surface book is... a bit different... it's upside down, which is good, its protected more. However it's also... upside down... which is new and unexpected. Not to mention the sleeping cell. Suffice it to say, the nerves were back.

### Clean Up_

After discarding the screen, I flipped the surface book so that the tablet portion was face up on the desk, with the base standing vertically. Giving me easy access to the now naked internals. Using the clear packing tape i dabbed around the inside of the chassis trying to clean up the remaining glass bits. While the screen removal was a pretty clean break, there was still a bunch of tiny glass bits scattered around. I then took some time to scrape the leftover adhesive and glass that was still stuck on the top edge of the frame. This way I wasn't cutting up my arms when I go for the battery removal. Placing a small piece of cardboard vertically as a barrier to prevent glass from flying into the left cells "mug", I used a small flat head screwdriver and scraped away... for a good long while. I placed a clamp on the desk to give me some leverage and stop the laptop from sliding all over.
 
In the Faceless log I mentioned, had the screen not already been cracked from the cell's pressure, I may have been able to get it off in one piece, given enough time. After scraping the remaining adhesive and glass off that top edge... I'm not so sure I share the same sentiment with yesterday's me... this stuff is SUPER strong and I found myself marring up the magnesium chassis more often than not. I still have two sides to go...

### It's A Process_

The top edge was clean and safe... Time to start hunting down the illusive screws... there were so many and they are very small. The motherboard, which is somewhat an asymmetrical "H" shape, with one side being much wider and the other skinnier, is all one piece (No separate HDD board or daughter board.) Here's the order of operations for getting to the battery... which is under, said motherboard.
Removing the screws that are visible across the motherboard, as well as the fan, Then the plastic bar at the top that covers the cameras as well as the foam under it on the motherboards back has to be peeled off a bit to get to the rest of the screws for the motherboard. Both antennas on either side need to be unscrewed as well. The headphone jack port that shares a screw with that plastic bar can be pulled out of its chassis hole. NOW the board can hinge up a bit, but cant come off unless the the locking mechanisms are unscrewed from the frame or unplugged from the motherboard along with the inter connector cable that allows the tablet and base of the surface book to share power and data.

I opted to not remove or unplug the locking mechanisms nor the inter connector cable. The fact that both lockers and the cable are all connected to the main board via wire/cables allowed for some play in hinging the motherboard up and supporting it with cardboard rather than a full removal. Eventually I upgraded the cardboard supports, that were just two small rolled up pieces of cardboard held together by electrical tape and a plastic Cabala's ear plug container taped to the frame. Upgrading to much more stable plastic container for M5 screws, a small 1/8th inch piece of wood and a random plastic spacer, stacked on top of one another held together by more electrical tape. I wasn't going to mess with what I didn't have to and this seemed the path of least resistance, offering enough room to get my paws on the golden goose...

</details>


<details markdown="1">
<summary><b></b>2026-04-26: The Tortoise</summary>b></summary>

### Fallout_

Last night... I hit a stalemate. Finally getting to the battery, to a position where i could rid myself of it, its been staring me down for hours as I've jumped through every hurtle just to be in it's presence. A stack of playing cards, isopropyl alcohol and a straw, I had the tools to defeat it... but lacked the patience and confidence to preform. Applying the alcohol and slicing the cards into every gap I could manage, resulted in nothing but the cells mocking me. I'm held back by how careful i must be to not provoke them, and limited by my own psychological unease. This was another moment of realization of just how far I've come just to be here, yet how out of my depth I remain. Coming up on two months off learning about this world and less time than that of actually being able to participate. Leaving the battery in a shallow pool of alcohol and victory, while I retreaded to bed.

### The Tortoise_

It's 10 AM the next morning but the same day of course. I managed 5 hours of sleep, rolled out of bed, slight nausea lingers. The room still smelling strongly of isopropyl alcohol and the 5 AM defeat. A deck of 32 playing cards, and three straws lay on the desk. A wide plastic and blue rubber straw being the faulty tools, the metal straw already discovered to work the best from the previous attempt. The adhesive seemingly unfazed. The coffee offsetting the alcohol smell and fighting the nausea, i dilute the scents back in the alcohol favor as i start again on the removal. A shell of my earlier morning self, I'm calm and steady, applying generous amounts of the de-bonding isopropyl, sliding more of the cards into place, folding them over and stacking them for lift. Soon i upgrade to an old Acorns investment card, the only other card i have is an old Fifth third debit card but its chewed up from trying to pry the screen off which feels like ages ago, it cant be used, it would tear the cells. The Acorns card is thick and sturdy, doesn't absorb the alcohol like the playing cards so remains authoritative. I give it assistance with easy force and a slicing motion as well as company by using the empty plastic holder for Post-it tabs, creating a wedge that applies pressure more directly. A slow start, using the metal straw to apply the alcohol, wedging the card and plastic in place, stepping away for 15 minuets and returning to repeat... over and over again. Instead of alternating between the cells i focused on the right, first. Getting it lifted by a few degree's, then 30... 45... 60... then it was out. Same process with the healthy sister cell and soon enough, the cells were free along with the battery connector board. All in tact, all soaked in a pungent smell of defeat.

</details>



<details markdown="1">
<summary><b></b>2026-04-27: 70% Downtime</summary>b></summary>

### 70% Downtime_

A small but prominent detail i left out before hand is that the isopropyl alcohol used, was actually 70%. Meaning 30% is water, this... I'm sure is bad taste. Its just what I had and should be fine, to be sure, I'm allowing for a full day of drying and evaporation. The USB fan has been on high, blowing directly over the dampened chassis throughout the process and still is, night and day helping out. Taking a dry microfiber cloth I've wiped and dabbed all around the chassis to ensure no water is lurking in the magnesium. Using a flash light i kept seeing little glints of glass and shadows of debris... it will take a long while to collect every piece. This dose prevent me from furthering at a quicker pace as otherwise i could boot up and see if the surface book still works. This day of downtime isn't void of work of course, I still need to scrape out the reaming adhesive and glass on either side, double, triple check that no glass is in the chassis and then screw everything back down into place. Waiting on "parts" is also a factor, yesterday i placed an order for 5 clear sheets of 1mm thick, 8x10 inch plexiglass, clear super glue, 4 20mm clamps and a rainbow of electrical tape. I plan to cover some of the marred up magnesium on the edges where the screen was cemented on and the area where the cells/connector board were, with electrical tape, so i cant screw everything back down yet anyway. The plexiglass, once arrived, will need to be cut, joined and rounded at the edges to cover the internals. The clamps will fasten the plexiglass to the frame securely, while not being permanent.  

### The Debate_

Id like to think that luck resets upon each new project, or at the very least randomizes. For this surface book repair, I'm certain I don't have a ton of luck Left to spare. When i removed the cells and their connector board, i left them all together as the cells are connected via a bridge that is adhered and connected to the board via soldered pins. Which can be cut off and the ribbon cable can be unplugged or cut, but if the positive and negative terminals are bridged with the cutters... the cells will go supernova. Given the risks and my dwindling luck... The question is... do i need that board? I'm not 100% certain, but thoughts remains...
Could it just refuse to power on entirely? 
Will the Surface book see that there is no board, no battery, and panic, locking the CPU to a snails pace?
Will in collapse into a black hole upon doing its initial scan and swallow me hole, angry that a novice like me tampered with it's internals? 
These are things i do not know. To keep or not to keep?

### The Theory_

Given that the surface book is specifically designed to be "fully" operational upon being un-docked, the tablet being able to work independently and the base just becoming a brick with a lit up keyboard as it has its own, much larger battery... I don't think it will even notice the missing board so long as they stay connected, now if i ever detach the tablet portion... for one it would blink off immediately as it doesn't have a battery. The tablet portion does have its own charging port, and if I un-docked it, and plugged the AC charger in, that would probably be were the panic and CPU locking come into play. I don't plan on doing that and given they will remain joined as one... i think its okay if I leave out the connector board. I can always salvage the connector board as I still have it and the cells in the temperature, cool closet.

</details>
