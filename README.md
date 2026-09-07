# Go Cafe

A native client for playing Go — Baduk, Weiqi — online. It signs in to
[Fox (foxwq)](https://www.foxwq.com/) and gives you the board, the clocks, the
lobby and your game history, without a browser and without the ads.

Builds here are for **testing**. They work; they are also unfinished, unsigned,
and not in any app store, which has consequences your computer will tell you
about the moment you open one. That is covered below.

## Download

**[→ Latest release](../../releases/latest)**

| Platform | File | Guide |
|---|---|---|
| **macOS** 10.15+, Apple Silicon and Intel | `GoCafe-<version>.dmg` | [INSTALL-macos.md](INSTALL-macos.md) |
| **Windows** 10 and 11, 64-bit | `GoCafe-<version>-windows-x64.zip` | [INSTALL-windows.md](INSTALL-windows.md) |
| **Linux** x86_64, glibc 2.35+ | `GoCafe-<version>-x86_64.AppImage` | [INSTALL-linux.md](INSTALL-linux.md) |
| **Android** 7.0+ | `GoCafe-<version>.apk` | [INSTALL-android.md](INSTALL-android.md) |

The Linux build needs **glibc 2.35 or newer** — Ubuntu 22.04+, Debian 12+,
Fedora 36+. Ubuntu 20.04 and Debian 11 are too old and it will not start on
them.

Nothing to choose on Android: one APK covers arm64, arm32 and x86_64.

## Your computer will warn you. Here is exactly why

Every platform below shows a scary message. None of them means anything was
found in the app — they all mean the same thing, which is that nobody has paid
to vouch for it yet.

**macOS** says *"Apple cannot check it for malicious software"* and offers only
Move to Trash. Signing an app for macOS needs a paid Apple Developer
certificate; this build has none. Right-click the app and choose **Open** and
you get the same dialog with an **Open** button. That is macOS's own way of
saying "I know where this came from" — it disables no security setting and
applies to this one app only.

**Windows** says *"Windows protected your PC"* under a blue SmartScreen panel.
Same cause: no code-signing certificate. Click **More info**, then **Run
anyway**.

**Android** says *"Unsafe app blocked — Play Protect doesn't recognise this
app's developer"*. Play Protect flags everything that did not arrive through the
Play Store. Tap **More details**, then **Install anyway**.

**Linux** says nothing at all, because Linux doesn't do this. You need
`chmod +x` and that's the whole ceremony.

Full step-by-step for each is in the guides linked above. Read the one for your
platform before you start — each has a couple of things worth knowing that this
summary leaves out.

## Checking that you got what we sent

Every file except the `.dmg` ships with a `.sha256` beside it. Download both,
then:

```sh
sha256sum -c GoCafe-<version>.apk.sha256
```

`shasum -a 256 -c` on macOS, which has no `sha256sum`. A truncated download is
by far the most common reason an install fails, and this catches it in a second.

## What it does with your account

You are being asked to type a password into an unsigned binary from a stranger
on the internet, so this ought to be said plainly.

- **Go Cafe has no server of its own.** Your username and password go straight
  to the Go server you picked — Fox — over its own protocol. There is no account
  to make here and no middleman to trust.
- **Your password is not stored.** Ticking "stay signed in" keeps a rotating
  session token in the app's private storage, not the password. Signing out
  discards it.
- **Nothing is collected.** No analytics, no telemetry, no crash reporting that
  phones home. There is a session log on your own disk, which the guides tell
  you where to find, and it does not contain your password.
- Android asks for exactly one permission: `INTERNET`.

## Reporting a problem

Open an [issue](../../issues). What helps most:

- what you did, what happened, and what you expected instead
- your platform and the version you installed
- the session log if the app misbehaved — each guide says where yours lives

Bug reports on a test build are the entire point, so nothing is too small.

## Licence and credits

The board and stone artwork is other people's work under their own licences —
MIT and CC BY-SA 4.0 — and every set is credited by name, author and licence on
the app's own **Settings → Credits** screen, which is generated from the
attribution file that ships inside the app rather than written by hand.

Go Cafe is an unofficial client. It is not affiliated with, endorsed by, or
connected to Fox Weiqi.
