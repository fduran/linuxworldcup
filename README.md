# Linux World Cup

v1.0

Linux World Cup (LWC) first edition: 2023.

## Main Questions

### What

LWC is a Linux-related online competition.

### Why

A lot of people enjoy Linux challenges and it can be fun. There are coding competitions, why not a Linux one?

### Who

Open to anyone with Internet and a browser.

### When

TBD but aiming at August or September 2023. See Timeline section at the bottom.

### How

<a href="https://sadservers.com/">SadServers.com</a> will be the platform that manages the challenges. See the "Mechanics" section below for details. 

Information like rankings may be posted at <a href="https://linuxworldcup.com/">Linux World Cup</a>.

### How Much

It's free. (I'll be happy if you <a href="https://www.buymeacoffee.com/sadservers">"buy me coffee"</a> to help with hosting costs).

### Prizes

There are no guaranteed material prizes.

## Code of Conduct

I really want to run a nice and fair event.

1. **Be Kind**. AKA don't be a jerk towards other participants or organizers. 

2. **Don't Cheat**. Hard to define all the possibilities but as rules:
- One person per account (registered email in SadServers).
- Do not share any information about the scenarios until after the event is over in all timezones.
- Do not try to manipulate or bypass the services working in the VMs that are needed for the  overall functioning of the system and which are not related to the challenge to solve, like the solution checking agent or a command history logging agent.

## Expectations and Disclaimers

TL;DR "Expect nothing" :-)

