Indywall update utilities
=========================

The firmware update tools of the Indywall firewall: kernel and base set
updates in the FreeBSD style, plus package updates through pkg(8), with
signature verification for every moving part.

The tools keep their `opnsense-*` command names, which the rest of the
system calls by name.

| Command | Purpose |
|---|---|
| `opnsense-update` | Single tool for package, base and kernel updates, including major FreeBSD version upgrades and debug kernels. Verifies signatures through pkg(8)'s own mechanisms. |
| `opnsense-bootstrap` | Reinstalls a running system in place (factory reset or file consistency), optionally wiping the configuration; can turn a stock FreeBSD release into an installation. |
| `opnsense-sign`, `opnsense-verify` | Sign and verify arbitrary files with pkg(8)'s signature methods, so packages and sets share one key store. |
| `opnsense-fetch` | Wraps fetch(1) and reports download progress to the caller. |
| `opnsense-patch` | Applies upstream git patches to core, plugins, installer and update tools, with a local cache for offline use. |
| `opnsense-code` | Fetches or updates full source repositories on an installed system with git(1). |
| `opnsense-revert` | Reverts a package to its state in an earlier release, within what the package mirrors hold. |

Status for Indywall
-------------------

The package mirrors for Indywall are not live yet (placeholders such as
`https://pkg.indywall.invalid`). Until they are, updates, bootstrapping and
reverts that need a mirror do not work for Indywall systems, and the
bootstrap instructions of the upstream project do not apply.

How the image uses this repository
----------------------------------

The Indywall image installs this code as the `opnsense-update` package,
built by the `opnsense/update` port in
[indywallfw/ports](https://github.com/indywallfw/ports). The port pins a
commit of this repository (`GH_TAGNAME`); to ship a change, merge it into
`master` here, then update `GH_TAGNAME` and regenerate `distinfo`
(`make makesum`) in the port.

Origin
------

Indywall is built on [OPNsense](https://opnsense.org). This repository is a
fork of [opnsense/update](https://github.com/opnsense/update) and remains
available under the BSD 2-clause license in `LICENSE`.
