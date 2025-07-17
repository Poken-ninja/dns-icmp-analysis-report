# Dns-icmp-analysis-report
# DNS and ICMP Network Traffic Analysis

This repository contains my analysis of a basic cybersecurity incident involving DNS queries and ICMP error messages. This was part of a beginner-level exercise to help understand how network protocols behave when a service is down or unreachable.

## What this project is about

I reviewed a packet log where a DNS request was sent using UDP, and the system responded with an ICMP "Port Unreachable" error. This helped me learn how different protocols (like UDP and ICMP) interact and how such logs can reveal service-level issues, like DNS outages.

## Key Observations

- UDP is used by DNS for fast, connectionless communication.
- ICMP is used to report errors or network issues.
- The DNS request was sent to port 53 but the response indicated that the port was unreachable.
- This suggested that the DNS service was either not running or not reachable on the target server.

## Steps I followed

1. Reviewed the DNS and ICMP traffic entries in the network log.
2. Noted the time when the DNS query was sent.
3. Identified the ICMP reply that reported the error.
4. Connected the two events to determine the likely cause.

## Tools Used

- Basic network log file
- Knowledge of common protocol ports and ICMP types
- Manual analysis (no tools like Wireshark used for this exercise)

## What I learned

- How to identify UDP and ICMP traffic patterns in network logs.
- That ICMP "Port Unreachable" errors often follow failed UDP requests.
- The significance of port 53 in DNS communication.
- How a simple log entry can reveal a deeper issue like a service outage.

## Next steps

In future exercises, I want to:

- Practice with real-time packet capturing using Wireshark
- Investigate TCP-related incidents
- Understand how DNS poisoning or spoofing differs from a simple service outage

## About me

I'm a BTech IT student currently learning the basics of networking and cybersecurity. This is one of my first attempts at analyzing traffic and writing about what I understood. Feedback is welcome.
