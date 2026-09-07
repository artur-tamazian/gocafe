# Installing Go Cafe on your Mac

Thanks for testing. This takes about a minute.

## 1. Open the disk image

Double-click **GoCafe-<version>.dmg**. A window opens with the Go Cafe icon and a
shortcut to your Applications folder.

## 2. Drag Go Cafe into Applications

Drag the **Go Cafe** icon onto the **Applications** folder next to it.

Then eject the disk image: click the ⏏ next to "Go Cafe" in the Finder sidebar,
or drag it to the Trash. (You are ejecting the image, not deleting the app.)

## 3. First launch — the important bit

**Do not double-click the app the first time.** If you do, macOS says

> "Go Cafe" can't be opened because Apple cannot check it for malicious software.

and offers you only **Move to Trash** or **Cancel**. Click **Cancel** — nothing
is wrong with the app, and the next step is the way past it.

Instead, open it this way the first time:

1. Open your **Applications** folder.
2. **Right-click** (or Control-click) **Go Cafe**.
3. Choose **Open** from the menu that appears.
4. You get a similar warning, but this time there is an **Open** button. Click it.

That is it. From then on Go Cafe opens normally with a double-click — you only
need to do this once.

## Why does macOS warn me?

Go Cafe is not signed with an Apple Developer certificate yet. Apple charges an
annual fee for one, and this build is an early test version, so it does not have
one. macOS shows the same warning for any app it has not seen notarised by
Apple, regardless of whether the app is fine.

Right-clicking and choosing **Open** is macOS's own built-in way of saying "yes,
I know where this came from, let it run." It does not disable any security
setting on your Mac, and it applies only to this one app.

## Anything not working?

Nothing, as of this build. **"Stay signed in" works.** It used to not: an
unsigned app cannot use the macOS Keychain, so the tick box looked like it
worked and saved nothing. Fox is now remembered as a rotating session token kept
in the app's own container instead of a password in the Keychain, which needs no
signature and no permission prompt. Your password is not stored at all.

## If something goes wrong

**"Go Cafe is damaged and can't be opened."**
This usually means the download was incomplete or the file was unpacked by
something that stripped it. Delete the app and the .dmg, download again, and
retry step 3. If it persists, run this in Terminal and try once more:

```
xattr -dr com.apple.quarantine "/Applications/Go Cafe.app"
```

**The Open option does not appear when I right-click.**
Make sure you are right-clicking the app in **Applications**, not inside the
still-mounted disk image.

**It opens but cannot reach a server.**
Check that you are online, then confirm no VPN or corporate firewall is blocking
outbound connections. Go Cafe talks to Go servers directly on their own ports,
not over plain web traffic, and some restrictive networks block that.

## Requirements

- macOS 10.15 or newer
- Works on both Apple Silicon and Intel Macs

## On macOS 15 (Sequoia) and later

Apple removed the right-click → Open shortcut. Step 3 above is therefore
different: launch the app normally, let macOS block it, then go to
**System Settings → Privacy & Security**, scroll to the bottom, and click
**Open Anyway** next to the message about Go Cafe. Everything else is the same.

## Reporting problems

If the app misbehaves, there is a log that makes it much easier to diagnose.
Copy it into a bug report:

```
~/Library/Containers/app.gocafe.gocafe/Data/Library/Application Support/app.gocafe.gocafe/gocafe-session.log
```

It records the app's conversation with the Go server for the current session. It
does not contain your password.
