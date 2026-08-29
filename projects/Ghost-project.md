# 👻 Ghost Project *(In Progress)*

---

[Back to Portfolio Homepage](../index.md)

* **Device:** Samsung Galaxy s20 FE
* **Primary Issues:** Damaged, unusable display.
* **Objective:** Confirm internal health and convert to headless documentarian using python and API
* **Tools Used:**

## Project Logs

---

### Volume_001_Revival

<details markdown="1">
<summary><b></b>2026-04-12: Proof of Life</summary>b></summary>

Proof of life: DeX (Desktop eXperience)

### Project Background_

I have an "old" Samsung Galaxy S20 FE that was my primary phone for a good while, was also my first
android based phone. Previously I was exclusively in the apple ecosystem.
A~A year and a half ago the phone was partially crushed when slipping out of my pocket at the same time
I was closing a car door (a perfect disaster), smashing the screen and bending the phones chassis slightly.
After this point... the phone is unusable as a standard device, it has laid dormant and powered off until now.

### The Objective: Documentarian AI_

Turn this "broken" S20 FE into a faceless "voice in a box".
An AI that can be communicated with entirely via voice commands.

### Concerns: Potential Project Killers_

-Since the phone is bend slightly... is the battery damaged?
This could be a project killer, but in peeling off the back of the phone, the battery seems to be unscathed.
-Since the screen is shattered and lifeless... how do I interact with it for the initial setup?
Luckily, the S20 FE has DeX, and in using an on hand USB-C to HDMI cable, After a quick charge (30 min), I was able to plug the FE into a monitor
and am looking at the sign in screen for the phone.

We have proof of life!

### Problem: Interaction_

While I can see the phones DeX lock screen, i have no way to interact with it to actually type my pin in.
The monitor i have has no other port for mouse and keyboard and neither does the phone.

I will have to buy a USB-C HUB with USB and HDMI ports to further from here.

</details>


<details markdown="1">
<summary><b></b>2026-04-14: PART-1 The Bridge Paradox</summary>b></summary>

Bridge: DeX + ADB (Android Debug Bridge)_

### Arrival & Interaction: Acer USB-C hub_

Was able to sign in with my pin through DeX via the USB-C. I am officially in.
Though this is a messier process... so while I'm booted into DeX, the plan is to focus on setting up
the S20 FE for android debug bridge first, while also checking off some setting that the AI will need later.
ADB will streamline the process of accessing the phone, the hope is to be able to wordlessly connect from my laptop.
I have never used ADB before, but its essentially like SSH (secure shell) which have used for for Ubuntu-server (overseer-alpha),
and plan to use for A.R.C.I/O once ready for python coding.

### Basic DeX settings_
* **Developer Option:** 7-tap ritual for "full" control.

* **Disable ADB Authorization Timeout:** Once The S20 FE is connected and trusts my laptop, it won't forget it after a 7 day period.
 
* **Power Saving Mode "OFF":** Having this "on" could throttled background tasks that I'll need running 24/7 for the documentarian.

* **Stay Awake:** Toggled on as the S20 FE will always be plug into the wall for power.

* **Limit Battery To 85%:** Far less harsh on the battery and will reduce heat. 

* **WiFi persistence "Always On":** Maintains connection as I will need to ADB into the phone and will have the S20 FE sending Logs 
to (Slack, for now).

	
### The Big Problem: ADB/RSA (Rivest-Shamir-Adleman) Paradox_

So... RSA is a wonderful algorithm used as the "Trust Gate"- its the handshake that I need so that the S20 FE sees and trust my laptop
in order to let my laptop ADB in.
The issue here being... the "Allow" button for the RSA prompt only appears on the phone screen itself and does not appear in DeX, I need to ADB in to get a 
view of the actual normal phone screen outside of DeX mode to see and tap the "allow" pop up... but I need the RSA handshake to enter ADB... (moderate panic ensued).
This is a security feature of android, but in my case was just fuel for panic and for a few minutes I thought this project was dead in the water. 
Yes, I could always replace the screen, but at that point it just becomes a regular phone again, while that's good, its not the project.
	
