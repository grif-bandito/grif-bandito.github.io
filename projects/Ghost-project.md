# 👻 Ghost Project *(In Progress)*

---

[Back to Portfolio Homepage](../index.md)

---

### Project Description

I have a difficult time keeping track of dates and certain events that take place throughout my projects and would like a hands off way to keep notes. 
An old phone of mine, A Samsung galaxy s20 FE is broken, slightly bent and the display is completely useless. I believed the internals were still good, so 
Ive deiced to embark on the journey of restoring the device into a faceless brain of a documentary device. Something I can say a memo to aloud and have it record that note in
file i can easily access on my daily drivers. I plan to use DeX and adb to modify the OS of the device and use a combination of AI, Python, API, and local repositories to create this assistant. as well as have the device safely and securely mounted in a custom wooden cooled chassis.

---

### Details

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

---

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

<details markdown="1">
<summary><b></b>2026-04-16: Selective Hearing</summary>b></summary>


Today is a big day, ghost truly has a name now and a wake word.
It's not perfect, but she seems to hear "ghost" and start listening ~60% of the time.

### Diagnostic Limbo_

This is something I was aware may happen, given "ghost" isn't a strong phonetic word, I still haven't thought of a way to aid with that, yet.
Her wake word can always be changed, and may have to be... but I hope to keep it, potentially bulking to a "two word wake word" like "hey ghost".
I'm going to leave it alone for now as I'm not 100% sure of anything on that front, I have been known to mumble... so it could just be me.

Another factor is that when I'm ADB'ed into the phone, looking at the screen on my lenovo, upon activating her wake work, a green microphone icon will pop
up in the top right corner of the screen for ~1-2 second, that good, tells me she hears her name and is helping me gauge how long she's actually listening when
activated... BUT, it seems to be inaccurate. I think shes actually listening for a slightly longer amount of time after the icon disappears. The icon also doesn't
appear instantly after the wake work is heard and understood by her, so there is some lag, or more likely its just her processing time.

All in all, in regards to the wake word, I'm going to give it some time to feel out how long shes actually listening and the gaps in time she needs to process the wake word
upon hearing it. Better to test a bit more before going all "Gung ho" making any major wake word changes. 
This is all so crazy to me still, python is becoming a bit less scary but still feels so fragile. While Gemini is a big help with scripting the python, I am here to learn.

### Logging_

Another huge milestone. Ghost is now capable of logs. Yes, before she could save logs to a text file natively, but now, via Webhook she can submit logs directly to Slack!
Using the "note that" command following the wake word, she will log to a slack channel that i can view on my phone, rad. 

### Drum roll, please_

Ghost's first successful log:  "not that rco is a r c i" -ghost 9:04pm

Intended log:  "ARCIO is A R C I O, Aluminium, Remote, Computer, Input, Output"

Now... This is really cool, but... there's a couple problems here... And the speech to text hearing "ARCIO" as "RCO" isn't a concern of mine, it makes sense. RCO is actually a cool
nickname of sorts. But for the sake of "what I actually said and thought" vs "what ghost heard". It's important to recognize.

### Problem #1_
Ghost logged the command itself "wake word"

### Solution in theory_
It seems she starts the log with the command, so possibly it needs to be specified in the script to tell her to "yes" acknowledge the command, but start the log after the command.

### Problem #2_
Ghost did not log the full message.

### Solution in theory_

Either ghost thinks the log is over prematurely or shes incapable of listening for longer, could be the script or this could be android interfering and killing the listening after 8 characters
of input. Will test further and see.

Ghost log @10:54pm:  "not that i like cheese" 

Intended log:  "note that I like cheese"

### Script thus far:

	import os
	import sys
	import requests
	import json
	import datetime

	# --- CONFIGURATION ---
	GROQ_API_KEY = "API_KEY"
	SLACK_WEBHOOK_URL = "WEEBHOOK"
	WAKE_WORD = "ghost"

	# Sliding memory: Remembers the last 5 exchanges
	history = []

	def ask_groq(prompt):
	    global history
	    print("\n[DEBUG] Brain: Connecting to Groq API...")
	    url = "https://api.groq.com/openai/v1/chat/completions"
	    headers = {"Authorization": f"Bearer {GROQ_API_KEY}", "Content-Type": "application/json"}
	    
	    history.append({"role": "user", "content": prompt})
	    if len(history) > 10:
		history = history[-10:]

	    messages = [
		{"role": "system", "content": "You are Ghost, a dry-witted AI sidekick for the RCO robotics project. You help document builds and solve IT problems."}
	    ] + history

	    data = {"model": "llama-3.3-70b-versatile", "messages": messages, "temperature": 0.7}
	    
	    try:
		response = requests.post(url, headers=headers, data=json.dumps(data), timeout=10)
		print(f"[DEBUG] Brain: Status {response.status_code}")
		answer = response.json()['choices'][0]['message']['content']
		history.append({"role": "assistant", "content": answer})
		return answer
	    except Exception as e:
		print(f"[DEBUG] Brain Error: {e}")
		return f"Error connecting to brain: {e}"

	def log_to_slack(text):
	    timestamp = datetime.datetime.now().strftime("%I:%M %p")
	    print(f"\n[DEBUG] Slack: Sending log...")
	    payload = {"text": f"📍 *BUILD NOTE* — _{timestamp}_\n> {text}"}
	    try:
		r = requests.post(SLACK_WEBHOOK_URL, json=payload, timeout=5)
		print(f"[DEBUG] Slack: Status {r.status_code}")
		return True
	    except Exception as e:
		print(f"[DEBUG] Slack Error: {e}")
		return False

	# --- MODE SELECTOR ---
	if len(sys.argv) > 1:
	    # VOICE MODE (Triggered by listen.sh)
	    raw_voice = " ".join(sys.argv[1:]).lower()
	    if WAKE_WORD in raw_voice:
		user_input = raw_voice.replace(WAKE_WORD, "").strip()
		
		if not user_input:
		    os.system('termux-tts-speak "Yes, Architect?" &')
		    sys.exit()
		
		if user_input.startswith("note that"):
		    if log_to_slack(user_input):
		        os.system('termux-tts-speak "Logged to Slack." &')
		    else:
		        os.system('termux-tts-speak "Slack sync failed." &')
		else:
		    answer = ask_groq(user_input)
		    # Remove quotes from the answer to prevent shell errors
		    clean_answer = answer.replace('"', '').replace("'", "")
		    # THE FIX: Fire and forget using '&' and double-quotes
		    os.system(f'termux-tts-speak "{clean_answer}" &')
		sys.exit()

	else:
	    # TEXT MODE (Manual interaction)
	    print(f"\n--- GHOST ONLINE | MEMORY: ACTIVE | SLACK: SYNCED ---")
	    while True:
		user_input = input("User >> ")
		if user_input.lower() in ['exit', 'quit']:
		    break
		
		if user_input.lower().startswith("note that"):
		    log_to_slack(user_input)
		    continue

		print("Ghost >> Working...", end="\r")
		answer = ask_groq(user_input)
		print(f"Ghost >> {answer}")
		# Even in text mode, try to speak the response in the background
		clean_text = answer.replace('"', '').replace("'", "")
		os.system(f'termux-tts-speak "{clean_text}" &')



	#!/bin/bash

	# --- GHOST LISTENER V2 ---
	echo "--- GHOST IS LISTENING (Headless Mode) ---"

	while true
	do
	  # 1. Capture the audio and convert to text
	  # Using -q (quiet) to keep the terminal clean
	  VOICE=$(termux-speech-to-text)

	  # 2. Check if you actually said something
	  if [ ! -z "$VOICE" ]; then
	    echo "Architect said: $VOICE"
	    
	    # 3. Pass that text to the Python brain
	    # We use python3 to be specific
	    python3 ghost.py "$VOICE"
	    
	    # 4. Small breather to prevent CPU spiking
	    sleep 0.5
	  fi
	done

