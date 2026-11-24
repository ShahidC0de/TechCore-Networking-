# TechCore Solutions - Enterprise Network Infrastructure
Cisco Packet Tracer capstone | CCNA practical labs: Days 1-6
Project status: Core network configured and tested in Packet Tracer. Formal acceptance evidence is being finalized. Server IP address management requires correction before final handover.

Overview
Simulated a small enterprise network supporting four departments, with segmented Layer 2 networks, inter-VLAN routing, DHCP, and an internal DNS/HTTP portal.

Goal: Demonstrate practical routing, switching, client-server services, verification and troubleshooting relevant to junior network support and IT support roles.
Topology

Replace this reference with your real annotated Packet Tracer topology screenshot before publishing.

- 1 Cisco 2911 router
- 2 Cisco 2960 switches
- 8 representative PCs and 1 internal server
- Router-on-a-stick trunk: Router G0/0 to Main-S Fa0/1
- Inter-switch trunk: Main-S Gi0/1 to Fin-Sales-Switch (VLANs 30, 40)
VLAN and IP addressing
Department	Users planned	  VLAN	    Subnet	Gateway
IT           12	    10	192.168.10.0   /24	  192.168.10.1
HR	         10	    20	192.168.20.0   /24	  192.168.20.1
Finance	     14	    30	192.168.30.0   /24	  192.168.30.1
Sales	       24	    40	192.168.40.0   /24	  192.168.40.1


DHCP exclusion policy: .1-.20 in each VLAN, with clients using .21+. A /24 subnet provides ample host capacity for each department.
Services
- DHCP: Cisco router DHCP pools for all four VLANs
- Routing: 802.1Q subinterfaces on the Cisco router
- HTTP: TechCore intranet website on an internal server
- DNS: intranet.techcore.test (reported working)
Addressing note: The internal DNS/HTTP server is currently reported at 192.168.10.22, which also appeared in router DHCP bindings. Before final publication, make the server address stable (static + DHCP exclusion or documented reservation) and verify all clients use the final DNS address. Do not assume it is already fixed.
Validation
Check	State	Evidence
Four router subinterfaces up/up	Verified	Test-Results/screenshots/router-interfaces.png
Four connected /24 routes	Verified	Test-Results/screenshots/router-routes.png
Main-S trunk operation	Verified	Test-Results/screenshots/main-switch-trunks.png
DHCP leases outside .1-.20	Verified	Test-Results/screenshots/dhcp-bindings.png
Web portal via DNS name	Reported working	Screenshot pending
All VLANs pass final gateway/host/HTTP matrix	Pending formal record	Test-Results/acceptance-tests.csv
Secondary switch current trunk evidence	Pending	Screenshot pending


Troubleshooting highlights
Missing Sales default gateway: VLAN 40 clients received DHCP addresses but could not reach other departments. Reviewed the DHCP pool, added default-router 192.168.40.1, renewed client leases, and restored connectivity.

DHCP initially configured on the wrong device: Moved DHCP provisioning to the router as designated for this lab.

Transient ICMP failures: Some pings began succeeding without further edits; root cause was not confirmed, so it is documented as an observation rather than a proven fault.

See [Troubleshooting notes](incident-log.md).
Repository contents
- Packet-Tracer/ - working .pkt project (TechCore-Project.pkt)
- Network-Diagram/ - labeled topology
- Configurations/ - sanitized CLI output for router and switches
- Test-Results/ - acceptance matrix and screenshots
- Troubleshooting/ - evidence-based incident log
- Documentation/ - detailed technical report
Skills demonstrated
IPv4 addressing, switching, VLANs, 802.1Q trunks, router-on-a-stick, DHCP, DNS, HTTP, Cisco CLI, ping/ARP diagnostics and structured troubleshooting.
Scope and limitations
Packet Tracer simulation only. No physical network deployment, production hardening, ACL implementation, internet/NAT, dynamic routing, or tested redundancy. Project is an educational lab and not an employer infrastructure configuration.
