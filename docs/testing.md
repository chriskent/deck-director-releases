---
title: Testing and other apps
nav_order: 7
---

# Testing and other apps

Deck Director isn't tied to Hangar Control. Anything that can send a UDP datagram or a line of text over TCP to `127.0.0.1:41555` can switch your decks.

## The Deck Director Console

Start menu › Deck Director › **Deck Director Console** opens a page in your browser for setting up and testing messages. Nothing is sent anywhere but your own PC.

- **Status:** whether Deck Director is answering, its version, and the address and port it listens on.
- **Decks and profiles:** every deck Stream Deck knows, whether it's connected, and what it's showing. Under each deck are its profiles, each with an **Adopted** switch. Turning a switch on or off adopts or releases that profile, closing and reopening Stream Deck. Decks that aren't connected are folded away at the bottom. Each deck has a **filter**: `*` matches any run of characters and `?` one character, so `GA-*` shows profiles starting GA-, and `*C172*` any with C172 in the name. Text without `*` or `?` matches anywhere in the name, and case doesn't matter. The count beside it shows how many are listed, such as *3 of 19 profiles*. Filters are remembered in your browser.
- **Message builder:** choose a **Device** (or the last used deck), a **Profile** (or the current one) and an **Action**, such as a page from that profile's list, next, back or home. The full message appears ready to **Copy** into Hangar Control or a script, with the host, port and protocol to use. **Send** tries it over UDP or TCP and shows the reply.

The console stops by itself 10 minutes after you close the page. Start it again from the Start menu.

## The test tool

Start menu › Deck Director › **Send a test message** (also in the download as `Send a test message.cmd`). Type a message and press Enter; the reply appears underneath. Start with `ping`, then `list`, then `page:+1`. An empty line finishes.

`list` groups everything by deck: what each deck is showing, the profiles Deck Director can switch, and the profiles not adopted yet.

## From PowerShell

Open PowerShell and paste one of these as a single line. Change the message between the quotes after `$m=`.

**UDP**

```powershell
$m='page:+1'; $u=New-Object Net.Sockets.UdpClient; $u.Client.ReceiveTimeout=3000; $u.Connect('127.0.0.1',41555); $b=[Text.Encoding]::UTF8.GetBytes($m); [void]$u.Send($b,$b.Length); $e=$null; [Text.Encoding]::UTF8.GetString($u.Receive([ref]$e)); $u.Close()
```

**TCP**

```powershell
$m='page:+1'; $c=New-Object Net.Sockets.TcpClient('127.0.0.1',41555); $s=$c.GetStream(); $s.ReadTimeout=3000; $w=New-Object IO.StreamWriter($s); $w.WriteLine($m); $w.Flush(); (New-Object IO.StreamReader($s)).ReadLine(); $c.Close()
```

The reply appears underneath. A red error about a timeout or a refused connection means no reply came back: check that Stream Deck is running, Deck Director is installed and the port is right.

Messages with spaces are fine: `$m='device:Stream Deck + XL; profile:HC Test; page:AVN'`. If a name contains an apostrophe, type it twice: `$m='profile:Chris''s Deck; page:1'`.

## From your own software

- **UDP**: send the message as one datagram, UTF-8. The reply comes back to the sending port.
- **TCP**: connect, send the message followed by a newline, read one line back. You can keep the connection open and send more lines.

Python, for example:

```python
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.settimeout(3)
s.sendto(b"page:AVN", ("127.0.0.1", 41555))
print(s.recv(4096).decode())
```

## Changing the port

Edit `%LOCALAPPDATA%\DeckDirector\config.json` and restart Stream Deck. Deck Director listens on `127.0.0.1` only, so other computers can't reach it unless you change `host`.