</details>


<details markdown="1">
<summary><b></b>2026-04-17: Selective Hearing P.S. </summary>b></summary>

### Selective Hearing Postscript_

Still not fantastic results, but progress. 
I am certain android is limiting the amount of time the microphone stays open, but I'm uncertain of how to bypass it.
The work around thus far is using the "-p" partial flag, which sort of... "fakes" the listening window being open for longer, essentially having ghost's speech-to-text
stream "guesses" in real time of what I'm saying, as I speak. It should hold the microphone open longer, rather than just cutting off at the first bit of dead air.

### Ghost log@12:03am: 
	note
	note that
	note that
	note that
	note that
	note that rco
	note that rco stands
	note that rco stands for
	note that rco stands for
	note that rco stands for
	note that rco stands for
	note that rco stands for aluminum
	note that rco stands for aluminum
	note that rco stands for aluminum remote
	note that rco stands for aluminum remote
	note that rco stands for aluminum remote control
	note that rco stands for aluminum remote control
	note that rco stands for aluminum remote control
	note that rco stands for aluminum remote control
	note that rco stands for aluminum remote control input
	note that rco stands for aluminum remote control input output
			
As you can see, this backfired by creating a stutter of sorts... submitting every "guess" to slack... still, it's progress.
Ghost did capture the full log and this one in particular was 10 words, an improvement over her 7-8 capture limit before timing out like in the previous logs.
The only real error is that I said *control* rather than "computer". Call it collocation, the late hours, or a subconscious cry for help given the lack of control I currently have.
Either way... technically the only error here was human. 



### An important realization_

Notice, this particular log has 11 words...


### Ghost log@:12:29am:

	note
	note that
	note that this
	note that this is
	note that this is your
	note that this is your first
	note that this is your first
	note that this is your first
	note that this is your first night
	note that this is your first night of
	note that this is your first night of being
	note that this is your first night of being
	note that this is your first night of being
	note that this is your first night of being on
	note that this is your first night of being on all"


But I've changed nothing... so... the "-p" isn't helping keep the microphone open longer? 

But, it did... I wasn't able to get ghost to log any more than 7-8 words until I implemented It.

Okay, then... let's just say it IS 100% only "time limit based"

Meaning android's speach-to-text is the main bottle neck here, cutting the microphone off prematurely. So... in theory, if i talk super fast, ghost could log... indefinitely? 

### No, and I'm slightly more confused_

Poking around on google it seems that typical android speach-to-text doesn't technically have a hard coded timeout... but if a pause of 2-5 seconds is detected, it will stop and process 
whatever input it's been given. Though the limit on how long the microphone could theoretically stay open is 60 seconds. AND "supposedly" with Termux in the mix, it may drop the 2-5 down
to a more harsh 2 seconds, which could be what's limiting Ghost... I don't know.

What I do know is..rambling on and on doesn't keep the microphone open any longer + speed talking will only limit Ghost's accuracy nor is it ideal for logging competent notes. 
I need to be able to pause, collect my thoughts, then resume. 
Ghost needs to be able to receive clear input for accurate logging.

There is also a possibility that some kind of background conflict is happening, where something else is fighting for control of the microphone, however, I've disabled everything that could/would do this,
like Bixby, whom would be the biggest suspect.

Could be an STT glitch?

Truly... I don't know.
 

### The "-p" Conspiracy_

The "-p" isn't the fix here, while i do think it is giving time for another couple words... i think it's doing so via lag.
Bear with me here...
I'm thinking, by adding that extra layer of processing for each "guess", The "-p" is actually lagging the speach-to-text, causing it to stay open for just a hair longer.
This would explain why we jumped from a 7-8 to a 10-11 word limit...  and I know it can't be a character limit as the 12:03 log has 57 letters and 9 spaces and the 12:29 log has 40 letters
and 10 spaces.

So TECHNICALLY it is helping, just not very well, moderately inconsistently and makes the slack logs messy.

So now I'm back to android timing out being the issue... even though technically it doesn't timeout as long as I don't pause... ugh.


### Problems here, problems there, lets see if the ghost can bear_

Despite all that, and as could be guessed by Ghost 12:29am log... which was actually supposed to say: "this is your first night of being on all night"
Redundant I know, but maybe ghost did too and is smarter than I think. Either way, I'm going to leave her running all night... the first official stress test.

