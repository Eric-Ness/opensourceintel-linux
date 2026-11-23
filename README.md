# OpenSourceIntel Linux

A live USB for open-source intelligence (OSINT) work: boot it on any PC,
investigate, and shut down without leaving anything behind. Ubuntu 26.04 with
GNOME, built with [linuxlive](https://github.com/Eric-Ness/linuxlive) from
one file, [`linuxlive.yaml`](linuxlive.yaml).

**Passive tools only.** Everything here reads public sources: search engines,
certificate logs, DNS datasets, social sites, archives. Nothing scans, probes
or brute-forces a target's own servers; for that, use a pentesting distro,
and only with permission.

## What's on it

Open **OSINT Tools** (or type `osint` in a terminal) for the list with
examples.

| For | Tools |
|---|---|
| People and accounts | sherlock, maigret, holehe, instaloader |
| Domains and organisations | theHarvester, subfinder, assetfinder, findomain, amass (passive mode), dnstwist, whois, dig, uro |
| Documents, images and video | metagoofil, exiftool, mat2 and Metadata Cleaner, yt-dlp, VLC |
| Frameworks | SpiderFoot (in the browser), recon-ng, **Get Maltego** |
| Browsing | Firefox (OSINT bookmarks), Tor Browser, OnionShare |
| Keeping the case | Joplin (notes), Zotero (sources and snapshots), KeePassXC, Gephi (graphs) |

**Maltego** isn't open source, so it isn't on the disc. **Get Maltego**
opens Maltego's downloads page; download the Linux `.deb`, open Get Maltego
again, and it installs and starts it. Maltego is free with a Maltego account.

## Where things come from

- Ubuntu's archive: recon-ng, sherlock, assetfinder, instaloader, dnstwist,
  exiftool, mat2, yt-dlp, whois, dig.
- Flathub: Tor Browser, KeePassXC, Joplin, Zotero, Gephi, Metadata Cleaner,
  OnionShare, Firefox, VLC.
- GitHub at pinned commits (`repos:` in the spec): theHarvester 4.11.1,
  SpiderFoot, metagoofil 1.5.0.
- PyPI at pinned versions: maigret 0.6.7, holehe 1.61, uro 1.0.2.
- Release builds checked by SHA-256: subfinder 2.17.0, findomain 11.0.0,
  amass 5.1.3.

The Python tools each get their own environment from
[uv](https://github.com/astral-sh/uv) ([`files/osint-uv`](files/osint-uv)),
on the Python version they need. [`scripts/build.sh`](scripts/build.sh)
installs the rest and checks that every tool starts.

## Build it

Commit to `main` and GitHub Actions builds the ISO, boots it five ways and
checks it. Download it from the run's **Artifacts**. It rebuilds itself on
the 7th of each month with the newest packages.

To update a tool, change its commit or version in `linuxlive.yaml` or
`scripts/build.sh` (and its SHA-256 for the release builds).

## Licence

The spec, scripts and art in this repository: MIT No Attribution (see
[LICENSE](LICENSE)). Each tool keeps its own licence; the ISO's package list
names every repository and commit built into it.
