# Scavenger Hunt

During the scavenger hunt, the team was provided with a set of instructuctions to follow in order to find the required items

Items to find:

- Firewall rules
  The firewall rules are placed under policies -> then security
  - under said policies, a question that arised was 'what is one thing you would change in regard to access that users have to the internet?'
    Under the firewall rules, the users are able to access http_proxy sites, and there is no rule stating that when a user wants to access a non-secure site that a warning should be displayed. That is one thing I would change, display a warning upon attempting to access an http_proxy site.
- Rule specifics
  The log parameter for the sessions is set to log at the end. These sessions can be found under 'activity logs' or 'dashboard'
- Offenses in System
  Offenses triggered in the system were:

  - Account failed to log on
  - Domain controller failed to validate the credentials for an account
  - An account failed to log on

- Purpose of QRadaris to log and trigger alerts or intrusions in a system, it also establishes and defines rules

## The Setup

During the Scavenger Hunt on the Cybersecurity Range, we familiarized ourselves with the range, tools, and technologies that we'll be using throughout the Spring semester. The Scavenger Hunt was designed for us to explore the environment within the range. We were given a list of tasks to complete to learn more about the tools in Cybersecurity.

## The Network Map

A cool feature of the Range is that we were provided with a network map that provided with the services and username and passwords for us to access all the different servers. Most networks don't have this, and a lot of businesses forget to write down critical information that could aid Cybersecurity professionals in their hunt for incidents. 

## Palo Alto Firewall

![Palo Alto Firewall Logs](/scavenger-hunt/img/scavengerHunt_Firewall_logs.png "Palo Alto Firewall Logs")

The Palo Alto Firewall is a place for rules to be set and manage the flow of network traffic in and out of the organization's network.

![Palo Alto Firewall Ping Query](/scavenger-hunt/img/scavengerHunt_Firewall_pingQuery.png "Palo Alto Firewall Ping Query")

The firewall is able to track ICMP requests on the network.

## Qradar

Qradar is a Security Information and Event Mangement (SIEM) system. SIEM systems are used for a number of functions, the four most common being log collection, event correlation, alert generation, and incident response. These functions serve to facilitate proactive monitoring and protecting of an organization's network and systems from security threats.

![Qradar image](/scavengerHunt_qradar_00.png)

In the scavenger hunt, we were tasked with going to a specific IP address and tracking it in the log. Due to how the network was setup, we were not able to find the traffic in the SIEM's log because it was not connected to that host.

### Qradar Offenses Tab

## Domain Controller

Domain Controllers are a nifty way for organizations to manage users that have access to technology. Due to licenses, only one person was able to access the Domain Controller at a time.

![Domain Controller](/scavenger-hunt/img/scavengerHunt_domainController_locateUserGroups.png "Domain Controller")

You can manage users and change their passwords or unlock their accounts:

![Domain Controller User Password](/scavenger-hunt/img/scavengerHunt_domainController_locateUserChangePasswod.png "Domain Controller User Password")

## DMZ Firewall

A DMZ is a part of the network that has special rules for services that are exposed to the internet. 

![DMZ](/scavenger-hunt/img/scavengerHunt_dmzFirewall_adminPage.png "DMZ Firewall")

## Zenoss

## Snort

## Mail Server

## Tools

## Hidden Files
