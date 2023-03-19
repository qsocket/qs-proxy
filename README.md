<div align="center">
  <img src=".github/img/banner.png">
  <br>
  <br>


  [![GitHub All Releases][release-img]][release]
  [![Build][workflow-img]][workflow]
  [![Issues][issues-img]][issues]
  [![License: MIT][license-img]][license]
</div>

[release]: https://github.com/qsocket/qs-proxy/releases
[release-img]: https://img.shields.io/github/v/release/qsocket/qs-proxy
[downloads]: https://github.com/qsocket/qs-proxy/releases
[downloads-img]: https://img.shields.io/github/downloads/qsocket/qs-proxy/total?logo=github
[issues]: https://github.com/qsocket/qs-proxy/issues
[issues-img]: https://img.shields.io/github/issues/qsocket/qs-proxy?color=red
[license]: https://raw.githubusercontent.com/qsocket/qs-proxy/master/LICENSE
[license-img]: https://img.shields.io/github/license/qsocket/qs-proxy.svg
[google-cloud-shell]: https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/qsocket/qs-proxy&tutorial=README.md
[workflow-img]: https://github.com/qsocket/qs-proxy/actions/workflows/main.yml/badge.svg
[workflow]: https://github.com/qsocket/qs-proxy/actions/workflows/main.yml
[qsrn]: https://www.qsocket.io/qsrn/

**qs-proxy** is a networking utility which allows redirecting the TCP traffic of binary programs over the [QSRN][qsrn] network. It does so by hooking fundamental socket libraries inside libc using LD_PRELOAD method.

## Installation

[![Open in Cloud Shell](.github/img/cloud-shell.png)][google-cloud-shell]

|   **Tool**   |   **Build From Source**    | **Binary Release**  |
| :----------: | :------------------------: | :-----------------: |
| **qs-proxy** | ```make && make install``` | [Download](release) |

---

## Usage

```
./qs-proxy [options...] <program> <parameters...>
	-s, --secret <string>    Secret (e.g. password).
	-v, --verbose            Verbose output.
Example:
	$ ./qs-proxy -s MySecret  ssh root@qsocket     # SSH over qsocket
	$ ./qs-proxy -s MySecret  rdesktop qsocket     # RDP over qsocket

```

### Examples
- SSH from *Workstation B* to *Workstation A* through any firewall/NAT
```bash
$ qs-netcat -f "localhost" -p 22 -l  # Workstation A
$ qs-proxy ssh root@qsocket.io       # Workstation B
```

- RDP from *Workstation B* to *Workstation A* through any firewall/NAT
```bash
$ qs-netcat -f "localhost" -p 3389 -l # Workstation A
$ qs-proxy xfreerdp qsocket           # Workstation B
```

#### 🚧 WARNING 🚧 
This utility currently do not support E2E encryption. The E2E encryption will be added on the first major release. 
