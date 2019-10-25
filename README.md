# UbiLab - Escape Room

![ubilab-escape-banner](/doc/img/ue-banner4.png)

> You are a team of special agents. Your mission, should you choose to accept it, is to steal the latest research results of lab area 051. You find yourself in the lab, the artificial intelligence controlling the room has gone rogue, and locked you in. You have one hour to convince the AI to open the doors and let you escape with the research results, before you will be captured by special forces.

**Welcome to the Ubiquitous Lab course WS 19/20**

Each group should work independently on their project to allow independent progress and individual grading. However, to accomplish a fully working escape room you obviously have to work together with other groups (or at least with the operator group) in order to embed your module(s) into the overall project. Therefore, we have defined some guidelines and restrictions in order to minimize the overall integration process and to maximize modularity and portability:
1. Use a version management system - more precisely, you should use git.
2. Wired and wireless communication from your module(s) to the server has to be implemented using TCP. Your module(s) should act as a TCP client(s).
3. For each message to/from the server, JSON encoding should be used. The protocol will be designed/specified by group 1, so you should communicate to them what you need/offer.
4. Do not use a sledgehammer to crack a nut - do you really need the processing power of a full blown Raspberry Pi or is a tiny microcontroller sufficient?

- [UbiLab - Escape Room](#ubilab---escape-room)
  - [Story (to be changed)](#story-to-be-changed)
- [Teams](#teams)
  - [Team Overview](#team-overview)
  - [Team 1 - Operator](#team-1---operator)
  - [Team 2 - Environment](#team-2---environment)
  - [Team 3 - Mission Briefing](#team-3---mission-briefing)
  - [Team 4 - First Door](#team-4---first-door)
  - [Team 5 - Safe](#team-5---safe)
  - [Team 6 - Prototype](#team-6---prototype)
  - [Team 7 - Second Door](#team-7---second-door)
  - [Team 8 - AI Server](#team-8---ai-server)
- [How to use this repository](#how-to-use-this-repository)

## Story (to be changed)
You are a team of special agents charged with stealing a highly classified prototype from a secret laboratory (lab 051) at the University of Freiburg. We know that the lab is secured with a state-of-the-art smart security system called STASIS (STate-of-the-art AsSIStant). STASIS is an AI controlling the room infrastructure and interacts with the inhabitants. You will need to outwit STASIS to access the prototype construction plans, which threatens to destroy the world.

**Level 1** *In front of the lab entrance* the team receives a communication device. The device tells the team about it's upcoming mission about stealing and transmitting the prototype construction plans from within the lab. The device will self-destruct after delivering the message. You will have one hour to steal the prototype and escape the lab unharmed.

**Level 2** *Antechamber, lobby-like with table and absent security officer*. The team has to pass through the first door to enter the lab. It is unclear what kind of security mechanisms the team is up against.

**Level 3** *Inside the Lab, Tables with computers and lab material...*. Unbelievable, the prototype is in clear sight, however it is locked inside a transparent compartment. The team has to figure out how to open the compartment (maybe there are hints in logfiles, in notebook lying around, or STASIS can be asked). There are multiple puzzles to solve. One thing is for sure, the entrance needs to be closed and the team must be in the room before the compartment can be opened.

**Level 4** *Inside the Lab, the prototype opens*. As soon as the team touches the prototype, an alarm sounds and STASIS announces a lock-down of the room and asks the team to return the prototype. Once returned the alarms turns off but the door stays closed. STASIS will also interfere with the team's ability to move, by turning off the lighting etc. The team needs to switch the prototype with a similar object to fool STASIS. Once done, the team needs to locate the central server (in the next room) and enter.

**Level 5** *Inside the Lab, open the server room*. The team has to decouple the control of the door from STASIS (manual override), for example by finding the hidden wiring the wall. Afterwards the lock of the door has to be broken (z.B. biometric hacking, e.g. finding a staff badge, RFID or similar).

**Level 6** *Serverroom, technical, some PC to transmit the prototype, home of STASIS*, The team has to transmit a copy of the prototype construction plans (e.g. stored on a floppy disk) to the client. Another puzzle has to be solved.

**Level 7** *Serverroom, escape*. STASIS has gone rogue and will not let you leave. You somehow have to outwit or shut down STASIS to let you leave and open the lab room for you to escape before Arnold Schwarzenegger will be baaaaaack.

https://github.com/orgs/ubilab-escape/projects/2


# Teams
 
## Team Overview
| Group   | Mission                          | Members     |  Supervisors         | Main Repo                                                             |
| :-----: | -------------------------------- | ----------- |  ------------------- | -----------                                                           |
| 1       | Operator Room                    |             |  Phil, Basti, Sven   | [operator](https://github.com/ubilab-escape/operator)                 |
| 2       | Environment & AI                 |             |  Ben, Basti          | [environment](https://github.com/ubilab-escape/environment)           |
| 3       | Mission Briefing                 |             |  Ben, Phil           | [mission-briefing](https://github.com/ubilab-escape/mission-briefing) |
| 4       | Both Doors & First Door Puzzle   |             |  Ben, Marc, Chris    | [first-door](https://github.com/ubilab-escape/first-door)             |
| 5       | Safe & Puzzles                   |             |  Sven, Marc          | [safe](https://github.com/ubilab-escape/safe)                         |
| 6       | Prototype & Puzzles              |             |  Chris, Basti        | [prototype](https://github.com/ubilab-escape/prototype)               |
| 7       | Second Door Puzzles              |             |  Phil, Marc          | [second-door](https://github.com/ubilab-escape/second-door)           |
| 8       | AI Server & Puzzles              |             |  Sven, Chris         | [ai-server](https://github.com/ubilab-escape/ai-server)               |


## Team 1 - Operator
With great power comes great responsibility. No pressure.

Your main task is to create your own centralized escape room management system. Through this system, all other components in the room are connected and controlled, and the logic of the escape game is implemented.

The system should:
- receive tcp messages from various components in the room and process them
- implement a json protocol for these messages that defines the communication between components
- implement the game logic, i.e. what events trigger which actions, what are the initial settings, what are the win conditions, etc…
- be able to run automatically if everything goes according to plan
- give the possibility to manually interact with and intervene in the game’s process, if the need arises
- have some kind of UI that gives an overview of the room and components, and their status

You are largely free to use whatever tools are necessary to implement such a system, but be aware that the other groups are hugely dependent on this and you should communicate with them extensively to meet their needs and/or define requirements for them, where applicable.

Some pointers to possible systems/tools/software that you may use:
- Self-built web server that processes all communication in the backend (e.g. using Django/Python, Ruby on Rails, Node.js, ...), and provides a frontend for UI and possibly an API (e.g. using native HTML/JS/CSS or frameworks like Angular, React, Ionic, ...)
- ROS http://wiki.ros.org/
- MQTT http://mqtt.org/
- ...

There are some commercially available escape room management systems that can be found online. You are encouraged to look into these for inspiration.

As a secondary task, you should integrate some cameras into the rooms and somehow display the video in your management system. We already provide some ESP based mini cameras with case (https://m5stack.com/products/esp-32-camera-psram).

## Team 2 - Environment
The group “Environment + AI” has to work closely with the operator group and your project is more or less three fold.

1. You should develop the infrastructure to change the lighting condition in the room(s). The room might glow in a matrix/MI green look at first. If the alarm goes off, you might flood the room with red warning light. You could use e.g. RGB light strips (WS2812B) or RGB light bulbs (Ikea TRADFRI with zigbee protocol). Furthermore, if the countdown goes off, a large 7 segment display should display the countdown. Feel free to add other light gimmicks to the scene.
2. Have you ever seen an alarm with only flashing light!? Typically it is combined with loud noise or a voice reading the remaining countdown e.g. each minute. That’s exactly what we want! Equip each room with at least one speaker. This speaker might feature a simple headphone jack to play sounds or a more advanced streaming interface (e.g. Bluetooth or DLNA).
3. Your last and potentially hardest task is to develop a speech response system. The escape room participants should be able to ask questions to an AI system like: “How long do we have?”, “What is the next step”, “Give us a clue”. The system should respond with spoken text through your own speaker setup. 

Things to look at if you want to develop your own text to speech and speech recognition system: CMU PocketSphinx, Python module SpeechRecognition, Mozilla DeepSpeech, Google Speech API. 
Things to look at if you want to enhance an already existing smart speaker:
- https://developer.amazon.com/docs/custom-skills/understanding-custom-skills.html 
- https://lifehacker.com/how-to-build-your-own-amazon-echo-with-a-raspberry-pi-1787726931 
- https://support.google.com/googlenest/answer/7194656?co=GENIE.Platform%3DDesktop&hl=en 
 
All developed modules should work independently (countdown display, lighting, sound, AI) but might also work together. e.g. countdown read automatically each 5 min. lighting (red flashing) can be reset by AI speech command, etc.

## Team 3 - Mission Briefing
The group “Mission Briefing” should be familiar with the movie Mission Impossible. Your task is to give participants a quick overview about the task in the escape room. The participants will therefore be handed a device (which you develop) which provides them information in form of e.g. speech, text, pictures, video, or a combination of these. This device should “self destruct” after the information is provided.

Things you could take a look at:
- Google Glass, ESP32, I2S, electric cigarette atomizer, (how do rc planes produce smoke).
- http://valkyriestudios.net/making-a-mini-fog-machine/ 
- https://www.instructables.com/id/Self-Destructing-Message/ 

In reality, it should not self destruct, you need a secret reset mechanism such that it can be reused. Make sure to provide a modular way to allow different missions to be presented with your machine. 

## Team 4 - First Door
Your task is threefold.:
1. Construct doors which can be opened and closed automatically. They may be sliding or standard doors. Please make sure that no one can get hurt, if he or she is stuck in between. Ideas:
   - Sliding door with linear bearings and ballscrew/belt automation
   - Swinging door with linear motor automation
   - Emergency-Stop via light barrier/pressure sensor 
2. Think about a puzzle for the entry room. The main room is locked. It is up to you how the door lock is realized, either via a simple passcode lock or a more advanced locking mechanism (RFID, biometric, etc.), or by interacting with Statis. The participants should solve at least one puzzle to open the door to the lab.
3. When the participants have entered the lab, one requirement to continue is that all team members are inside the lab and that the door to the entry room is closed (because it will be locked during the alarm). It is your task to create a puzzle which forces all team members to be present in the lab and which can be used as trigger to close the door. Ideas:
   - Dead-Man-Switches - All team members need to press a button at the same time
   - Position-Tracking via cameras/DecaWave

## Team 5 - Safe
Your task consists of 2 subtasks:
1. You should create a safe-ish storing compartment which can be used to safely store the prototype/research results. The participants should be able to spot the prototype/research results inside the safe but they should not be able to gain access to it before they solved a couple of puzzles. Therefore, at least a plexiglas top-plate should be integrated and some kind of an automatic, remote-controllable lock is needed. Ideas:
   - Build a simple box with a plexiglas-top that can be locked with a servo/magnetic-lock
   - Build a compartment inside a table

2. The participants need to solve multiple puzzles to open the aforementioned safe. Your second task is to create these puzzles. You should integrate the whole room in the puzzles. You could also use the “AI” which will be created by group 2. You could also think of directly integrating one of the puzzles in the safe from subtask #1. Ideas:
   - Find three USB-Drives and insert them in the right order in the safe
   - Solve a question which is asked by the AI with things inside the room (e.g. a mathematical equation)
   - Move some switches in the right position
   - Hack something on a wall-terminal

## Team 6 - Prototype
Your task is to implement a top secret “prototype” object into the escape room. The prototype is the main objective that the players will search for when starting into the room. The default idea for this is a 3.5’’ floppy disk, placed into the safe built by group 5. Immediately when the disk is removed from the safe, an alarm is triggered. You should implement a scale that detects if the disk or another object of comparable weight is placed on it, and that sends its status to the server to trigger the alarm event.

Secondly, you should implement some puzzle(s) that process the prototype in some way. For example, the disk could be put into a floppy disk drive in the third room, and through some mechanic or puzzle, an upload of the saved data is started (obviously the floppy disk is a futuristic high-tech data storage device, so the only way to access the petabytes of data stored on it is via the server machine built by group 8). You could use an actual floppy drive for this and read actual data, or just simulate this via some mechanism.

## Team 7 - Second Door
Your task is to create different puzzles which have to be solved by the participants to open the door to the server-room. You should integrate the whole room in the puzzles. You could also use the “AI” which will be created by group 2. To finally open door you build some kind of a (biometric) lock directly at the door. Ideas:
- A hidden fuse-box inside which some rewiring had to be done to decouple the door-lock from the AI
- A biometric door-lock which has a little face-detection that can be opened with a picture on a staff badge (found somewhere in the lab)
- A biometric door-lock which has a fingerprint reader. One of the participants can open the lock since his/her fingerprint was secretly taken before. 

## Team 8 - AI Server
Your task is to build room three: the server room. This is the “brain” of the AI which needs to be destroyed at the end. So you need to build some servers:

These just need to look like servers but not really work. However the interface for reading and uploading the prototype have to work. So you should communicate with group 6. They might use a 3.5 floppy disc or something else. The participants need to verify the prototype and upload it somehow.
After that they need access to the “servers” of the AI. Now they have to solve some puzzles that you need to implement to gain access to them. Also there should be an option to shutdown or start the self destruction of the AI, maybe the participants need the admin password (42) to initiate the shutdown/self destruction. So you need to communicate with group 2 who is responsible for the AI.
After the AI is destroyed all doors needs to open and the timer should stop so you have to arrange this with the other groups.


# How to use this repository

https://github.github.com/training-kit/downloads/submodule-vs-subtree-cheat-sheet/

TODO
