# Redeemer (HackTheBox - Starting Point)

**Date:** 14 Oct 2026
**Platform:** HackTheBox
**Difficulty:** Very Easy

## What the machine covered
A beginner Linux box used to introduce Redis, an in-memory database, and the risks of running it with no authentication configured.

## What I did
1. Connected to the HTB lab network over OpenVPN from my Kali VM.
2. Confirmed the machine was reachable with `ping -c 4 <target_ip>`.
3. Ran a default `nmap` scan first, which came back with all top-1000 ports closed. Re-scanned with `nmap -p- -T4 --min-rate=1000 <target_ip>` to check every port faster, and found port 6379/tcp open, running Redis.
4. Connected to the service with `redis-cli -h <target_ip>`.
5. Confirmed the connection and checked server details with the `info` command, which showed the server was running **Redis 5.0.7**.
6. Selected database 0 with `select 0` and checked how many keys it held using `dbsize` (4 keys).
7. Listed the keys with `keys *`, which returned: `numb`, `temp`, `stor`, and `flag`.
8. Retrieved the flag's value directly with `get flag`.
9. Submitted the flag on the HTB platform.

## What I learned
- Redis is an in-memory database, meaning it stores data in RAM rather than on disk by default, which makes it fast but also means data doesn't persist unless configured to.
- Like Telnet on Meow, Redis can be left completely open with no password, letting anyone who can reach the port read and write data.
- A default nmap scan only checks the top 1000 ports, so a service running on a less common port (like 6379) can be missed unless you scan all ports with `-p-`.
- Redis has its own simple command set (`select`, `keys`, `get`, `dbsize`, `info`) that's quick to learn and very useful for basic enumeration.

## What I'd do differently
I'd run the full `-p-` scan from the start on unfamiliar machines, rather than waiting for a default scan to come back empty first. It would save time.
