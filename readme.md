<div align="center">

# fastd

small udp vpn daemon for ip and ethernet tunnels.

<a href="https://count.owenewans.org/owenewans/fastd?theme=moebooru-h&notitle"><img src="https://count.owenewans.org/owenewans/fastd?theme=moebooru-h&notitle" alt="repository views"></a>

`c99` `vpn` `linux`

</div>

## features

- TUN (L3 IP) and TAP / multi-TAP (L2 Ethernet) modes over UDP
- authenticated encryption (`salsa2012+umac`, `aes128-gcm`, `aes128-ctr+umac`, `salsa20+poly1305`) and authenticated-only or null modes
- `ec25519-fhmqvc` handshake with static or dynamic peers
- 4 MiB UDP socket receive and send buffers (`SO_RCVBUF` and `SO_SNDBUF`)
- optional L2TP kernel offload for `null@l2tp` in multi-TAP mode
- runs on Linux, FreeBSD, OpenBSD and macOS

## install

Install `meson`, `ninja`, `bison`, `pkg-config`, `libuecc`, `libsodium`,
`openssl`, `libcap`, `libmnl` and `json-c`. Then:

```sh
git clone https://github.com/owenewans/fastd
cd fastd
meson setup build --buildtype=release -Db_lto=true -Dc_args="-O3 -march=native -mtune=native"
ninja -C build
```

The binary is written to `build/src/fastd`.

## usage

```sh
build/src/fastd --generate-key
build/src/fastd --config fastd.conf
```

See [man page](doc/fastd.1) and [documentation](doc/source/index.rst) for
configuration options, peer files and MTU selection.

## license

[BSD-2-Clause](LICENSE)
