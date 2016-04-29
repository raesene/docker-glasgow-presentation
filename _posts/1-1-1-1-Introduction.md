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
* Docker Daemon Security {% fragment %}
* Containers Vs VMs {% fragment %}
* Docker Threat Models {% fragment %}
* "Practical" Docker Security {% fragment %}

---

# Some Terminology

--

Attack Surface

--

<img src="/images/risk.png"/>

Note: 

Image from wikimedia - Riskgamenut -  https://upload.wikimedia.org/wikipedia/en/5/55/Riskgameboard.svg - CC BY-SA 3.0

--

Threat Model

--

<img src="/images/cyber-criminal.jpg" width="75%"/>

Note: 

Image by Perspecsys Photos - https://flic.kr/p/qa7nm9 - CC BY-SA 2.0

--

<img src="/images/anon.jpg" width="50%"/>

Note:

Image By Kigsz (Own work) [CC BY-SA 3.0 (http://creativecommons.org/licenses/by-sa/3.0)], via Wikimedia Commons

--

<img src="/images/nation_state.jpg" width="75%"/>

Note:

Image By Alvesgaspar (self-made, stitch from 4 photographs) [GFDL (http://www.gnu.org/copyleft/fdl.html) or CC BY-SA 3.0 (http://creativecommons.org/licenses/by-sa/3.0)], via Wikimedia Commons

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

--

## IPC

Note: 

One of the points here relates to protecting containers against a malicious container attempting to read shared memory space used by IPC http://labs.portcullis.co.uk/whitepapers/memory-squatting-attacks-on-system-v-shared-memory/

--

## PID

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
https://github.com/docker/docker/blob/master/docs/security/seccomp.md - Details of seccomp in Docker

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
