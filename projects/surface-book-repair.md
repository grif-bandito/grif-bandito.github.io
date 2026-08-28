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
