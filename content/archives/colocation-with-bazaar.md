+++
date = 2012-03-09T21:40:00.000Z
title = "Colocation with Bazaar"
draft = false
+++


<div><p>(<strong><em>UPDATE GUYS</em></strong>: I fixed the problem outlined in this post. Please go ahead and finish reading it, but then <a href="http://blog.humanmade.org/post/19410890644/colocation-with-bazaar-the-glorious-fix">go here</a> to read about what was missing.)</p>
<p>I use Bazaar (bzr) for work. On just about everything else, I use git. I like
both&#8212;for very different reasons&#8212;and basically just use whichver one the code
I&#8217;m working on is primarily available. So work, bzr, and side projects (which
began on github), git.</p>
<p>The only real oddity this creates for me has to do with branching. Git
colocates its branches by default. You have one working directory, and the
contents of that directory may change as you switch between branches. All the
history and metadata about the branch is hidden away in the .git directory.</p>
<p>Bazaar puts each branch in its own directory&#8212;switching branches means
changing the directory you&#8217;re in, rather than changing the contents of your
current directory.<sup id="fnref:p19018238488-1"><a href="#fn:p19018238488-1" rel="footnote">1</a></sup> This is actually a really good system for the novice
DVCS user. New branches are new directories, what could be simpler? But if
you&#8217;re used to branching in git (or mercurial for that matter) it&#8217;s a little
weird.</p>
<p>To address this, there&#8217;s a plugin named bzr-colo. Bzr colo lets you work with
branches the way you would with other DVCSes. Since for work I use a shared
repository with a ton of little branches, I thought setting up a single
directory with colocated branches for launchpad work would be cool.</p>
<h3>The experiment</h3>
<p>Setting things up seemed pretty easy.</p>
<pre><code>bzr branch lp:launchpad ./devel
cd devel
bzr colo-ify
</code></pre>
<p>I also added some stuff in my <code>locations.conf</code> so <code>bzr push</code> and the like
worked properly.</p>
<pre><code>[/home/jc/Code/launchpad/devel/.bzr/branches]
public_branch = bzr+ssh://bazaar.launchpad.net/~jcsackett/launchpad
public_branch:policy = appendpath

push_location = lp:~jcsackett/launchpad
push_location:policy = appendpath

submit_branch = /home/jc/Code/launchpad/devel/.bzr/branches/devel/
submit_to = merge@code.launchpad.net
</code></pre>
<p>This sort of echoes the setup of our shared repo setup as established by our
<a href="http://bazaar.launchpad.net/~launchpad-pqm/launchpad/devel/view/head:/utilities/rocketfuel-setup">recommended setup</a>. I had to rename the default branch in my colocated
directory as well, since bzr-colo wants to call it trunk.</p>
<p>With this setup, I started a new branch with <code>bzr colo-branch</code> and got to
work.</p>
<h3>The results</h3>
<p>For the most part, things worked as I expected. I was able to <code>bzr pull</code> into
devel, and bzr merge from it into my current branch. <code>bzr push</code> worked as
expected too. Everything seemed groovy.</p>
<p>Then I hit my one snag.</p>
<p>I attempted to submit my branch for code review using <code>bzr lp-propose</code>. Sadly,
the branch I was evidently proposing against was
lp:~jcsackett/launchpad/devel, rather than lp:launchpad.</p>
<p>I&#8217;m pretty sure this is a problem in my locations.conf; I will be the first to
admit I don&#8217;t know entirely what all of those settings mean, or how they are
used. I hope to get that problem sorted and go back to using this setup
soon, and will post a follow up when I do.</p>
<div class="footnotes">
<hr /><ol><li id="fn:p19018238488-1">
<p>For the most part, that is. Bazaar has <em>lots</em> of options, and with
lightweight checkouts and shared repositories you can end up with a single
working directory you switch in, but the branches are still all separate ones
at the same layer in the file tree. It&#8217;s handy, but gets confusing. <a href="#fnref:p19018238488-1" rev="footnote">↩</a></p>
</li>
</ol></div></div>