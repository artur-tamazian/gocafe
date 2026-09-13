# Go Cafe

A native client for playing Go — Baduk, Weiqi — online, on
[Fox (foxwq)](https://www.foxwq.com/). Board, clocks, lobby and history, without
a browser.

Go Cafe isn't in any app store, and isn't signed yet — which your computer will
have opinions about. See below.

## Download

**[→ Latest release](../../releases/latest)**

| Platform | File | Guide |
|---|---|---|
| **macOS** 10.15+, Apple Silicon and Intel | `GoCafe-<version>.dmg` | [install](INSTALL-macos.md) |
| **Windows** 10 and 11, 64-bit | `GoCafe-<version>-windows-x64.zip` | [install](INSTALL-windows.md) |
| **Linux** x86_64, glibc 2.35+ | `GoCafe-<version>-x86_64.AppImage` | [install](INSTALL-linux.md) |
| **Android** 7.0+ | `GoCafe-<version>.apk` | [install](INSTALL-android.md) |

Linux needs **glibc 2.35 or newer** — Ubuntu 22.04+, Debian 12+, Fedora 36+.
Older than that and it won't start. Android is one APK for every device.

## Your computer will warn you

Nothing is wrong with the app. The warning means nobody has paid to vouch for it,
which is a different thing — signing certificates cost money, and Go Cafe isn't
signed yet.

- **macOS** — *"Apple cannot check it for malicious software"*, offering only
  Move to Trash. Click **Cancel**, then open **System Settings → Privacy &
  Security**, scroll down and click **Open Anyway**. (On macOS 14 and earlier:
  right-click the app → **Open** instead.)
- **Windows** — a blue *"Windows protected your PC"* panel. **More info** →
  **Run anyway**.
- **Android** — *"Unsafe app blocked"*. **More details** → **Install anyway**.
- **Linux** — nothing. `chmod +x` and run it.

Each guide above has the full walkthrough plus the handful of things that go
wrong. Worth a look before you start.

## Checking the download

Every file has a `.sha256` next to it:

```sh
sha256sum -c GoCafe-<version>.apk.sha256     # shasum -a 256 -c on macOS
```

A half-finished download is the most common reason an install fails, and this
catches it in a second.

## Something broken?

Open an [issue](../../issues) — what you did, what happened, your platform and
version. Each guide says where your session log lives; attaching it helps a lot.
Nothing is too small to report.

## Credits

Board and stone artwork is other people's work under MIT and CC BY-SA 4.0, each
set credited by name, author and licence on the app's **Settings → Credits**
screen.

Go Cafe is an unofficial client, not affiliated with or endorsed by Fox Weiqi.
