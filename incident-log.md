# Troubleshooting incidents

| ID | Symptom | Investigation | Root cause | Resolution | Verification |
|---|---|---|---|---|---|
| INC-01 | Sales clients get DHCP IP but cannot ping other VLANs | Checked PC `ipconfig`, router interfaces, DHCP pool configuration | Sales DHCP pool missing `default-router` | Added `default-router 192.168.40.1` and renewed DHCP | User reported successful connectivity |
| INC-02 | DHCP initially failed | Checked switch/router configuration and device role | DHCP pools entered on switch instead of designated router | Configured DHCP pools on Cisco 2911 | Router bindings later confirmed |
| INC-03 | Ping initially timed out but later succeeded | Checked routes, trunks, gateways, PC paths | Not proven | No definitive change identified | Later pings succeeded |
| INC-04 | DNS/HTTP server address 192.168.10.22 inside DHCP lease range | Compared reported server IP to bindings and excluded addresses | Address-management inconsistency | **Pending:** statically allocate and exclude/reserve server IP | Pending |

> Evidence standard: Distinguish reproduced faults, observed symptoms, and hypotheses.
