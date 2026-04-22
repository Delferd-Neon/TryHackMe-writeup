# Takeover - (Enumerate to spawn_)
<!--
Source - https://stackoverflow.com/a/14747656
Posted by Tieme, modified by community. See post 'Timeline' for change history
Retrieved 2026-04-21, License - CC BY-SA 4.0
-->

<img src="https://github.com/Delferd-Neon/TryHackMe-writeup/blob/main/TakeOver/Images/takeoverr.png" alt="drawing" style="width:200px;"/>

In this challenge we will revolve around subdomain enumeration to solve this challenge.  

Before begin make sure to add your target IP with `futurevera.thm` domain, on `/etc/hosts` file so it can be reachable.  

As it sounds that it is an subdomain enumeration challenge then we don't need to scan the target with nmap we can start with `ffuf` directly. We have explored the web-page, source, Js but nothing found interesting for us. Now let's begine our Fuzzing.   

For fuzzing the subdomains of futurevera.thm we use `ffuf`("Fuzz Faster U Fool"). It is a web fuzzer written in Go, primarily used by penetration testers and bug bounty hunters to discover hidden directories, files, parameters, and virtual hosts.  

### Enumerating Sub-Domains  

Let's use ffuf to discover subdomains by this command:  

```ffuf -w /usr/share/seclists/Discovery/Web-Content/raft-large-directories.txt -u http://MACHINE-IP/ -H "Host: FUZZ.futurevera.thm" -fs 0```  
| Flags | Descripton |
|-------|------------|
| `-w`  | Used to provide wordlists |
| `-u` | Provide the URL of of machine |
| `-H` | Header|
| `-fs`| Filter HTTP response size|

