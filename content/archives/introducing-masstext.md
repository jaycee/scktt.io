+++
date = 2010-02-21T06:50:00.000Z
title = "Introducing MassText"
draft = false
+++


<div><p>This past weekend, I was at PyCon. My entire department went, which led to some communication difficulties. While we all had each other&#8217;s mobile numbers, text messages and phone calls were requiring a phone tree system, which was both lossy&#8212;not everyone got the messages&#8212;and really inefficient.</p>
<p>Not to mention irritating.</p>
<h3>Programming to the Rescue</h3>
<p>Fortunately, <a href="http://twilio.com">Twilio</a> recently released an SMS service, which makes programming SMS powered web apps really simple. With a little django power, I was able to put together a simple webapp that can accept an SMS and send it on to a number of other people.</p>
<h3>MassText</h3>
<p>Unoriginally, I&#8217;ve entitled the project MassText. It&#8217;s a surprisingly simple application&#8212;only one model, only one view (plus a little love from <strong>contrib.admin</strong> and <strong>contrib.auth</strong>). The model stores a phone number and who owns said number; the view handles the send and receive via Twilio.</p>
<p>The basic process works like this:</p>
<ul><li>An SMS is sent to a Twilio number.</li>
<li>Twilio sends a <strong>POST</strong> to the masstext view.</li>
<li>The masstext view: </li>
<li>
<ul><li>pulls the other users in the list</li>
</ul></li>
<li>
<ul><li>creates a Twilio XML response containing the original sms message for each user.</li>
</ul></li>
<li>
<ul><li>Sends the response to Twilio</li>
</ul></li>
<li>Twilio sends the defined SMS messages to all users.</li>
</ul><p>Like I said, simple.</p>
<h3>I Wanna Play Too!</h3>
<p>I&#8217;ve put the code up on <a href="http://github.com/jaycee/masstext">github</a>. I&#8217;ll be adding official licensing and working on better features in time. Feel free to take a look and set it up yourself.</p></div>