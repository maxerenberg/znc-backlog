znc-backlog
===========

This is a fork of [znc-backlog](https://github.com/FruitieX/znc-backlog), with the following changes:

* The logs directory path is automatically determined from the log module. The network-loaded directory will
be searched first, then the user-loaded, then the
globally loaded (see [here](https://wiki.znc.in/Log#Arguments)).
* The LogPath command no longer exists. This prevents users from reading arbitrary file paths, e.g. User A reading the logs of User B.

**Note**: This forked module will not work for ZNC versions prior to 1.6 as the log paths are different.

znc-backlog is a ZNC module that makes it easy to request backlog. Its intended
use is for when you have just launched your IRC client and gotten a few lines of
backlog sent to you, but want to read more. Instead of having to deal with
shelling into the box where you run ZNC and manually sifting through the logs,
you can issue a short command in your IRC client to request any amount of the
most recent lines of log.

Dependencies
------------

Requires make and znc-buildmod to build (should come bundled with ZNC)

Compiling & Installing
----------------------

	git clone https://github.com/FruitieX/znc-backlog
	cd znc-backlog
	make
	cp backlog.so /path/to/znc/modules/

Usage
-----

After the module is loaded, you can request for logs with:

	/msg *backlog <window-name> <num-lines>

A handy alias for weechat:

	/alias bl msg *backlog $channel $1

Now you can:

	/bl 42

to request 42 lines from the current window or just:

	/bl

to request the default amount (150) of lines from the current window.

TODO
----
- Optimize?
- Server-time for timestamp, http://ircv3.org/extensions/server-time-3.2
- make install rules (see kylef's plugins)
- CDir instead of opendir(), see FileUtils.h
- see how timestamps are created in buffer playback code
- investigate '\*' lines in XChat server window, maybe random space somewhere?
