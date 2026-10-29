# Redeemer (HTB Starting Point)
**Goal:** find and read data from an exposed Redis server
**Tools used:** nmap, redis-cli
**Steps:** 1) scanned with nmap, 2) found port 6379 open, 3) connected with redis-cli, 4) listed keys, 5) grabbed the flag
**Key concept:** Redis is an in-memory database; with no password, anyone can read it
**What I'd do differently:**
