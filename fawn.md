# Fawn (HackTheBox - Starting Point)

**Date:** 14 Oct 2026
**Platform:** HackTheBox
**Difficulty:** Very Easy

## What the machine covered
A beginner Linux box used to introduce FTP (File Transfer Protocol) and the risks of allowing anonymous logins.

## What I did
1. Connected to the HTB lab network over OpenVPN from my Kali VM (already connected from the earlier machine).
2. Confirmed the machine was reachable with `ping -c 4 <target_ip>`.
3. Scanned the machine with `nmap <target_ip>` and found port 21/tcp open, running FTP.
4. Connected with `ftp <target_ip>`.
5. Logged in using the username `anonymous` with a blank password, which was accepted (response code `230 Login successful`).
6. Listed the available files with `ls` and found a single file, `flag.txt`.
7. Downloaded it with `get flag.txt`, exited the FTP session with `exit`, then read the file locally with `cat flag.txt`.
8. Ran `nmap -sV <target_ip>` afterwards to check the exact service version, which showed **vsftpd 3.0.3** running on **Unix**.
9. Submitted the flag on the HTB platform.

## What I learned
- FTP (File Transfer Protocol) runs on port 21 by default and is used to transfer files between a client and server.
- FTP sends data, including login credentials, in plain text, the same core weakness as Telnet. SFTP (built on SSH) is the secure modern alternative.
- "Anonymous" is a standard FTP username that, when allowed by the server, lets anyone log in without a real account.
- The `-sV` flag on nmap is needed to see service version numbers, a plain `nmap <ip>` scan only shows the port and service name, not the version.

## What I'd do differently
I'd run `nmap -sV` as part of my first scan on every machine from now on, rather than as a follow-up step, since version information is useful early and costs little extra time.
