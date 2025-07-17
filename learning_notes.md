# DNS & ICMP Investigation – My Learning Notes

## What Happened?

Users weren’t able to access a certain website. I checked the packet logs and found that a DNS request was made over UDP, and shortly after, an ICMP message came back saying “Port Unreachable.” This helped me understand how these protocols interact when something goes wrong.

## Timeline of What I Observed

| Time         | What I Saw                                                                |
| ------------ | ------------------------------------------------------------------------- |
| 13:24:32.192 | A device tried to contact a DNS server using UDP (on port 53)             |
| few ms later | Got an ICMP error saying “Port 53 unreachable”                            |
| After that   | Realized the DNS server wasn’t responding — the service was probably down |

## What I Understood About the Protocols

**UDP:**

* It's a fast and simple protocol that doesn’t need a connection.
* DNS usually uses UDP to send small queries.
* There’s no built-in error checking — if it fails, something else needs to tell us.

**ICMP:**

* This protocol is used for sending error messages across the network.
* In this case, it told the client that the server’s DNS port wasn’t reachable.

**Port 53:**

* Standard port used for DNS servers.
* If the server’s DNS service isn’t running or responding on this port, queries will fail.

## Important Things I Learned

* When DNS fails, the traffic still gives clues through ICMP errors.
* ICMP can show whether a specific service (like DNS) isn’t reachable, even if the server is up.
* A “Port Unreachable” ICMP error usually means the server is online but the application (here, DNS) isn’t running or is blocked.
* Always check if DNS is running on port 53 when domain names aren’t resolving.

## Tools and Approach

* I looked at the network logs (could be Wireshark, tcpdump, or a simplified log viewer).
* I didn’t use any complex commands — just followed the packets to see what failed.

## Final Thoughts

This was my first time doing packet-level investigation, and even though it looked confusing at first, it started to make sense when I matched the DNS request and the ICMP response.
It taught me how protocol errors show up in traffic and how to identify what service might be failing. This kind of analysis feels like real-world security work.
