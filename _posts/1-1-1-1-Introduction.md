# Docker

## Security Myths - Security Legends

---

# About Me

 - 15 Years in IT/Information Security
 - Managing Consultant at NCC Group PLC
 - Contributor at Security Stack Exchange

---

<img src="/images/home.jpg" width="75%"/>


---

# Topics

* Container Security Building Blocks {% fragment %}
* Containers Vs VMs {% fragment %}
* Docker Daemon Security {% fragment %}
* Practical Docker Security {% fragment %}
* Docker Threat Models {% fragment %}


---

# Some Terminology

--

Attack Surface

--

<img src="/images/risk.png"/>

Note: 

Image from wikimedia - Riskgamenut -  https://upload.wikimedia.org/wikipedia/en/5/55/Riskgameboard.svg - CC BY-SA 3.0
Concept of attack surface is very important in security, the larger the attack surface the more there is to secure and the larger the scope for security vulnerabilities

--

Threat Model

Note:

Threat models are very important in security.  First question in response to "Is this secure?" is "From what"

--

<img src="/images/cyber-criminal.jpg" width="75%"/>

Note: 

Image by Perspecsys Photos - https://flic.kr/p/qa7nm9 - CC BY-SA 2.0
Cyber criminals are pretty prevalent these days and will focus wherever there is money to be made.  this may be wider than you think (e.g. ransomware)

--

<img src="/images/anon.jpg" width="50%"/>

Note:

Image By Kigsz (Own work) [CC BY-SA 3.0 (http://creativecommons.org/licenses/by-sa/3.0)], via Wikimedia Commons
Hactivists are a different class of threat.  May be more determined but are less well resourced.  Things like DDoS more likely

--

<img src="/images/nation_state.jpg" width="75%"/>

Note:

Image By Alvesgaspar (self-made, stitch from 4 photographs) [GFDL (http://www.gnu.org/copyleft/fdl.html) or CC BY-SA 3.0 (http://creativecommons.org/licenses/by-sa/3.0)], via Wikimedia Commons
Depending on who you are, nation state level attackers may be a possibility.  Again very different in terms of their capabilities and methods of attack.

---

<img src="/images/pandoras_box.jpg" width="75%"/>

Note: 

Image Credit - Michael Hensmann - https://www.flickr.com/photos/mycael/3664900435/in/photostream/ - CC BY-SA 2.0

---

# How Do Containers Contain?

---

# Container Security == Linux Security

Note:

All the mechanisms used by containers can be used by users directly
Docker policy is for "sensible default" which can then be tweaked up or down

---

# Namespaces

--

## Mount(chroot)

--

## Process

--

## Network

Note:

A good example of the problems of --net=host is https://github.com/docker/docker/issues/14767 which shows a docker host that uses upstart can be rebooted by a container using --net=host

--

## IPC

Note: 

One of the points here relates to protecting containers against a malicious container attempting to read shared memory space used by IPC http://labs.portcullis.co.uk/whitepapers/memory-squatting-attacks-on-system-v-shared-memory/

--

## UTS

--

## User(!!)

---

# Capabilities

* Break up the monolithic 'root' Privilege
* Useful for commands that need one privilege
* Some need careful handling (e.g. CAP_SYS_ADMIN)

Note:

https://github.com/docker/docker/blob/master/oci/defaults_linux.go lists the default capabilities

---

# CGroups

* Resource Limits
* Restrict Access to Devices

Note:

Reason for the use of cgroups to limit access to devices is that the dev system is not namespaced.
cpu, memory, blkio, devices, network, freezer, pid
PID cgroup is a new one used for blocking fork bombs amongst other things https://github.com/docker/docker/pull/18697

---

# Seccomp

Note:
https://github.com/docker/docker/blob/master/docs/security/seccomp.md - Details of seccomp in Docker, also details the default profile


---

# Mandatory Access Control

* AppArmor
* SELinux

---

# Containers Vs VMs

<img src="/images/bears.jpg" width="50%"/>

Note:

Photo Credit - Anneheathen - https://flic.kr/p/aAMxAW - CC BY-SA 2.0

---

# Docker Engine Security

<img src="/images/docker-engine.png" width="50%" />

--

## Authentication & Authorization

--

## Inter Container Communications (--icc)

Note:

First up is changing the default by disabling icc, second the risk of arp poisoning, which could be mitigated by removing CAP_NET_RAW

--

## The Perils of --privileged

--

## Mounting docker.sock

---

# Docker Hub

<img src="/images/docker-hub.png" width="50%" />

--

## Image Provenance

Note:

Talk here about both the Dockerfile sourcees and also about Docker Content Trust, its scope and limitations

--

## Image Hardening

Note:

Cover attack surface, and also reduced patching requirements of smaller containers.

---

# Threat Models

What level of security is right?

---

# Resources - 1

* Docker Bench - https://github.com/docker/docker-bench-security 
* CIS Security Guide for Docker - https://benchmarks.cisecurity.org/tools2/docker/CIS_Docker_1.11.0_Benchmark_v1.0.0.pdf

---

# Resources - 2

* Docker security eBook - https://gallery.mailchimp.com/979c70339150d05eec1531104/files/Docker_Security_Red_Hat.pdf
* Understanding and Hardening Linux Containers - https://www.nccgroup.trust/globalassets/our-research/us/whitepapers/2016/april/ncc_group_understanding_hardening_linux_containers-10pdf/

---

# Conclusion

* Security Model isn't perfect, but is improving
* A number of hardening steps available
* Always think about your threat model and attack surface :)

---

# Questions

* Twitter - @raesene
* E-mail - rorym@mccune.org.uk
