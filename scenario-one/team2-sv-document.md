# Scenario One: Website Defacing 

On Febuary 17th, 2023, the Ogani website was defaced by the Automatic Red Team. During the attack Automatic Red Team made unauthorized changes to the Ogani website homepage. The disruption interrupted services for over an hour. The attacker only made changes to the Ogani website homepage and promptly left the network. The Security Team has restored the Ogani website and has recommended changes to prevent a similar incident from happening again.  

Image of the defaced website:
![Defaced Website](/scenario-one/img/hacked_website.png)



## Incident Timeline

1. Port Scanning
2. Fuzzing
3. Brute Forced root
4. File Modifications
5. Changing Apache Settings
Port Scanning Occured
Fuzzing
Brute Forced root
Installed nettools 
    - Ran whoami
Created working directory in tmp
Ran wget to download archieve


## Timeline of Events

## What: Website Defacing
### What is Website Defacing?
Website defacing is when an attacked makes unauthorized changes to a homepage. This type of attack is usually carried out by attackers with the intention of causing damage, embarrassment, or making a political statement. Sometimes website defacing is used as a rite of passage for certain hacker groups. 

### What was affected?
One of the webservers was accessed. The webserver that was accessed was CNT-DMZ-Apache2. It was an Apache2 webserver that was hosting the Ogani website. 

## When

## Where

## Recommendations

1. Block external SSH acccess 
2. Enforce keys for SSH access
3. Enable timestamps for Linux terminal commands