# SoftAgents-Platoon

-----------------------------------------------------------------
SoftAgents-Platoon
-----------------------------------------------------------------
SoftAgents-Platoon is a framework for assessing the security of CACC platons.

SoftAgents has been introduced by the following article submitted to VNC 2020:

Yuri Gil Dantas, Vivek Nigam, and Carolyn Talcott: 
A Formal Security Assessment Framework for Cooperative Adaptive Cruise Control

-----------------------------------------------------------------
Purpose of this README file
-----------------------------------------------------------------
This README file provides instructions on how to reproduce the results presented in the article. 

-----------------------------------------------------------------
Setup
-----------------------------------------------------------------
The instructions below have been tested in a Linux operating system (Ubuntu 18.04 desktop 64-bit).

-----------------------------------------------------------------
Dependencies
-----------------------------------------------------------------
- Maude3
(http://maude.cs.illinois.edu/w/index.php/Maude_download_and_installation)

-----------------------------------------------------------------
Running Injection of False Msgs against Follower
-----------------------------------------------------------------

(0) Open your terminal and go to {REPOSITORY-PATH}/Models/platooning/

(1) Load Maude 
$ maude

(2) Load 'test-intruder.maude' 
Maude> load test-intruder.maude

(3) Run the search command to look for a crash between 2 vehicles
Maude> search [1] in TEST-INTRUDER : asysint(70, 1) =>* iasys such that crash(iasys) = true .

-----------------------------------------------------------------
Running Injection of False Msgs against Joining Vehicle
-----------------------------------------------------------------

(0) Open your terminal and go to {REPOSITORY-PATH}/Models/platooning/

(1) Load Maude 
$ maude

(2) Load 'test-intruder-join.maude' 
Maude> load test-intruder-join.maude

(3) Run the search command to look for a crash between 2 vehicles
Maude> search [1] in TEST-INTRUDER : asysint(70, 1) =>* iasys such that crash(iasys) = true .

-----------------------------------------------------------------
Running Injection of Emergency Brake
-----------------------------------------------------------------

(0) Open your terminal and go to {REPOSITORY-PATH}/Models/platooning/

(1) Load Maude 
$ maude

(2) Load 'test-intruder-emergency.maude' 
Maude> load test-intruder-emergency.maude

(3) Run the search command to look for a crash between 2 vehicles
search [1] in TEST-INTRUDER-EMERGENCY : asysint(70, 1) =>* iasys such that fakeEmergency(iasys) and crash(iasys) = true .

-----------------------------------------------------------------
Running Blocking Legitimate Emergency Brake Msgs
-----------------------------------------------------------------

(0) Open your terminal and go to {REPOSITORY-PATH}/Models/platooning/

(1) Load Maude 
$ maude

(2) Load 'test-intruder-drop-emergency.maude' 
Maude> load test-intruder-drop-emergency.maude

(3) Run the search command to look for a crash between 2 vehicles
search [1] in TEST-INTRUDER-DROP-EMERGENCY : asysint(20, 0) =>* iasys such that crash(iasys) and noLogs(iasys) = true .

-----------------------------------------------------------------
Running Slow-Injection of False Msgs against Follower
-----------------------------------------------------------------

(0) Open your terminal and go to {REPOSITORY-PATH}/Models/platooning/

(1) Open 'load.maude'. Uncomment Lines 17 to 33. Comment out Lines 39 to 55

(2) Load Maude 
$ maude

(3) Load 'test-intruder-slow-injection.maude' 
Maude> load test-intruder-slow-injection.maude

(4) Run the search command to look for a crash between 2 vehicles
search [1] in TEST-INTRUDER-SLOW-INJECTION : asysint(30, 16) =>* iasys such that crash(iasys) = true .