### Concerns:

Will the S20 FE overheat and burn the house down? _ I set the phone on a glass White Barn candle scented: Autumn Woods... might help, might be the last thing I ever smell.
Will she shut off by morning? _ If so, we have bigger problems then a Stutter and Androids kill word.
Will I awake to several strange hallucinate logs in slack? _ I hope so.

</details>


<details markdown="1">
<summary><b></b>2026-04-17: Checkmate</summary>b></summary>

### Background Elements I Haven't Formally Documented_

### 1. The listen loop_

I haven't actually figured out how to have ghost in an "always listening" state. The solution so far has been a "heartbeat". As noted in the "Selective_Hearing" Log.

"sleep 0.5" This was the original attempt at "faking" an "always Listening" state. though this didn't work for two reasons... 

### Reason #1:
"0.5" doesn't give Ghost enough time to process a log or even just a general "hello" before opening the next "listening" window.

### Reason #2
This actually completely messes up the listening window as ghost will talk over herself and it will off and on listen even after the wake word was heard and understood by ghost.

The actual version that was active during the "Autumn Woods" stress test was patched. By having "sleep 15" giving ghost 15 seconds of uninterruptible down time before having to
open her microphone to listen in for the wake word. As well as a separate down time of "sleep 10" for the slack logging, ensuring she has a total of 25 seconds of full down time
to process and reset after a "note that" command was used. The "sleep 15" was bumped up to a "sleep 30" for the initial overnight "Autumn Woods" stress test.
These are functional for now. The 15 seconds is manageable... but if she doesn't pick up on the wake word... its a longer wait than you'd think to try again.



### 2. The Torch_

This is a newer addition that was also implemented for the "Autumn Woods" stress test. Before, like with all phones, I was able to know when the microphone was actually open via
the chime that plays when it activated and the chime that plays when it deactivates. But i didn't want to hear that all night... so i figured a blinding bright light would be better.

Using "termux-torch on/off", the flash on the S20 FE will blink when the microphone opens. With the device on silent, its a pretty solid way to get feedback without a little noise every
15 seconds. 
As mentioned in the previous log, during the stress test i had the S20 FE on a glass candle and because i was concerned about heat i had the camera bump overhanging and flashing onto 
another candle's metal lid. The flash actually didn't get hot at all upon checking this morning, but better safe than sorry.

For long term, the torch wins over the chime, it actually gave me a fun idea for the box i intend to house her in... but that's for another time.


	
### The Morning After: Autumn Woods Stress Test_
	
Success! Ghost ran all through the night! The S20 FE was cool to the touch, neither of us were burnt to a crisp and the script was open and running all night!
Unfortunately... no strange logs in the slack channel, can't win em all.

Ghost was blinking her light for a bit over 12 hours in total before I had to "ctrl+C" the fun and get back to tinkering.

So... we have a wake work, we have a system that doesn't destroy itself when left alone for half a day... what now? Break pads.



### The Checkmate Protocol: Kill Word_

This idea hit like a truck. we need a "send button" a way to tell the system "okay, NOW I'm done talking". I think this could be a key element. Its a way to rid myself of these Android timeouts
and eventually do away with the confusing "-p" flag and it's strange magic. (I may keep it for now, having the "guesses" pop up like that... is a pretty neat spectacle and kind of displays
Ghost actively listening and thinking. It will have to go eventually... It's really janking up the Slack logs.)

The implementation of a kill word in which I've chosen to be "checkmate" as its pretty strong phonetically and its an uncommon word that I wouldn't use otherwise. This should force the
script to keep the microphone open, as I'm certain that nothing in the background is fighting for the mic. As long as I'm right about that... this should work.

</details>

---

### Volume_003_Body

<details markdown="1">
<summary><b></b>2026-04-18: The Box Part-1</summary>b></summary>


Today I implemented some ideas I had been brewing while working on the software side of Ghost. Taking some measurements and staring at that wooden "bench" trying to figure the
best way to do this. I have a pretty good idea in mind, using scrap wood and various bits of hardware i plan to evolve the "C shaped bench" into an enclosed cube...

### The Must haves_

* **1. Cooling_**
Given, at the end of the day... I'm putting a lithium ion battery powered phone that will be running 24/7 into a wooden enclosure, It needs to stay as cool as possible.
To be fair, the device will always be plugged into the wall, the charge is limited to 85% and has not shown any signs of any kind of heat whatsoever... still, lets not push it.
The "bench" already has those rectangular holes I mentioned before, The idea is to have the holes vertically so i can mount a fan to the top and use a "mesh" on the bottom to
prevent the inside from getting... fuzzy. With a fan on top, pulling the air in from the bottom hole and blowing it up and a way, this should create a wind tunnel, that will pass directly
across the phones screen, it also helps that heat tends to enjoy rising. Heat on the S20 FE is primarily dissipated via the screen and i need the camera bump facing outward, so this should
work pretty well overall. 

* **2. Feedback_**
In previous logs I mentioned that the device's flash will blink every 15 seconds to indicate Ghost is listening, my idea is to keep that by having a big, circular cutout in the box right
over the spot that the phones camera bump will be. By adding some Photography light filters inside the box, between the phone camera bump and the cutout, it should take the edge off of
the brightness of the flash and allow me to change the color of the "heartbeat" light to a more "droid esk" red.

* **3. Mounting_**
This part is strangely a bit more tricky. The two things i need to mount are, the HSBC hub and and S20 FE itself. They need to be removable and close enough to connect. 

The S20 FE needs to have cutouts in the box for the top, bottom microphones so i can talk to Ghost and she can hear me. It also needs a cutout for the USB-C charging port so the USB-C hub can
connect. Another factor here, is screen rotation, as when I'm ADB'ed into the phone, working in Termux, I like the phone locked at a horizontal rotation. This creates a better view for a desktop.
Mounting the device horizontally is a concern as I don't want the "heartbeat" light cutout to be too low on the box face.

