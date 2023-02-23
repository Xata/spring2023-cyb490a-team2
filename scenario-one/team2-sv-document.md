# Scenario One: Website Defacing

On Febuary 17th, 2023, the Ogani website was defaced by the Automatic Red Team. During the attack Automatic Red Team made unauthorized changes to the Ogani website homepage. The disruption interrupted services for over an hour. The attacker only made changes to the Ogani website homepage and promptly left the network. The Security Team has restored the Ogani website and has recommended changes to prevent a similar incident from happening again.

Image of the defaced website:
![Defaced Website](/scenario-one/img/hacked_website.png)

## Incident Timeline

### Alert

#### 1. Port Scanning

![Port Scanning](/port-scanning-pwd-guessing.png)

#### 2. SSH Fuzzing

#### 3. Brute Force Attack

Gained root access

### Investigation

#### 4. Installed nettools - Ran whoami

#### 5. File Modifications

Created working directory in temp file - anyone can read/write.

#### 6. Ran wget to fetch archive

#### 7. Changed Apache Settings

Extracted png from archive, set as the homepage for ogani.com.

### Containment, Eradication, Remediation

#### 8. Checked Firewall

#### 9. Restored Website

#### 10. Lessons Learned

The Security Team has compilied a number of policy and technical improvements to implement that will improve organizational security, reduce cyber vulnerability, and potentially reduce the impact of future cyber incidents. These are listed under "Recommendations" below.

## What: Website Defacing

### What is Website Defacing?

Website defacing is when an attacked makes unauthorized changes to a homepage. This type of attack is usually carried out by attackers with the intention of causing damage, embarrassment, or making a political statement. Sometimes website defacing is used as a rite of passage for certain hacker groups.

### What was affected?

One of the webservers was accessed. The webserver that was accessed was CNT-DMZ-Apache2. It was an Apache2 webserver that was hosting the Ogani website.

## When

### Timeline of Events

## Where

## Recommendations

1. Block external SSH acccess
2. Enforce keys for SSH access
3. Enable timestamps for Linux terminal commands
