---
layout: post-light-feature
title: The Zealot King Problem & An Operational Version of Rice's Theorem
description: "Musings on Turing machines inspired by Sipser's 'Introduction to the Theory of Computation.'"
categories: [blog, science]
modified: 2010-05-15
image:
  thumb: king-solomon.jpg
---
<img class="aligncenter size-full wp-image-680" title="religious king" src="http://djstrouse.com/images/king-solomon.jpg" alt="religious king" width="382" height="500" />

<strong>The Zealot King Problem</strong><br>
Let's say you're the king of a far-off land inhabited by Turing machines.  As a highly religious king, you have strict morals and lately, you've been frustrated to see many of your citizens acting immorally.  You've been especially aghast at their frequent and flagrant violation of restriction R. Restriction R isn't a law, but you simply find its violation morally repugnant.  Your department of mad scientists has shown that Turing machines operating under restriction R are just as powerful as those that don't, so you don't feel bad about taking away your citizen's privileges to break restriction R. Thus, the religious zealot you are, you do it; you declare a law that no Turing machine may violate restriction R <em>on any input</em>.

Now you need to enforce your law.  You need to make a Turing machine police force that runs around testing passerbys to see whether they are upstanding, R-abiding Turing machine citizens.  Can you do it?

<strong>Further Motivation for the Theoretical CS Junkie</strong><br>
After an awesome course in mathematical logic with Len Adleman at USC that flirted with issues of computability, I've been addicted to theoretical CS textbooks, including Michael Sipser's excellent <a href="http://www.goodreads.com/book/show/400716.Introduction_to_the_Theory_of_Computation_Second_Edition">Introduction to the Theory of Computation</a>.  One exercise (5.28) introduces <a href="http://en.wikipedia.org/wiki/Rice's_theorem">Rice's theorem</a>, which states that the question of whether or not a Turing machine's language has some non-trivial property is undecideable.  But this only holds for "linguistic" properties - those of the Turning machine's language.  You might wonder (at least I did), what about "operational" properties?

Certainly there are some operational properties we can decide.  Does [insert your favorite Turning machine here] move left on step 6 for any input of length 10?  Beats me, but I could sure simulate your Turing machine for 6 steps on each of the n^10 strings of length 10 (where n is the number of symbols in your tape alphabet) and check.

But there are plenty more operational properties that we <em>can't</em> decide.  I was interested in identifying the conditions that make an operational property undecideable, and I've at least found a sufficient set.

I post this little result here for several reasons:
<ol>
	<li>Someone has very likely already cooked up a much tighter solution to this (or a similarly stated) problem already. Â If anyone reading this knows of such work, please point it out!</li>
	<li>I'm a TCS noob and would love for someone to prove my conditions wrong.</li>
	<li>Is there a more general set of conditions than the ones I give? Â Are there other more interesting tweaks to Rice's theorem? Â Any ideas here are welcome.</li>
	<li>I'm a <a href="http://www.thisiscolab.org/">sucker for open science</a>.</li>
