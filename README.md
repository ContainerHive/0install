# ContainerHive 0install feed

Signed [0install](https://0install.net) feed for the `ch` CLI of
[ContainerHive](https://github.com/ContainerHive/ContainerHive).

## Install

```sh
0install add ch https://0install.container-hive.timo-reymann.de/containerhive.xml
0install run ch
```

On the first run, 0install asks once to trust the release key.

## How it works

The branch `gh-pages` is served on this site. It holds:

- `containerhive.xml` — the signed master feed with every released version
- `<fingerprint>.gpg` — the public key of the release key, next to the feed
- `containerhive.png` — app icon for 0install launchers

CircleCI publishes the feed: the `publish-0install-feed` job in ContainerHive runs
`scripts/publish-0install-feed.sh` on release tags. It generates a version feed with
`0template`, merges it into the master feed with `merge-feed.py`, and pushes the
re-signed master feed here. The scripts and the feed template live in the
ContainerHive repository; this repository stores published state only — do not
edit the feed files by hand.
