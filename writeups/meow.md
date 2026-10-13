# Meow (HackTheBox - Starting Point)

**Date:** 13 Oct 2026
**Platform:** HackTheBox
**Difficulty:** Very Easy

## What the machine covered
A beginner Linux box used to introduce the Telnet protocol and the risks of default/blank credentials.

## What I did
1. Connected to the HTB lab network over OpenVPN from my Kali VM.
2. Confirmed the machine was reachable with `ping -c 4 <target_ip>`.
3. Scanned the machine with `nmap <target_ip>` and found port 23/tcp open, running telnet.
4. Connected with `telnet <target_ip>`.
5. Logged in as `root` with a blank password — no credentials were required at all.
6. Found `flag.txt` in root's home directory with `ls`, then read it with `cat flag.txt`.
7. Submitted the flag on the HTB platform.

## What I learned
- Telnet sends everything, including login attempts, in plain text, so anyone watching the network traffic could read it.
- A system can be fully open if it's left with a blank or default root password. This is a very common real-world misconfiguration.
- Nmap's default scan is enough to spot an obviously risky open service.
- The command `find / -name filename 2>/dev/null` is useful when a file isn't where you expect.

## What I'd do differently
Next time, I'd capture the Telnet session in Wireshark to see the plaintext login in the packet capture, to make the "Telnet is insecure" point concrete rather than just something I read about.
