# Scenario One: Website Defacing

On Febuary 17th, 2023, the Ogani website was defaced by the Automatic Red Team. During the attack Automatic Red Team made unauthorized changes to the Ogani website homepage. The disruption interrupted services for over an hour. The attacker only made changes to the Ogani website homepage and promptly left the network. The Security Team has restored the Ogani website and has recommended changes to prevent a similar incident from happening again.

### Image of the defaced website:

![Defaced Website](/scenario-one/img/hacked_website.png)

### Artifacts from the Incident:

![Incident Artifact](/scenario-one/img/hacked_artifact.png)

## When

### Incident Timeline

12:33 AM - External IP Address [199.203.100.172] pinged the network.
12:39 AM - Admin Login Failure.
12:44 AM - Outside IP Address Able to Access A Server [172.16.100.22].
12:56 AM - Last firewall reference of external IP address.

#### 1. Alert - Port Scanning

An external IP address [199.203.100.172] conducted reconnaissance on the Organization via a port scan to learn which ports were open and listening, as well as possibly learn about the firewall setup of the system. Once the actor verified an open target port, they proceeded to the next phase of their attack.

![Port Scanning](/scenario-one/img/port-scanning-pwd-guessing.png)

#### 2. Verfied True Positive - SSH Fuzzing

The actor conducted dynamic testing, or fuzzing, on the SSH port [22] to find a vulnerability by injecting random or invalid inputs to cause a fault to occur. This fault resulted in an exploitable unexpected behavior-- in this case granting the actor access to a deeper layer of the network.

#### 3. Begin Incident Investigation - Brute Force Attack

The actor gained root access to the network via a brute force attack. This attack employs the strategy of password guessing commonly used passwords or passwords that seem likely given data gathered about an individual. The password that granted the actor access is considered weak by industry standards: [password here].

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

The webserver CNT-DMZ-Apache2 [172.16.100.22] was accessed by an external IP address [199.203.100.172]. The changes implemented by the external IP impacted the Ogani website, replacing the existing homepage with a png they extracted from an archive they downloaded over the course of their attack.

## Where

The Ogani website is hosted in the apache2 server, near the demararcation point of the organizations network; specifically allocated in the CNT-DMZ Palo Firewall.

![Network Topology With DMZ Outlined with Blue Rectangle](/scenario-one/img/network-topology-dmz.png)

## Recommendations

There are several policies and new technologies that can be implemented to negate a similar attack. The recommendations have been split into two sections Policy and Technical. It is recommended that the following be implemented to ensure that a similar defacing incident doesn't happen again. In addition to preventing another defacing incident, the following recommendations will also reduce the attack surface of the organization overall.

### Policy

#### Block SSH Access from Internet

SSH should not be accessible from outside the internal network. This is how the attacked gained access to the network. All 1services should have Port 22 blocked from the outside. SSH should only be accessible by users connected to the internal network.

#### Enable Timestamps for Commands on Linux-based Servers

During the investigation of the attack. Security Analysts were unable to easily get the time that commands were executed by the attacker. Enabling timestamps in the history command will allow analysts to review commands executed in the shell.

##### References

- GNU: [9.1 Bash History Facilities](https://www.gnu.org/software/bash/manual/html_node/Bash-History-Facilities.html)

#### Disable Default Admin/Root Access from SSH

The default Admin and Root accounts should not be able to access the machines with SSH externally. SSH access with the admin or root accounts need to be disabled. Dedicated accounts for each service should be implemented to make configuration changes. According to the National Institute of Standards and Technology, user access needs to be split into groups. Users who need SSH access should be in a SSH group. The default Admin and Root accounts should not be in the SSH access group.

##### References

- NIST Guide to General Server Security: [4.2.2 Configure OS User Authentication](https://nvlpubs.nist.gov/nistpubs/legacy/sp/nistspecialpublication800-123.pdf)

#### Enforce Password Complexity for Default Admin/Root

The default passwords for admin or root need to be changed to something more complex. Since the default admin and root accounts should not be accessed after the initial configuration of the server, the accounts need to have complex passwords so brute-force attacks can't quickly break them.

##### Password Complexity Rule Recommendations

Below is a list of complexity requirements recommendations:

1. 16-character minimum length
2. At least 1 uppercase letter
3. At least 1 lowercase letter
4. Does not contain company name or related assets
5. Does not describe the system being accessed

##### References

- Infosec Institute: [Password security: Complexity vs. length](https://resources.infosecinstitute.com/topic/password-security-complexity-vs-length/)
- Harvard University: [Complex passwords](https://policy.security.harvard.edu/sa2-complex-passwords)

### Technical

#### Enforce Keys for SSH Access

Users who require SSH access to servers cannot use their password to authenticate their access. SSH access from internal networks need to use keys for authentication. Only users who need to use SSH to configure or maintain servers and services on the network need SSH keys. One benefit to having SSH keys is that users do not need to manually enter their log-in credentials to access everything.

##### SSH Key Pair Recommendations:

Below are recommendations for which algorithms should be used when generating key pairs.

1. Newer Systems:
   > System administrators should generate Ed25519 key pairs.
2. Older Systems:
   > RSA should be used.

##### References

- BeyondTrust: [SSH Key Management Overview & 10 Best Practices](https://www.beyondtrust.com/blog/entry/ssh-key-management-overview-6-best-practices)
- RedHat: [How to configure key-based authentication for SSH](https://www.redhat.com/sysadmin/key-based-authentication-ssh)
- ArchLinux Wiki: [SSH keys](https://wiki.archlinux.org/title/SSH_keys)

#### Implement Fail2Ban

Fail2Ban is a simple utility that scans log files and bans IPs that show too many password failures. This utility is a way to easily reduce the attack surface on servers that need to have SSH access. If an attacker gains access to a computer within the company network, it will make it more complicated to brute force a user account's password. Fail2Ban's popularity means that many guides exist for System Administrators to help them implement the utility.

##### References

- Fail2Ban: [Fail2ban Wiki](https://www.fail2ban.org/wiki/index.php/Main_Page)

#### Implement Uncomplicated Firewall for Apache Servers on the DMZ Subnet

Uncomplicated Firewall (or UFW for short) is a utility to manage firewalls with iptables on Ubuntu and Debian distributions of Linux. Every service should not be accessible from the internet on the servers running Apache. This will reduce the attack surface on critical business websites. For example: Use the default UFW rules for Apache when enabling UFW on the Apache servers.

##### References

- UFW: [UFW Repository](https://launchpad.net/ufw)