### The Fix: Occam's Razor_

In DeX mode, you can actually toggle back out to the regular phone screen, the HDMI cable will just mirror the actual normal phone screen on the monitor.
This worked. This simplest solution is indeed often the correct one. The USB-C hub was the real hero here.

### Done with DeX, Time for ADB_

Finally in, was able to establish the first ADB connection via Ethernet cable.
*Using the Ethernet port on the Acer USB-C hub for the S20 FE and a USB (male) to Ethernet port (female) dongle for my laptop (Lenovo think-pad 1 which doesn't have a native Ethernet port)*

### Basic commands for ADB in the Lenovo's terminal (running ubuntu 24.04.4 LTS)_
* **"adb devices"_ Lists available adb devices**
* **"adb connect (IP:Port)" to actually form the connection between the devices**

Initially I had a port# for the connection, but each time the Lenovo or S20 FE was powered off, that port resets, so id need to recconect via HDMI and use DeX or Mirror to get a new one. (Not ideal).
Quickly i learned i could use a command "adb tcpip 5555" to set the port. Though the S20 FE has to be plugged into the Lenovo via USB to set that port#. 
Not a problem and is only need when either has been powered off completely. 
A pretty neat and handy bypass.

</details>


<details markdown="1">
<summary><b></b>2026-04-14: PART-2 The Purge</summary>b></summary>

### Getting Android out of the way_

Deciding on a happy medium between not killing the android OS completely while still being able to run ubuntu.

* **Deleting old files. ig: Photos, Notes, app cashes, etc. Making room for the Documentarian.**
* **Disabling most all apps and unneeded services, Google Play, Phone, Messaging, Bixby, etc. Eliminate combatants.**


### Killing the system updates:

The device is due for and update, in order to maintain stability and coexist with the android OS, I had to prohibit it from initiating those updates.

### For the actual system (SM-G781U1_192.168.7.xxx:5555)
* **adb -s 192.168.7.xxx:5555 shell pm disable-user --user 0 com.sec.android.soagent &&** 
* **adb -s 192.168.7.xxx:5555 shell pm disable-user --user 0 com.wssyncmldm &&** 
* **adb -s 192.168.7.xxx:5555 shell pm disable-user --user 0 com.samsung.android.soagent**

Doing the same for the ABD emulator on my Lenovo as an extra safe guard.

### For the android debug emulator (SM-G781U1_emulator-5554):
* **adb -s emulator-5554 shell pm disable-user --user 0 com.sec.android.soagent &&** 
* **adb -s emulator-5554 shell pm disable-user --user 0 com.wssyncmldm &&** 
* **adb -s emulator-5554 shell pm disable-user --user 0 com.samsung.android.soagent**

Doing a similar hault for the Samsung account, which i can't safley disable without potentially giving the phones kernel a panic attack,
so setting to disable the notifications for the samsung account.

### Killing the Samsung account notifications (keeps it running in the background without prompting user to “join the ecosystem”):

### For the actual system (SM-G781U1_192.168.7.xxx:5555):
* **adb -s 192.168.7.xxx:5555 shell pm disable-user --user 0 com.samsung.android.mobileservice**

### For the android debug emulator (SM-G781U1_emulator-5554):

* **adb -s emulator-5554 shell pm disable-user --user 0 com.samsung.android.mobileservice**

*This Samsung account notification disable attempt didn't take, will live with the notification... for now*

</details>


<details markdown="1">
<summary><b></b>2026-04-14: PART-3 Foundation</summary>b></summary>

ACT-3 - Foundation_

Now that the bulk of android is walled off and the system is clear, I can start building the foundation for the Documentarian.

I have decided to Name the Documentarian... Ghost ...Its not a word of high phonetic clarity but it fits the system well. 
I will troubleshoot the Phonetics for the wake word best i can when i get to that point.
The name is more symbolic than practical, "Ghost" a dead device that should have been discarded and would have been.
Sort of a theme for this build and others, I get some sort of deep warm feeling when i revive a "broken" piece of tech. 
It also starts with a "G" and similar to ARCIO's alphabetical hierarchy, Ghost's "G" mirrors my name starting with a "G" as she is a direct partner of myself, we will work in tandem.

### Retroactive Reflection_Ghost Philosophy

*Its no deep secret that products today, tech especially are meant to be disposed of, designed to fail, designed to be forgotten and replaced 
by a newer model with negligible improvements.
The art of refinement and tinkering is being snuffed out. While I didn't have the confidence or knowledge to push back against this even a months ago, I do now.
I may be dramatic or too emotional, but the results remain. 
Ghost, A.R.C.I/O and the Surface Book, are all projects I've tacked in the past few weeks, being completely out of my depth at every turn. Yet I remain.*

*It has felt like the "END" so many times.
Hitting a wall that feels as if, with every stretch of the mind is... Impossible to overcome.
It's been certain in my head at several points that "There's nothing more I can do, It's broken, I Failed... I lose."*

*Then, you come up with an idea, or maybe just a seed of an idea and it blossoms, turning the "Impossible" to a "Maybe", to an "Accomplishment."
There is ALWAYS a path to restoration. Nothing is ever truly broken. Ghost represents that very same philosophy, "Broken is a temporary state, not a final identity."*

*When rebuilding, fixing what's wrong is only part of the equation, Finding a purpose for what remains is the other.*

### Building The Foundation_

(Apps)
-Installing F-droid - as the google play version was out of date and Ghost is now a "Google-less" system.
-Installing Termux (Terminal) and Termux API (Nervous System- allows Termux + Python scripts to communicate with the phones body).
	
(Termux Packages)
* **"pkg install termux-api"_ While Termux-API is an app installed via F-Droid, without this command line tool, the Termux App can't actually call functions inside the Termux-API app.**


### The proot-distro debacle_

(proot-distro)
* **"pkg install proot-distro"_ Allowed me to run the Ubuntu distro in Termux without having to root the phone.**

The initial plan was to go through a proot-distro Ubuntu layer to have a standard Linux environment with dependency stability as well as not have to root the phone which can get messy and could 
brick the phone, tripping Samsung's Knox security fuse. 
However, Ubuntu was complicating more than it was helping. The separated Ubuntu layer was proving to be unreliable in connecting with the Termux:API and slowing the system.

This caused me to step back and realize, Python3 and these scripts I'm running, don't need a full OS, just a place to run. Termux is plenty for this project, 
while it's respiratory isn't as vast as a Full OS like Ubuntu. Termux still has a massive library and is already optimized to function with the Samsung's hardware while also not running a heavy OS on top.

### Brain.py_
* **"apt install python3 python3-pip nano git"_ Essentially the brain, where ghost logic is written.**

* **"termux-battery-status"_ Monitoring ghost's power levels since she’s running on a salvaged battery/wall-power hybrid.**
* **"termux-tts-speak"_ The initial method for giving the Ghost a voice during the Python testing phase.**
* **"termux-setup-storage"_ The command that allowed the Linux environment to "see" the phone's internal storage, which was necessary for saving long-term logs.**

Created a directory specifically for Ghost's logic. 
This is where I started testing the initial communication scripts that would eventually evolve into the current Python iterations.

### The foundational script to test Ghosts vocal chords_

import os

def speak(text):
	    print(f"Ghost is saying: {text}")
	    # This command sends the text back to the Android system to speak
	    os.system(f'termux-tts-speak "{text}"')

speak("System online. My name is Ghost. I am ready to document your progress.")


adb shell am start -n com.android.settings/.Settings\$TextToSpeechSettingsActivity


adb shell settings put secure tts_default_synth com.google.android.tts


termux-tts-engines


*Ghost is alive.*

</details>

### Volume_002_Peripherals

<details markdown="1">
<summary><b></b>2026-04-15: Ghost Brain</summary>b></summary>

Ghost can fully speak through the microphone via "termux-tts-speak", provided I tell her what to say.
This is very exciting and fun to already have a voice for her, however... she needs a brain.

A.R.C.I/O will be a full on droid, He will run entirely on python, but for ghost, I am going to try and mesh in some AI.
Essentially making Ghost the uncanny valley of Alexa.


### The bottleneck_

The S20 FE's snapdragon 865 processor, is a respectable chip, its stable and efficient. It even has an AI engine for photography and voice recognition.
However it does lack the Neural processing unit that these newer chips have, making it "obsolete" for running AI's with any sort of efficiency... natively.
The S20 FE with a local LLM or SLM could likely get about 5-10 tokens per second (assuming it didn't melt) 
To match a normal human speech cadence, 15-20t/s would be the benchmark.

### Adjacent evidence_

Before converting my Dell XPS 8910 PC tower into an Ubuntu Server, I messed around with creating a local AI using Librechat via docker.
The Dell has an i7 quad-core processor and 16GB of ram. At the time was running Linux Mint Xfce, which is a pretty light OS.

Despite that, running Gemma 3B as the local AI, the Dell was able just barely hit 15t/s while the fan screamed in agony.

I had better success running Lama 3.2 at 1B, clocking around 30t/s which seems impressive. But actually felt much slower than that. 
Partly due to the docker container, but the main culprit being that i7 processor just not being built for AI, lacking that NPU.
Not to mention 1B models aren't very smart, essentially auto complete with a dash of personality.

Given that, It's not going to be a good call to go local with the AI portion of Ghosts brain. A 3B would turn her into a puddle and a 1B would essentially be
a toddler on drugs.


### Groq pivot_

How do I maintain privacy, stability and intelligence? 
By using a Groq API (Application Programming Interface) key. This key will allow me to give ghost the AI portion of her brain without the hefty weight being directly on
the device. It's cloud based allowing ghost to have 8B parameters or ~250t/s. Making ghost super fast and intelligent. As for security, yes, its cloud based but the data
isn't collected or kept, only stored on the device. 
For this I decided Ghost will run on llama 3.2 8B model.


### Ghost_v1.0 


After establishing the API key as the AI implementation method, its time to build out the python script.

Using a Bash script to bridge the Termux Speech-to-Text API with the Groq Python script, 
Ghost officially has gained her ears... sort of, the foundation of ears is here, but ghost could only be communicated with via physical inputs on a keyboard.
I could now type "note that" followed by a "note" and the 70B model would send back a block of text, reading it aloud in response as well as log the "note" in the RCO text file. 
Ghost is essentially a chat-bot documentarian now.

	Brain.py

	import os
	from groq import Groq

	# API key from Groq
	client = Groq(api_key="API_KEY")

	def ghost_chat():
	    print("Ghost is online. Type 'exit' to quit.")
	    while True:
		user_input = input("You: ")
		if user_input.lower() == 'exit':
		    break
		    
		# The logic for notes
		if user_input.lower().startswith("note that"):
		    with open("rco_build_log.txt", "a") as f:
		        f.write(user_input + "\n")
		    print("Ghost: Note saved to rco_build_log.txt")
		    continue

		# General Chat
		completion = client.chat.completions.create(
		    model="llama-3.3-70b-versatile",
		    messages=[{"role": "user", "content": user_input}]
		)
		print(f"Ghost: {completion.choices[0].message.content}")

	ghost_chat()



	listen.sh

	#!/bin/bash
	while true
	do
	  # 1. Listen for audio and convert to text
	  # This opens the Google Voice overlay briefly to grab your words
	  result=$(termux-speech-to-text)

	  # 2. Check if you actually said something
	  if [ ! -z "$result" ]; then
	    echo "Architect said: $result"
	    
	    # 3. Pass the text to your Python script
	    # We use a flag like --voice so the script knows it's a voice command
	    python3 talk.py "$result"
	  fi
	done


</details>
