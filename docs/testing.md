---
title: Testing and other apps
nav_order: 7
---

# Testing and other apps

Deck Director isn't tied to Hangar Control. Anything that can send a UDP datagram or a line of text over TCP to `127.0.0.1:41555` can switch your decks.

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
