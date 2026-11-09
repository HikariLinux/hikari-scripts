# Hikari Linux administration scripts

Utilities for systems using the retained Apple Silicon Linux boot and firmware
interfaces. Public commands are `hikari-diagnose`, `hikari-fwupdate`, and
`update-m1n1`; Arch integration also installs `update-grub` and `first-boot`.

## Installation

On Linux with GNU make and coreutils, select the integration for the target image:

```sh
make install-fedora PREFIX=/usr DESTDIR="$pkgdir"
# Or, for an Arch-based image:
make install-arch PREFIX=/usr DESTDIR="$pkgdir"
```

Packaging must replace/conflict with `asahi-scripts` and any distribution
package owning the same boot hooks or utilities. Shared helpers live under
`/usr/share/hikari-scripts`. The firmware updater reads
`/etc/default/hikari-fwupdate`, falling back to the legacy configuration file.

The mkinitcpio hook `asahi`, dracut module names, kernel driver names,
`asahi,*` device-tree properties, `/usr/lib/asahi-boot`, ESP firmware layout,
`ASAHIFW`, `asahi-fwextract`, and external package/keyring dependencies retain
their existing names for compatibility. `hikari-diagnose` reports Hikari
packages alongside compatible upstream packages. Review diagnostic output for
private information before sharing it.

These utilities can change firmware and boot files. This rebrand preserves the
snapshot's implementation and does not establish support for new machines.
Upstream Packit jobs have been removed; builds do not fetch upstream packaging.

## Origin and license

Based on the preserved [asahi-scripts snapshot](https://github.com/HikariLinux/asahi-scripts/tree/755b1d19e61d58b010f32349b7aba8f2c580fc29),
commit `755b1d19e61d58b010f32349b7aba8f2c580fc29`. Original history and snapshot tags are retained.
Hikari Linux maintains this project independently; this is not an official
Asahi Linux release. Original copyright and license notices are preserved.
Hikari Linux changes use the same [MIT license](LICENSE).
