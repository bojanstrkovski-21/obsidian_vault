I. With Package Managers
## Gentoo ([GURU](https://gitweb.gentoo.org/repo/proj/guru.git/tree/x11-wm/leftwm))

```shell
sudo layman -a guru && sudo emerge --sync 
sudo emerge --ask --verbose x11-wm/leftwm
```

## [](https://github.com/leftwm/leftwm#archlinux-aur)Archlinux ([AUR](https://aur.archlinux.org/packages/leftwm))

```shell
paru -S leftwm
```

[paru](https://github.com/Morganamilo/paru) is an AUR helper like [yay](https://github.com/Jguer/yay), but written in [Rust](https://github.com/rust-lang/rust).

## [](https://github.com/leftwm/leftwm#fedora-copr)Fedora ([copr](https://copr.fedorainfracloud.org/coprs/atim/leftwm/))

```shell
sudo dnf copr enable th3-s4lm0n/leftwm -y && sudo dnf install leftwm
```

## [](https://github.com/leftwm/leftwm#netbsd-official-repositories)NetBSD ([Official repositories](https://pkgsrc.se/wm/leftwm/))

```shell
pkgin install leftwm
```

or, if you prefer to build it from source

```shell
cd /usr/pkgsrc/wm/leftwm
make install
```

## [](https://github.com/leftwm/leftwm#void-xbps)Void ([XBPS](https://voidlinux.org/packages/?arch=x86_64&q=leftwm))

```shell
sudo xbps-install -S leftwm
```

## [](https://github.com/leftwm/leftwm#cargo-cratesio)Cargo ([crates.io](https://crates.io/crates/leftwm))

```shell
cargo install leftwm
```

If you install LeftWM with crates.io, you will need to link to the [xsession desktop file](https://github.com/leftwm/leftwm/blob/758bbf837a8556cdc7e09ff2d394f528e7657333/leftwm.desktop) if you want to be able to login to LeftWM from a display manager (GDM, SSDM, LightDM, etc.):

```shell
sudo cp PATH_TO_LEFTWM/leftwm.desktop /usr/share/xsessions
```

Also see [the build options](https://github.com/leftwm/leftwm#optional-build-features) for more feature options, especially if you don't use `systemd` or want to use your own hotkey daemon like `sxhkd`.

## [](https://github.com/leftwm/leftwm#openbsd-openbsd)OpenBSD ([OpenBSD](https://openbsd.org/))

At the moment LeftWM is not packaged with OpenBSD package manager, but it could be installed via Cargo.

```shell
cargo install leftwm --no-default-features --features lefthk
```

`leftwm-config` not yet ported to OpenBSD, as it requires a nightly Rust compiler to build. The default config is generated by LeftWM when it is first started.

To start LeftWM with `xenodm` add the following to your `~/.xsession`. Make sure to remove or comment-out the `exec` to the previous WM you had there.

```shell
exec dbus-launch ~/.cargo/bin/leftwm >> ~/.cache/leftwm.log 2>&1
```

