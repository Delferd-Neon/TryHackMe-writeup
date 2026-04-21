# Takeover - (Enumerate to spawn_)
![image](https://github.com/Delferd-Neon/TryHackMe-writeup/blob/main/TakeOver/Images/takeoverr.png)
In this challenge we will revolve around subdomain enumeration to solve this challenge.
Before begin make sure to add your target IP with `futurevera.thm` domain, on `/etc/hosts` file so it can be reachable.
For fuzzing the subdomains of futurevera.thm we'll use `ffuf`("Fuzz Faster U Fool"). It's an web fuzzer written in Go, primarily used by penetration testers and bug bounty hunters to discover hidden directories, files, parameters, and virtual hosts.
