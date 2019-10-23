# UbiLab - Escape Room
> You are a team of special agents. Your mission, should you choose to accept it, is to steal the latest research results of lab area 051. You find yourself in the lab, the artificial intelligence controlling the room has gone rogue, and locked you in. You have one hour to convince the AI to open the doors and let you escape with the research results, before you will be captured by special forces.

**Welcome to the Ubiquitous Lab course WS 19/20**

Each group should work independently on their project to allow independent progress and individual grading. However, to accomplish a fully working escape room you obviously have to work together with other groups (or at least with the operator group) in order to embed your module(s) into the overall project. Therefore, we have defined some guidelines and restrictions in order to minimize the overall integration process and to maximize modularity and portability:
1. Use a version management system - more precisely, you should use git.
2. Wired and wireless communication from your module(s) to the server has to be implemented using TCP. Your module(s) should act as a TCP client(s).
3. For each message to/from the server, JSON encoding should be used. The protocol will be designed/specified by group 1, so you should communicate to them what you need/offer.
4. Do not use a sledgehammer to crack a nut - do you really need the processing power of a full blown Raspberry Pi or is a tiny microcontroller sufficient?

 
## Team Overview
| Group | Mission                   | # Members | Supervisors       |
|:-----:|---------------------------|:---------:|-------------------|
|   1   | Operator Room             |     3     | Phil, Basti, Sven |
|   2   | Environment & AI          |     3     | Ben, Basti        |
|   3   | Mission Briefing          |     2     | Ben               |
|   4   | Both Doors & First Puzzle |     2     | Ben, Marc, Chris  |
|   5   | Safe & Puzzles            |     2     | Sven, Marc        |
|   6   | Prototype & Puzzles       |     2     | Chris, Basti      |
|   7   | Second Door Puzzles       |     2     | Phil, Marc        |
|   8   | AI Server & Puzzles       |     2     | Sven, Chris       |
