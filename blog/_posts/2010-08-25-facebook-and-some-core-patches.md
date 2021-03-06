---
title: Facebook and Some Core Patches
authors:
- ola-kleiven
tags:
- sitepatching
license: cc-by-3.0
---

## Added patches



PATCH-292, Avoid TinyMCE-triggered bug, make adding notes on Facebook work again. Writing several times into an iframe may cause a script deadlock. Will be fixed in Core as well.

PATCH-290, Avoid overflowing table on Salesforce. Temporary patch for a Core regression with overflowing content in relative width tables causing very wide tables.

PATCH-287, Hack to make script see typed value in TEXTAREA on blog.ebuddy.com. Opera fails to read correct value from a previously hidden textarea.

PATCH-286, Avoid throwing JS errors on Hangame.co.jp from CSS hacks. Opera throws when trying to add invalid CSS with insertRule. This causes the script to break down. The proper fix would be to make Opera just drop the rule.

PATCH-285, Enable log-in button on Cambrian bank. Too much sniffing here, but the trigger was that we earlier removed tags() from randomelement.all but not randomelement.all itself (not to be confused with document.all)

PATCH-282, Avoid scrolling down when space key is pressed on monocubed.com. Perhaps not the biggest site, but since <a href="http://my.opera.com/sitepatching/blog/show.dml/15758422#comment37789752" target="_blank">ouzoWTF</a> asked so nicely :)

PATCH-279, Fix URLs with empty port number on form submit. If you have something like

	<form action="http://somesite.com:/path">
		<input type="submit">
	</form>

submission will currently fail. This is a somewhat ugly Core regression that we have fixed, but not released a fix for. It also manifests in other ways, like

	<script src="http://somesite.com:/somescript.js"></script>

will fail to load the script. This patch only solves the form submit part, not the resource loading part.

PATCH-264, Enable @mentions on Facebook. Not going to mention anything about it other than that it will be removed as soon as they fix it.

PATCH-76, Work around sniffing in old BackBase library on ing.nl. Caused missing submit buttons etc.

## Changed patches



PATCH-203, Prevent script scheduler hanging due to triple markup/script insertion into editor IFRAME. Improved patch for the Microsoft forums issues.

## Removed patches



OTW-5801 - walla.co.il draggable interface not working. Site has changed. This was also the last patch that used the massive 240 lines emulateIECapturingEvents code in browser.js, so it is now more lightweight.
