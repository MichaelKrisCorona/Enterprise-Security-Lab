## Architectural Framework & Modular Deployment

This home lab is engineered as a highly dynamic, multi-scenario simulation environment. The infrastructure is architected to pivot seamlessly between diverse offensive and defensive operational contexts. 

The diagram below outlines the core, unchanging structural zones and trust boundaries of the environment:

![Home Lab Network Topology](network-topology.png)

### Operational Subnet Matrix

To accommodate fluid testing pipelines, network routing shifts based on the active exercise matrix:

* **Scenario A: External Edge Testing (Perimeter Boundary)**
  The Emulation Host is positioned externally, routing adversarial traffic through the WAN interface of the OPNsense gateway to test ingress filtering, firewall rule efficacy, and edge-defense postures.
* **Scenario B: "Assume Breach" & Insider Threat (Internal Segments)**
  The Emulation Host is retrofitted onto an isolated internal host-only segment (`vmnet2`). It assumes an internal footprint (`10.0.0.7`) to simulate a compromised endpoint, lateral movement vectors, and east-west traffic visibility to the Debian production target and REMnux sandbox.
