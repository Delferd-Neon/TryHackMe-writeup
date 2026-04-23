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
<img width="1656" height="700" alt="ffuf output" src="https://github.com/user-attachments/assets/1cd055cb-b3b9-46ef-b4b5-58f03a7a6201" />    


We have found 2 new subdomains, add them into `/etc/hosts` file to access it.  

Nothing find interesting on these subdomains, they points to the homepage of site.  

After some enumeration and techniques i have found that, what if we use `HTTPS` rather `HTTP`. So now i'm trying to enumerate through https by changing target url `https://MACHINE-IP/`.  

<img width="1760" height="690" alt="Screenshot 2026-04-23 091757" src="https://github.com/user-attachments/assets/b36eac54-b833-4093-98a4-6d425a09bd03" />


Here we also find two different subdomains, let's add them into hosts file and access it.  

Now check it's certificate by going your browser `view certificate`, and notice that DNS name have some another subdomain.  

<img width="460" height="350" alt="Screenshot 2026-04-23 100838" src="https://github.com/user-attachments/assets/94acd9bb-c691-4258-81ec-4c2544d7a57f" />  

You won't get your flag by HTTPS, go for HTTP then you get your flag.  

<img width="892" height="52" alt="image" src="https://github.com/user-attachments/assets/1c9beda4-2f14-452b-914b-ea1a2436419d" />


### Thank you !