</ol>
<strong>Formalism & Proofs</strong><br>
First, let's define two conditions that the restrictions we will consider must have.
<blockquote><span style="text-decoration: underline;">Definition 1</span>: A restriction R is "gentle" if for every Turing machine T, there exists another Turing machine T2 that operates under the restriction R and recognizes the same language as T.</blockquote>
In other words, R does not reduce the power of Turing machines.
<blockquote><span style="text-decoration: underline;">Definition 2</span>: A restriction R is "non-expiring" if, given any Turing machine T and input w, there does not exist a number of steps N such that if T has run for N steps on w without halting, it is no longer possible for T to violate R.</blockquote>
In other words, R can be violated at any point in a computation and there is nothing a Turing machine can do to "lose" the opportunity to break R, besides halting.
<blockquote><span style="text-decoration: underline;">Lemma</span>:  Given a "gentle" restriction R, it is possible to create a Turing machine S that never violates R and upon input &lt;T,w&gt;, where T is a Turing machine and w is some string in the tape alphabet of T, S simulates T on w.</blockquote>
<em>Proof</em>:
Its well-known that we can create a universal Turing machine U that given inputs of the type &lt;T,w&gt; simulates T on w (if you don't believe me, go try to do it yourself or check out <a href="http://en.wikipedia.org/wiki/Universal_Turing_machine">Wikipedia</a>).  By the definition of "gentle", we can also create U2 that operates under restriction R and for inputs &lt;T,w&gt;, simulates T on w. This U2 is our desired S.
<blockquote><span style="text-decoration: underline;">Theorem</span>: Given a "gentle" and "non-expiring" restriction R, the language BEHAVED = {&lt;T&gt;: T is a Turing machine that does not violate R on any input} is undecideable.</blockquote>
<em>Proof</em>:
We'll prove this by reduction to the halting problem, described by the language HALT={&lt;T,w&gt;: T is a Turing machine and T halts on w}.  That is, we'll assume we have a Turing machine deciding BEHAVED and build one that decides HALT.

Let B be a Turing machine that decides BEHAVED.  Construct the following machine H that decides HALT.

H= "On input &lt;T,w&gt;,
<ol>
	<li>Construct the following machine N. Â On any input x,
<ol>
	<li>Run R-abiding simulator S (from the lemma) on &lt;T,w&gt;.</li>
	<li>If S accepts, violate R and halt.</li>
	<li>If S rejects, violate R and halt.</li>
</ol>
</li>
	<li>Run B on &lt;N&gt;.</li>
	<li>If B accepts &lt;N&gt;, reject &lt;T,w&gt;.</li>
	<li>If B rejects &lt;N&gt;, accept &lt;T,w&gt;."</li>
</ol>
If S halts (accepts or rejects), N violates R and halts. If S doesn't halt, N never violates R and doesn't halt. So N violates R if and only if S halts. By definition, S halts if and only if T halts on w. So N violates R if and only if T halts on w. Also, by definition, B accepts &lt;N&gt; if and only if N <em>does not</em> violate R for any input. So B accepts &lt;N&gt; if and only if T <em>does not</em> halt on w. So by steps 3 and 4 of H's description, H decides HALT.

<strong>Justification of "Gentle" and "Non-Expiring" Conditions</strong><br>
I needed the "gentle" condition for the lemma. Â If the restriction actually reduces the power of Turing machines, the above method of building some Turing machine simulator that operates under that restriction and only violates it to signal some particular situation (i.e. halting) won't work, since the simulator won't be universal.

I needed the "non-expiring" condition to make sure that when S finishes simulating T on w, its still possible for N to violate R. Â This condition kicks out those easily decideable restrictions that I mentioned earlier.

Any suggestions on tweaking these conditions are welcome.

<strong>Some Examples of "Gentle", "Non-Expiring" Restrictions</strong><br>
Turing machines are robust little guys and we can come up with plenty of plenty of restrictions that won't reduce their power.  Here are some examples mostly adapted from Sipser's text:
<ul>
	<li>Only move left to "reset" like a typewriter (that is, if you want to move left, you have to go all the way to the left edge of the tape and then work your way to the right again).</li>
	<li>No writing on multiple tapes (for instance, we could lay out several tapes to "tempt" a Turing machine, then demand that it only use one).</li>
	<li>No exploiting non-determinism (similarly to the multi-tape case, we could give a Turing machine the option of "branching", then demand it not do so).</li>
	<li>Alter each tape square only once.</li>
	<li>No using squares of a doubly infinite tape to the left of some given square (that is, we give a Turing machine a doubly infinite tape, then demand it not cross a certain boundary, effectively restricting it to the usual semi-infinite tape).</li>
</ul>
I'm sure you can come up with many more and feel free to share your favorites.