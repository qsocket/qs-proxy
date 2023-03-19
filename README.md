<div align="center">
  <img src=".github/img/banner.png">
  <br>
  <br>


  [![GitHub All Releases][release-img]][release]
  [![Build][workflow-img]][workflow]
  [![Issues][issues-img]][issues]
  [![License: MIT][license-img]][license]
</div>

[go-report]: https://goreportcard.com/report/github.com/qsocket/qs-netcat
[go-report-img]: https://goreportcard.com/badge/github.com/qsocket/qs-netcat
[release]: https://github.com/qsocket/qs-netcat/releases
[release-img]: https://img.shields.io/github/v/release/qsocket/qs-netcat
[downloads]: https://github.com/qsocket/qs-netcat/releases
[downloads-img]: https://img.shields.io/github/downloads/qsocket/qs-netcat/total?logo=github
[issues]: https://github.com/qsocket/qs-netcat/issues
[issues-img]: https://img.shields.io/github/issues/qsocket/qs-netcat?color=red
[docker-pulls]: https://img.shields.io/docker/pulls/qsocket/qsocket?logo=docker&label=docker%20pulls
[license]: https://raw.githubusercontent.com/qsocket/qs-netcat/master/LICENSE
[license-img]: https://img.shields.io/github/license/qsocket/qs-netcat.svg
[google-cloud-shell]: https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/qsocket/qs-proxy&tutorial=README.md
[workflow-img]: https://github.com/qsocket/qs-netcat/actions/workflows/main.yml/badge.svg
[workflow]: https://github.com/qsocket/qs-netcat/actions/workflows/main.yml
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
$ qsocket ssh root@qsocket.io        # Workstation B
```