The USB-C hub is a bit more difficult as it has ports all around it and the hub does actually get pretty warm, so i don't want it directly on the wood. Its a relatively flat and slightly elongated
rectangular prism. The hub has an Ethernet port on one end + the USB-C male cable that will plug into the phone on the other end, 2 USB-A 3.0 ports + a USB-C data transfer port on the top long edge,
and an HDMI + USB-C PD port on the bottom edge. I want to be able to access all over these port, not entirely sure how I'm going to mount it... yet.


### Scrapper Manifesto_

The "How am i going to mount this thing?" question, followed by just staring at what i need mounted and what I currently have to mount it and racking my brain until i get a headache... Is a dilemma I'm
becoming more an more familiar with. If you look up on google "How to mount (Insert whatever tech)" you'll find two prominent answers, plastic Tupperware (Solid, but all of mine is glass) and my favorite
"Just 3D print it!" (I don't have that either...) I'm Not made of money, nor do i have a lot of tools and no.. i don't know how I'm going to mount all of this together into one cohesive unit. But that is
okay. Despite what I want Ghost to look like and even how i want her to function, I know from past experience with Music, Animation and Video production that there will always be a gap between the 3am 
crazy, perfect, polished idea and the limited reality based on what you have available and your own capabilities. Don't get me wrong, I'm not going for "Cheap", I'm going for "Practical". And yes, purchases 
will and have been made to further the project. But i found that typically, what i have is 90% of what i need, as long as i let the build morph and change into whatever form it needs to, from that very base
of whats already currently available. I have loads of random bits of hardware, scrap wood and "junk" parts from old tech... I have a foundation, let's see what ole Grif can MacGyver together.

</details>


<details markdown="1">
<summary><b></b>2026-04-18: The Box Part-2</summary>b></summary>


The wood for the starting point as the "C-shaped bench" is Cedar, Its a softwood, has a slightly warm tint and a strong beautiful smell,
which differentiates it from Pine. Pine is basically scentless (it dose smell like wood of course) and lighter. 
The Cedar is 3/4th inch thick and 2 of the 3 panels have those rectangular cutouts as mentioned in Part 1. 

Whats to be the face panel, is 8 inches in height x 7in & 1/4th in width and will have a 2 inch diameter 
hole cut out for the flash of the "heartbeat" light to shine through.
The top and bottom panels being 5in & 7/8th in depth x 7 & 1/4th in width.

### R & L panels:

I've removed the square dowel and have cut out 2 panels for the sides, where the ends of the phone will be. 
These panels are 1/2in thick ply wood and will need cutouts.

### If looking at the box from the front:

R panel: One small hole ~1/2 inch in diameter on the right panel. - For the Top mic.
L panel: A slot that is 4 & 1/2 inches tall and 5/8ths wide on the left panel. - For the Speakers, Bottom mic and USB-C port.


### Back Access panel_

This is an important one, and was a pretty nerve racking part of the build. 
The back access panel could just be screwed in and while i almost entirely interact with Ghost via Voice and ADB... I still want quick access to the inside of the box.
Id rather not seal the S20 FE in a wooden cuboidal tomb. So... MAGNETS! This was the sketchy, nerve racking part... I need four magnets in total... Two need to be inset
into the edges of the top and bottom panels. the other two need to be on the inside face of the back panel... which is already cut to size at 8 x 7 & 1/4, same dimensions
as the cedar face panel but is that same 1/2 ply wood as the R & L panels. 

### The How:

I chiseled out insets in the 4 previously mentioned locations that the magnets need to be, ill set in a layer of putty directly in the inset, then smush the magnets down on top,
remove the excess, fill the gaps best I can... hope for the best.
Using a leftover tube of JB weld Steel-stik epoxy putty from an armature I made a while back for claymation to secure the magnets. This JB putty should be overkill and super solid 
when set into the chiseled out insets in the cedar and ply wood for the magnets. Steel is also magnetic so, that's a bonus.

	
### The magnet inset concerns:

* **Splitting the ends of the Cedar top and bottom panels:**
This did actually happen... a chunk of the top panel on the inside face broke off completely, going all the way down to where the rectangular hole is (where the fan will 
eventually be mounted over). Best case scenario... It is hidden on the inside of the box and using some wood glue, it's like it never happened.

* **Strength:** 
Essentially, the back access panel is only held on by 4 total magnets and the plan is to somehow mount the USB-C hub to that very back panel... The worry is that the weight of the
ply wood + the USB-C hub will be too much for the magnets and... slide off or just not hold at all. Both the 1/2 panel of ply wood and the hub aren't super heavy, but they aren't weightless. Not to mention when i actually have the USB-C PD cable + Fan plugged in and the occasional USB-A for resetting the port number for ADB or just the act of plugging and unplugging back in may tear the panel off... also I'm not entirely sure what kind of mount will be used to secure the hub, but it needs to be light.

* **Polarity and alignment:**
This was the biggest concern, if I were to mount the magnets wrong, the magnets will repel each other and this access panel becomes... completely useless. To avoid this i snapped 
the magnets together, pulled them apart and laid their attracted faces up, marking them with a red sharpie, I was extra careful with my measurements and made sure the insets were 
"perfectly" aligned before committing to the epoxy putty and magnet setting. Given that once the epoxy was set with the magnet in place... I won't be able to snap the panel on
to actually verify everything was alighted until i was 100% sure the epoxy had FULLY set, otherwise the magnets would just pull themselves out of place. It was a leave it overnight and hope it snaps into place the next morning type of deal. I started building around 8 AM and finished at ~10 PM.


</details>


<details markdown="1">
<summary><b></b>2026-04-19: The Box Part-3</summary>b></summary>
	

Success, the back access panel snaps on "perfectly" and actually feels pretty secure while not being too hard to pull off when needed.
The wood foundation of the chassis is set, now is a matter of getting everything mounted to the inside and outside. 
Today we learn if my measurements were accurate.

### The Intake:

A simple installation but an important one. This will be the grate that covers the rectangular hole on the bottom floor panel inside the box. A donation of sorts, since A.R.C.I/O
doesn't have a keyboard over his motherboard anymore, i took that keyboard, removed the keys and peeled off the membrane circuit (that thing was really on there) this left me with a flexible, metal sheet with a bunch of square holes in it. A few bends and snaps, from working it back and forth in a vise and BOOM... we have a pretty dang good grate that can sit over the rectangular hole on the floor inside the box. This will keep derbies out but allow for air to be sucked in via the fan. Keeping things cool.

### The Fan:

Here's a good case of a necessary purchase, maybe someday I can build a fan... My first idea was to use the two laptop fans inside an old mac book pro, thought better of it... as I do intend to fix that old thing. So I bought a 2 pack of 5 x 5 inch, 5 volt, USB fans. Ill save one for something else, maybe A.R.C.I/O. 
The fan sits really nice on top of the box!
Covers the ~2 inch x 3 inch rectangular hole and looks crazy cool. The fan has 3 setting, Low, Medium and High, even on High its super quiet and just blends into the Dreo tower fan noise that I typically always have going anyway.
Each fan has 8 rubber spacers on the 4 corners of each side, to reduce vibrations, since the fan will be mounted to the top of the box, i don't actually need the top four rubber spacers for the fan. I took those off and used two pairs of two different screw to mount the fan. I actually lost one rubber spacer... it rolled somewhere into the void under the workbench, spent an hour poking around, couldn't find it. So the spare fan only has 7 spacers now as I needed 8 total for ghost, the 4 for the fan to standoff on and I used the other 4 as feet for ghost to sit up off the table, that way there is a gap so the bottom intake can actually... intake air.

### The Mic Mishap:

As mentioned in Part: 2, a hole was drilled on panel R for the S20 FE's top microphone, unfortunately... its not super well lined up and I've had difficulties getting Ghost to hear her wake word "Ghost". Could be the phonetics or blockage from the box or an echo throwing things off... Either way she is hearing me less now. So, I mounted a 2 x 3 inch rectangular prism shaped block of wood to that side, covering the hole. This block is so I can mount a USB microphone directly to the box. Its a budget mic that I used for vocal recordings in the past. The issue here is that, if the microphone was mounted upright... the grill of the mic peaks up about an inch over the top of the box... right by the fan. The fan is quiet, yes, but sounds like a freight train to a microphone that is ~2 inches away from it. I mounted the microphone upside down and it seems to have fixed the initial issue of ghosts mic being blocked and the issue I created... technically these are both issues that I created... moving on.

### Phone and Hub Mount_

I've come up with a pretty solid plan for mounting the phone inside the box and the USB-C hub on the outside of the box. By using an "old" phone tripod mount that I've
fastened to the floor of the box using the threaded hole that's already there (Its designed to be screwed into the quick release plate on a tripod). The phone can be
locked in place horizontally. Ill be able to remove the back access panel and can turn the knob on the phone tripod mount inside the box, which releases the phone allowing 
me to slide it out of the slot in the L panel. The phone holder, has a tight grip, but is easy to release. Given the C-shaped clamp of the mount it will cover very little 
of the back of the device and allows the phones screen to be fully uncovered. Air can come in the bottom vent, breeze across the screen and be expelled through the fan on top.

For the USB-C hub I'm using 2 left over L brackets from A.R.C.I/O's 2020 aluminum extrusions. These will be fasted alternating up and down to cradle the hub while also
providing a stand off from the wood itself. Each L bracket has 2 threaded hole, I screwed them into the back access panel and used the other two holes for 17 gauge wire I had from claymation armature building. looping it in a Z shape around the USB-C hub, both ends of the 17 gauge wire meet on the inside of the back panel and are secured around a fence staple that had to be snipped at an angle on either side so it wouldn't bust through the outside of the back panel. Admittedly is a tad bit crude, but its secure, keeps the USB-C cool and off the wood as it can get pretty warm. This "mount" is also very light weight. 
Even withe the USB-C hub, its mount, the ply wood itself, everything plugged in and a good shake of the box... the magnets hold!

</details>

---

### Volume_004_Testing

<details markdown="1">
<summary><b></b>2026-04-25: Toast</summary>b></summary>

### 168hs of Uptime_

It has been roughly a week of ghost being operational within her wooden box, once I finished the box on the 19th, I wasted very little time getting her settled in it. As of now she sits on the corner of my desk, I plan to move her as my desk has gotten very crowded with all these parts laying around. She is pretty cool looking, this crazy, chunky wooden unit with a big red light blinking in intervals of 15... Despite her name, she has a pretty strong presents visually. Though to her name, and despite my concerns, she can fade into the background pretty easily and the blinking light isn't bothersome, even through the night. I have 3 photography light diffusers inside her, 2 red, sandwiched between an orange one. This works pretty well, ensuring the whole of the "eye" is illuminated evenly and keeps her from blinding me every 1/4th of a minute.

She's been pretty helpful lately, logging some often messy, but recognizable moments and being a good distraction from the struggles of building ARCIO at times. When I'm at the desk and activate her to note something and she does... its seriously cool. More often then not it's me saying "Ghost" then signing because i either missed the window or she "ignored" me... then I'm sitting there waiting for another blink... bit of a pain at times... but progress nonetheless. I haven't changed anything drastic with her coding, just minor teaks. I'm more so in a beta testing phase with her, shes functional but definitely not a fully capable documentarian, yet. Definitely room for improvements. Struggling to hear her wake word "Ghost", unreliable with understanding the "note that" command and... the hibernation mode... oh man... the hibernation mode. I'll get into that at another time, the main troubleshooting has been focused on solving the wake word issues thus far... baby steps.

It took me a few days to fully notice and perceive the wake word as an issue, I had thought that the devices microphone was gummed up or that it couldn't detect me while in the box. The USB microphone would solve these and it's not broken or anything. So its 100% something to do with the software. I landed on a pretty good idea, which apparently is one that other virtual assistants use, a good idea but not as outside the box as i though initially. The phonetics of the name "Ghost" aren't very strong... this I knew, but I had the thought of "Okay, if she's not hearing 'Ghost' then what is she hearing? What else sounds like 'Ghost'?". Most, Toast, boast... among others, I added these into her code, giving her some better chances of waking up when summoned. This... sort of works, it's defiantly better. I did actually wrestle with the idea of a rename entirely to "Toast" as... in her wooden box, she dose sort of look like a toaster... but no, her name is Ghost. I'll have to chew on this whole "Wake word dilemma" a bit more, see what I can come up with.

</details>


<details markdown="1">
<summary><b></b>2026-04-28: Toaster</summary>b></summary>

### Fire Hazard_

Uncanny foreshadowing... kicks like a joey. Maybe I spoke this into existence or maybe I should just be more careful with my wattage. A few days back I got some USB-C cables and 2 30W bricks to accompany them, the cables are braided and pretty nice, the bricks are yellow with a USB and USB-C port. Typically I use 1 of the 4 40W bricks i already have, 2 of them are just USB-C and the other 2 have 2 USB and 2 USB-C ports, these get the job done, but wanted a few more as they fill up fast... my greed is my downfall it would seem.

I gave Ghost one of the new pairs of cable and brick, this keeps the S20 FE juiced up and powers her 5V USB fan, all through one USB-C cabled from the brick to the USB-C hub on Ghost... this should have been fine one would think. BUT, in an act of stupidity as i was tinkering... i plugged in one of my Emart lights into the remaining USB port on that 30W brick. These lights pull very little power and generate no heat when on the dimmest setting, however, when I'm working i set them to full blast... they get very hot and pull a lot of power on high. So that poor little 30W brick was keeping a Samsung juiced at 85% and the 5v USB fan on high running continuously, while also powering the light that pulls tremendous power, for a couple sessions of several hours at a time while I worked. Bad... not good. The S20 FE pulling ~25W, USB fan at ~2.5W and the light pulling 15W... 42.5W total... super very not cool, "How am I not ash?" type of not cool. First of all.. the Samsung is probably not pulling 25W as its not charging from 0, just being maintained at 85%, so it could be closer to that 15W, even so, with all three, we are WAY over what that brick is able to support. Second of all, if the Samsung was Pulling a consistent 25W and the fan pulling that ~2.5W... 27.5W on a 30W brick is still way too close for comfort. third of all... I 100% janked up that brick an hour, if even, in to that night of supercharging it. This was probably why I wasn't engulfed in flames as the brick and cable entered "limp mode" fairly quickly given they were at most 12.5W over their limit. Glad they're moderately "stupid proof".

To make this worse, I didn't notice at first. After that night of unknowingly pushing the brick over 10W beyond what its designed for... I started to see that the fan was turning off and on, it would stop its blades.. then spin up again and repeat every so often. Eventually Ghost's light stopped blinking as she wasn't getting power and eventually died. That's when I opened everything up, confused, then checked the brick... which was VERY hot, it hurt to touch it and i have ZERO idea how this plastic brick didn't melt. That brick and cable are fried, though they dont look it. 

I Gave ghost her own 40W brick and a fresh cable, she is okay. Though I have little doubt that once she's smart enough to... I may be the first to go when the machines take over. 

It's safe to say I'm eerily lucky at this point, but my stupidity is watering it down for sure. Sorry Ghost.

</details>


<details markdown="1">
<summary><b></b>2026-04-28: Ghost Bear</summary>b></summary>

### Wake Word Solutions_

Bit of a multi task-er myself... almost burring down the house while also finding a solid solution for the "Wake work dilemma". As stated, I'm pretty stern on keeping the name "Ghost" and I remain just as stubborn on that front, the solution involves giving her a last name of sorts. 

Applying some strange but sound "logic" from the "Checkmate" command seems to be the key. Something I've done to make the "Checkmate" command work consistently, was mostly subconscious. The "Checkmate" command being the kill word, it closes her listening window and is especially helpful after giving her a "Note that" command. While just saying "checkmate" does work on its own, typically i say "Checkmate Ghost". "Ghost" is not programmed in any way to be understood or work with the kill word command. Despite that, this works nearly 100% of the time. Making this kill word combo far more reliable than her wake word or the "Note that" command on their own. I think it's partially due to "Checkmate" being strong, phonetically. By following it with "Ghost" it creates a sort of "run on" as just saying "Checkmate" is brief. That minor continuation of a second word allows for some type of cool down, its more information. This is all in theory, but i think its fairly close to why this is happening. And technically, if I'm right abut why this is working, it shouldn't matter what word follows "Checkmate" as nothing else is programmed to be the kill word... and it doesn't. I have said "Checkmate Butter, Gabagool, poop, etc" it doesn't matter, it works just as well, though I'll probably continue using "Ghost". to follow.

Applying this concept to the wake word, I'm doing so with a more programmed in approach. I added to the wake word "Ghost" with "Ghost, Kodiak". This helps out a ton. Technically she can be woken up with either independently. I found that using them together works super well. "Kodiak Ghost". While both are seen as wake words to Ghost's logic, "Kodiak" is very strong phonetically while "Ghost" isn't. By saying Kodiak first followed by "Ghost" its essentially a double chance for her to recognize a wake word. "Kodiak" being strong by itself but also creating that "run up" to "Ghost" when used first. It works incredibly well.
 
I chose Kodiak simply because it sounds cool and is strong phonetically, however I do like Bears and "Ghost Bear" is a pretty cute/rad name.

</details>

---

### Volume_005_Refinement

<details markdown="1">
<summary><b></b>2026-05-01: Dataset</summary>b></summary>

### Life with Ghost

Living with Ghost for a span of 12 days, minus a couple due to the near inferno incident, I have a pretty good idea of where we stand. During this run, I've done my best to tweak and refine, shes at a pretty good state... However, I'm going to go ahead and attempt a full on update & upgrade software wise. While I could leave her as is, I want that polish, to get her to a place where she is solidly reliable and capable. Ghost needs to be in a "Finished" state so that i can fully focus on ARCO without having to babysit... technically, she's supposed to be the babysitter here. 

Ghost's current version is technically v7.3. This is a solid version that at the very least works... though it has problems. The version numbers before don't really matter, they were messy and very limited. Though establishing v7.3 as the basis version and progressing from here is a good idea, should help me keep track of things... it also sounds cool.

### Ghost_v7.3_

* **Torch_**
The S20 FE's flashlight blinks every 15 seconds, Double blinks upon hearing the wake work and stays solid while listening until the kill word is activated. Solid feature.

* **Listening_Cycle_**
Unable to listen indefinitely, A 2-3 second window of listening after every 15 second interval of sleep. Tedious and limiting.

* **Wake_Word_**
A paring of "Ghost" and "Kodiak" and programmed to register similar "close enough's". Fairly reliable. 

* **Kill_Word_**
"Checkmate" typically followed by "Ghost". Very reliable.

* **Documenting_**
Logs to Slack with an automatic cool down of 8 seconds + the 15 seconds already in place.

* **Hibernation mode_**
Entering "Hibernation mode" narrows sleep of 15 seconds intervals down to 20 minutes. Giving her a rest when I'm away or asleep. Functional, impractical upon reentry.

These foundational elements are in for solid enhancements... assuming the jump goes well.

### Ghost_v8.0_

### ENH Listening/ Communication_
* **From a 15 second listening cycle to --> "Always on listening" via PyAudio.
* **Enabling conversation windows, she can ask questions to clarify entries and further conversation.**
* **"Always on listening" allows for more range of functionality.**

### ENH Documenting_ *Builds off ENH listening*
* **Complex noting to slack, From her typical response of: "noted to slack" to --> Read back to verify note and prompting to correct/add details.**
* **Reference her memory and slack respiratory to prompt reminders or check progress.**

### ENH Hibernation_
* **Enables Hibernation timer via in place command.**
From "go to sleep" to --> "go to sleep for (list time in half and full hour increments)"
* **Announcement when she wakes.**

### ENH Awareness levels_
* **Enables ghost to recognise and announce her state when prompted. ie: Battery level, if/if not charging, heat level, connection ect.**
* **Voice recognition or adjacent so the ghost knows who is talking to her (typically myself_ grif).**

  *needed due to ghost missing a command and getting into a dialogue about "grif isn't here but we can talk" type of thing... it's strange.*

</details>

<details markdown="1">
<summary><b></b>2026-05-02: v8.0 Fiasco</summary>b></summary>

### Setup installs for v8.0

Pyaudio installed without a hitch via-

* **Hooks_**
pkg install portaudio libffi libbz2 readline
pkg install clang python portaudio libffi openssl libsndfile fftw

* **Pyaudio_**
pip install pyaudio

* **Speechrec_**
pip install speechrecognition

* **pocketsphinx_**
pkg install build-essential cmake swig
pip install pocketsphinx
*the initial install for pocketsphinx failed, pocketsphinx is written in C, so i had to build cmake first 
so that pip could compile the C code into python, then successfully installed Pocket sphinx.*

### Music player_
Attempted to install an apk for Spotify lite via browser, worked, used SAI to actually do the installation.
However, ended up scrapping Spotify due to difficulties with a google handshake (the Samsung s20 FE is Google-less and Spotify lite refused to let me sign in (even after a password change)

Ultimately decided to go with a media player "Metro" from F-Droid for local play, better for the project overall as I want to remove myself and my machine from "Subscription Hell"

### Process of v8.0

Moved the logic from shell scripts (listen.sh) directly into the Python "Brain."
It worked, but the Android Google pop-up was "twitchy."
	
The Hard-Wired Mic Replaced the Google pop-up with a forced 10-second raw recording (termux-microphone-record). 
Created a "Permission Error" because Termux couldn't see the SD card.

The Safe House Moved all files to the internal Termux Home folder to bypass Android permissions. 
Fixed the directory errors, but the mic started "blinking" (instant cut-off).
	
The Mic-Drop Added commands to force-quit any hanging recordings and added "breathing room" pauses. 
Discovered that the Passive Listener (always-on ear) was refusing to let go of the mic.

The Circuit Breaker A total rewrite where the Listener kills itself the moment it hears "Ghost" to free up the mic hardware. 
Logic is solid, but the hardware hand-off is currently too fast for the S20 FE.


Though now she is unresponsive... Though i thought it would make things simpler... may consider reopening the .sh file... everything on one nano might be confusing the system.
Overall, not bad. I think this can work, as several times, ghost's listening window remained open continuously and she was responding. She would notice her "wake word" exceptionally well. The problem is she was only responding with errors and or just looping waiting for a command... But she did speak the errors as if she understood them. Even more interestingly, in the termux window she would type out potential solutions, noticing flaws in the code... This wasn't Termux or python errors like normal... it was ghost. Which is very cool and is the strongest showcase of intelligence from the API thus far... Her model has 70 billion parameters so she should be pretty intelligent and well versed in coding... though her corrections were wrong. Possibly a hallucination, confusion or I'm missing something. 


*It is 4:30 am and my brain is mush, ghost is not very cooperative. Not angry, just tired.*

</details>


<details markdown="1">
<summary><b></b>2026-05-20: Adjustment</summary>b></summary>

### Fresh Eyes, Four Flaws, Freaky Ghost

Took some time away from working on Ghost and ARCIO to catch up the logs, i had a bunch of notes, photos and dates to sift through. Took a while, but I got caught up. over 20 thousand words... I might be a rambler. Then I got distracted again... spending some time messing with the DVD drive that was in the ASUS. I'm working on making a little achiever for DVD's which is very fun and neat but... Ghost has been offline for 20 days and I'm missing my creepy little documentarian. I could have just left her active with the 7.2 script but i really didn't think it'd take so long to get back at it. 

Here we are, back at it! Tonight was more so about getting settled. It's been 18 days away from meddling inside her brain... so i needed a refresher. Thankfully, I have logs! Getting caught up was a bit of a mess even so, the night of may 2nd was a tornado of code and confusion. 

After getting situated, it was back to conflict hunting. Through many headaches and negotiating with Google Gemini, I slowly pieced together potential flaws in that final python script from may 2nd before throwing it back into ghosts head. It's never quite so simple...

Sometimes i get ahead of myself... I have ideas and want them to work and will destroy myself when they don't, pushing and pushing while failing to do the one thing that actually leads to success... stepping back, checking the ego, putting progress on hold and dumbing it all back down so I can relearn and ensure I understand. I cannot fix what I don't understand.


	
### Back to Zero, mental notes_


### Local Components Layout_

* **Pocketsphinx - (STT - Speech-to-text) -** Essentially the EARS, via the python code its only job is to listen for the wake word "Ghost", its a digital tripwire

* **Android - (Termux-TTS - Text-to-speech) -** Essentially the MOUTH, via the python code it projects Ghost's voice out through the S20 FE's speakers.

* **Python - (Script) -** Essentially the NERVES, its simple, robotic, on/off, only focused on getting to then end of the list of code, checking boxes, moving on.

* **Termux-API - (Application programming interface) -** Essentially the MUSCLES, interprets the script into "movement" to interact with the device, toggling the torch mic and speakers on and off.
(termux-microphone-record - Opens the mic gate)
(termux-torch on/off - Toggles the S20 FE physical LED bulb)
(termux-tts-speak "text" - Triggers the android TTS engine to push out via the speakers)

### Cloud Components Layout_

Groq API - (Toolbox) The key set of tools created by groq that allows access to servers that run the LLM to be used remotely, as running a 70 billion parameter LLM on an S20 FE would melt it.

API Key - (Password) The unique "password" that allows access to the Groq API system

Whisper - (ASR - Automatic Speech Recognition) - The translator, a system that transcribes the audio file of my speech into recognizable text for the Llama engine to understand.

Llama 3.3 70B - (AI Engine) - The LLM that Ghost is powered by. With 70 Billion parameters, Ghost is essentially a genius in coding and problem solving. Making her the most overqualified documentarian in existence.

	**API - Application programming interface**
API's are essentially middlemen, though there are different types, in the case of the Ghost Project, there are two at play. 

Termux-API - (Hardware Bridge) - The middleman between python and android, Android OS is locked down tight and sees python as a total stranger and is never going to directly allow it to tell the device what to do, this is were the Termux-API comes in. The application, Termux-API, has all the permissions needed for the Android OS to trust and recognize it. When python needs to "check the box" and say... Turn on the microphone, it tells Termux-API to do just that. Termux-API being trusted by Android OS, requests that that the microphone be turned on and Android is happy oblige.

Groq API - (Cloud Bridge) - The middleman between python and the internet, Groq being a company with thousands of severs and graphics cards don't want users directly to have access to them, so they have API digital windows. The python code is loaded with a specific API key, allowing it access to put in a request from Groq, whom recognizes the key and allows python access to transcribe the audio file into the actual Llama 70B engine. The llama engine needs Whisper to translate that audio file into text so it can actually process it. 
	** **

With my cheat sheet in place and my mind all refreshed, here's some problems we have with the current script.


### Flaws in the code_


### Flaw 001 -	Line Busy_

There isn't any "Checkbox" currently in the python that tells it to close Pocketsphinx... It's always actively listening, keeping the mic open for the wake word, after that it should close so the process can continue down the script and termux-microphone-record can take over and listen for commands and general voice. Since Pocketsphinx isn't being told to shut off and release the microphone, termux-microphone-record just assumes the mic is in use and this kills the process as a whole. This is a simple fix, implementing the del command so python knows to "check the box" and ensure pocketsphinx releases the mic after its job is done so termux-microphone-record can take over.


### Flaw 002 -	Impatient Python_

Python and Pocketshpinx are separated and there for dictated by a single "&" so after Pocketsphinx registers the wake word, python moves on at the exact same time to start the voice capture with termux-microphone-record, essentially everyone is trying to work at the same time, breaking everything. Another simple fix, by replacing "&" with "&&" and creating a more sequential order, everyone gets there time to shine and breathe.

*AND Notes_& vs &&*

Single "&" = "In the background" - Non-sequential 
Double "&&" = "And THEN" - Sequential 


### Flaw 003 -	Clogged.wav_

Every time I speak a command or ask a question to Ghost, my voice is saved as a .wav file, that file is sent to Groq, translated via Whisper and the llama engine is able to process the meaning of it. After that its no longer needed. These need to be temporary as to not confuse, clog and inevitably lag the system. Yet another, simple fix. All that was needed was to add a file system cleanup block to delete the old .wav files before a new recording window is opened. 

Another issue in relation to the .wav files was that if ghost came across a timeout or quite room, that "blank" .wav file would still be sent to groq > Whisper > Llama creating a failure. That .wav file being without the information of voice and largely just static, essentially just the file header at ~40 bytes. Quick patch on this was upping the threshold to "os.path.getsize(path/to/.wav) < 1000" to ensure that any .wav file that's sent, must exceed at least 1000 bytes to avoid failures of this nature. 


### Flaw 004 -	Syntax Error_

Currently the script reads "termux-microphone-record, -d, 10, TEMP_AUDIO" Essentially this means, open the microphone for the default time of 15 secconds and save it to the temporary audio file path... however... this is wrong. Technically the file path is unspecified so the script has no idea where to save the .wav and the "10" following the "-d" is seen as an error becasue is also uspecified... so all this is really doing is killing the process with syntax errors. 
The new script reads "termux-microphone-record -d, -f TEMP_AUDIO.wav, -l, 10" This SHOULD fix this as it now actually is communicating the limit of 10 secconds for the recording window "-l 10" and the file destination "-f TEMP_AUDIO.wav"

### Command KEY_
* **-d = Default settings for the mic**
* **-f = File destination**
* **-l = Limit (in secconds)**
TEMP_AUDIO = Temporary audio file


These fixes, while I'm sure help and move us forward... did not result in a functioning ghost. She was hearing her wake word EXCEPTIONALLY well, but would immediately timeout before i could say a command. Her torch didn't even blink on until minuets after I had to manually force stop termux as a simple "ctrl + C" failed to stop the process. Several minuets after completely killing termux and its adjacent API... her light blinked on solid... this was very eerie as she is just out of my peripheral when I'm at my desk. Her reed glow illuminated my glasses in the dark room and I turned to look in shock. 

Eerie in a dark room at 3am? Absolutely! But its a logical clue... the termux-torch was backed up, not possessed... something is clogging the flow.

</details>