LWC and SadServers is run (and financed!) by just this guy (well, I've had help in creating some of the scenarios). I'll try my best but I can always make mistakes (there's a couple issues already in SadSevers scenarios for example). I may have forgotten an "obvious" rule or explanation here and they may change before the competition.

There's also the technical things that can go wrong, like network delays or issues in AWS.

A special pain point is the "Check Solution" script, which may not be perfect and have false positives and false negatives. I may review logs and decide to override the script output and yes this can be subjective.

While the event is running, if there's any system-wide issue or any important notification, I'll use the <a href="https://twitter.com/sadservers_com">SadServers Twitter</a> (erm, X) account. I may not be awake or available at times during the competition; in principle it should run automatically without any manual intervention.

The SLA or QoS of this is "best effort".

## Mechanics, Rules & Miscellaneous Info

### Rules

- Participants must come from a "regular" IP address that can be resolved geographically, that means for example not using a VPN provider, and not coming from a cloud provider server. I consider IP address/geolocation as private information. Contact me if this rule is a problem for you. 

- There's a deadline before the competition starts (see Timeline section below) to change your timezone. Participants must be in their declared timezone and use the corresponding competition times for it.

- Please do not delete or try to delete your shell command history. Command history is not private information and may be publicly disclosed.

### Difference with SadServers

In general the scenarios and VMs will behave the same as any other SadServer scenario and VM with some changes to help running the competition smoothly:
- VMs won't be AWS spot instances but regular on-demand instances.
- Rate limiting is disabled for the event participant.

Also:
- There will be no "clues" provided for competition scenarios (there may be tips but they would be in the description, not under the "Next Clue / Solution" button).

### Event Days and Times

Competition will be done in two different weekends (dates To Be Announced):
- One day for a "qualifier" event (one scenario)
- Another "finals" day for those who pass the qualifier phase, consisting of several scenarios. The final scenarios can be done in any order (ie you don't have to pass one to access another). I'll order them by (my perceived) difficulty: easier to harder.

During both those days there will be three four-hour windows of time to participate, one interval per each of the three time zone groups: Asia-Pacific (UTC+4 to UTC+12), Africa-Europe (UTC-3 to UTC+4), Americas (UTC-11 to UTC-3).

People on Asia-Pacific times will compete on a Saturday and the rest of the world on the following Sunday (next day). People in some locales may find more convenient to use a different time zone area than the continet suggested, for ex in Pakistan or India you can pick early Saturday or late Sunday, or in a Pacific island you can choose Saturday afternoon or Sunday morning.

Please remember you can only use one time zone area and it must be declared in your SadServers LWC account page.

<b>Saturday from 00:00 UTC to 04:00 UTC</b>   
Asia-Pacific

Examples of local times:  
New Dheli 5:30 am - 9:30 am  
Beijing: 8 am - 12 noon
Tokyo : 9 am - 1 pm  
Sydney: 10 am - 2 pm  
  
  
<b>Sunday from 15:00 UTC to 19:00 UTC</b>  
Europe-Africa  

Examples of local times:  
Dakar: 3 pm - 7 pm  
Berlin: 5 pm - 9 pm  
Kyiv: 6 pm - 10 pm  
New Dheli: 8:30 pm - 00:30 pm  
  
  
<b>Sunday from 20:00 UTC to 00:00 UTC</b>  
Americas  

Examples of local times:  
Rio: 5 pm - 9 pm  
New York: 4 pm - 8 pm  
Vancouver: 1 pm - 5 pm
Honolulu: 10 am - 2 pm  



Participants can try the challenges at any time during their window; there's no advantage in doing them starting at an earlier time (it may be disadvantageous to try right when the window opens if there's many people doing it at the same time).


### Teams

I wasn't sure how to do or organize teams when I created the sign up form; if maybe people were interested in pairing up with other people/teams they didn't know. Also I forgot to put a limit to the number of people in a team, and now we may have some large teams which doesn't seem totally fair. Anyways, my bad, for this event I simplified everything and at the end people are either in a team they put in the form or not. If there's only one person with a team name, that's fine, it's an individual participant.

In SadServers you'll be able to edit the team name or delete it if you want to change your status. There's currently no internal software logic regarding teams other than the team name associated with a person's account.

### Scoring

- There are two tracks: individual and teams (ie one ranking for individuals and one for teams).

- Scoring criteria: ranks will be created according to least total time for people/teams in solving all the final scenarios. If one or more scenarios are not solved (not expecting this but just in case), then ranking will be by least time in the solved scenarios (ie, final scenarios have the same scoring weight although they may have different difficulty). 

- The automatic check validation script in the readable ~/agent/check.sh is what decides if a solution is valid or not. In extreme circumstances I'll check the command history manually to validate a solution that didn't pass the check script.

## Scenarios

The challenges or scenarios run on single, bootable VMs, so that restricts the type of issues to present. 

The hard scenarios in <a href="https://sadservers.com/">SadServers.com</a> can give an idea of how the LWC can be.

Not sure how useful this classification is but scenarios can be of the "fix" type (something is broken, troubleshoot and leave in a working state), or the "hack"/"capture the flag" type to uncover a secret or puzzle, or the "do/find" type, like manipulating data for example.

I favor the Debian distribution but other flavors of Linux that run on AWS can be used.

In some scenarios the default user can elevate privileges to superadmin (root), in some scenarios this is disabled.

The tooling (packages) installed in each scenario may be different.

Some programming skills (using a shell script or a popular programming language like Python) are required. Some basic SQL can be needed.

It's not possible to list the Linux components or tools that can show up in the challenges but popular Open Source implementations of key services like web servers, proxy servers, databases (relational or not) and message brokers are fair game.

Containerization (Docker) is an important technology that may be included. Kubernetes is out of scope for this competition. 


## Timeline

- Until 2023-07-31: Deadline to <a href="https://linuxworldcup.com/">sign up for LWC</a>
- Until 2023-08-13: (If your email in the LWC form is not a SadServers account): Deadline to create an account in SadServers with the same email.
- Until ? (TBA): Deadline to optionally update your LWC information in SadServers, namely "alias" (public information to show in rankings, like handle, name or email), "time zone" and "team name".
- ? (TBA) Qualifier challenge: One not-so-hard scenario to pass in order to qualify for the final scenarios. Window of 4 hours (starting at three different times, one per time zone group).
- ? (TBA): Final challenge. Several scenarios. Window of 4 hours (starting at three different times, one per time zone group).

## Questions

Open an Issue here if you think it's useful for other people or contact me (info@sadservers.com for ex) if it's more individual.







