---
title: The Long Journey of Server-Sent Events (EventSource)
authors:
- anne-van-kesteren
tags:
- eventsource
- html5
- testsuite
- coreblog
license: cc-by-3.0
---
Over six years ago Ian Hickson wrote up a proposal for <a href="http://ln.hixie.ch/?count=1&amp;start=1083167110">Server-sent DOM events</a>. This feature allowed for creating a persistent connection with the server over HTTP and let it stream updates to the page as DOM events. News tickers, stock updates, and all kinds of other use cases would be a lot easier to implement. It became part of something that is now known as HTML5 and we prototyped an implementation and shipped it in Opera 9.<br/><br/>The specification however was really quite complex and our implementation not entirely complete. Based on feedback from Jonas Sicking the feature was <a href="http://lists.whatwg.org/htdig.cgi/whatwg-whatwg.org/2009-February/018660.html" title="eventsource/RemoteEventSource wierdness">redesigned</a> to no longer be based on an element, but rather a simple object — much like <code>XMLHttpRequest</code>. Feedback before that had already drastically simplified the event stream format so no longer each and every feature of a DOM event had to be supported. The <code>EventSource</code> object also moved out of HTML5 into its own <a href="http://dev.w3.org/html5/eventsource/">Server-Sent Events</a> specification.<br/><br/>When WebKit gained an implementation of this feature we thought we should update our experimental version so less special casing by developers would be needed. I wrote a <a href="http://tc.labs.opera.com/apis/EventSource/">test suite for <code>EventSource</code></a> and Pablo Flouret then went to update our implementation which resulted in quite a bit of code removal :hat: (We love code removal.) Our work can be found in the <a href="http://my.opera.com/desktopteam/blog/2010/10/11/websockets">latest Opera 10.70 snapshot</a> and will most certainly make it into Opera 10.70 final as well. The test suite will be contributed to the W3C WebApps WG and has already been shared with WebKit developers.<br/><br/>Now we have two implementations — i.e. one in Opera and one in WebKit — that are very close to each other and six years of experience with the feature, the Server-Sent Events specification can finally become a standard. :beer:
