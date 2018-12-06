+++
date = 2010-02-26T16:34:00.000Z
title = "MassTexter Follow Up"
draft = false
+++


<div><p>So, it&#8217;s the end of the week, and I thought I would write some follow up information on the masstexter.</p>
<p>I got the masstexter up and working Thursday night; we used it for all of PyCon.
With ten people using it we had a really high response rate&#8212;people generally got the message sent to them within seconds of someone sending a message out. I left the code sending the message to everyone in the list&#8212;including the sender&#8212;so as to maintain some sort of confirmation that the message was sent. But at $0.03 a text, I removed that feature. With the feature, pretty heavy usage of the texter ran a cost in three days of about $60. That&#8217;s about 180 uses with ten users. Without the confirmation message, that would go up to about 200 uses.</p>
<p>The application turned out to very useful&#8212;we had planned on using a chatroom on our company VPN for communication, but given some pretty prevalent wifi issues we ended up falling back on the masstexter more than I had planned.</p>
<p>Towards the end of the con, I threw in another modification, though we never had too much need for it; if someone not in the masstext database sends a message, it doesn&#8217;t pass that message on. I realized that if someone got ahold of the twilio number, they could easily spam all of us without any penalties, driving up the cost of the application and irritating everyone. That change was pushed up to <a href="http://github.com/jaycee/masstext">github</a>.</p>
<p>I&#8217;m looking into some other features as well; chief among these is some sort of grouping feature, and usage of an asterix server to cut down on the costs of sending messages out.</p>
<p>I&#8217;m also considering what license to push this out under; something better than the informal &#8220;it&#8217;s on github, feel free to play.&#8221; If anyone has recommendations, let me know&#8212;otherwise I&#8217;ll probably default to the BSD License or similar.</p></div>