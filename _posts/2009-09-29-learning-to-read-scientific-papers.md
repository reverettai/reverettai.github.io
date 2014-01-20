---
layout: post-light-feature
title: Learning to Read (Scientific Papers)
description: "How to parse the terse, unfamiliar language of the scientific paper."
categories: [blog, education]
modified: 2009-09-29
image:
  thumb: reading.jpg
---
Remember that prideful moment when you read your first book to your parents as a child?  I certainly do.  I felt as though I had just entered a prestigious, international club of the literate.  I also thought that I had received a lifetime membership, one that could never be revoked.  Then I encountered scientific papers.  Back to infancy...

Scientific papers are written in rigid, formulaic, and often entirely cryptic jargon designed to prevent untrained intruders from extracting the ideas inside (kind of like an academic walnut).  Of course, the ideas inside are some of the most fascinating, powerful, and recent ones in the collective state of human knowledge, so their's is a code worth cracking.

Unfortunately, learning to read scientific papers is not usually an explicitly taught skill in college.  Apparently, its just expected that you'll pick this up on street corners.  Fortunately for me, <a href="http://www.usc.edu/programs/neuroscience/faculty/profile.php?fid=16">Dr. Michael Arbib</a> has worked this into the curriculum of his CSCI 564 - Brain Theory and Artificial Intelligence course at <a href="http://www.usc.edu/">USC</a>.  This skill is particularly useful in a neuroscience course because neuroscience is an absolute zoo of terminology. Being both a young and extremely fast-paced field, different researchers often label the same brain areas with different names and describe the same core principles with different jargon.  Our first project for 564 involves a careful reading and documentation of a detailed brain model and I thought I'd share my lessons.

<strong>First Pass</strong><br>
Read once for the gist of the idea.  The key goal of this first pass is to determine <em>what is innovative</em> about the author's idea.  Why did they propose this new model?  What does it explain that old ones do not?  Don't sweat the details until the second pass.  With a broad view of how the model works, it will be much easier to evaluate the importance of the details and recognize the relation of individual elements to one another.

<strong>Second Pass: Considering Experiments</strong><br>
Experiments can be relevant to a model in many different ways.  Some act as <em>inspiration</em> for building the model in the first place.  For instance, they might have revealed gaps in older models or introduced entirely unexplained phenomena.  As long as the model is designed with these experiments in mind, they will constitute <em>support</em> for the model.  Another category of important experiments are those with results <em>predicted</em> by the model.  These experiments provide key support for the model because they allow it to be <em>tested with data other than that which was used to build them</em>.  Others might be mentioned only because they are vaguely related or famous in a specified discipline of research and not because they are directly relevant to the model itself.  These are included either (a) for the interest of the reader (optimistic interpretation) or (b) for padding the citation list in a you-cite-me-I-cite-you fashion (realistic interpretation).  For instance, if I'm introducing a new tool for large-scale genomics, I am legally obliged to mention Craig Venter's human genome paper.  So in summary, experiments might be included for:
<ol>
	<li>inspiration/support</li>
	<li>prediction/testing</li>
	<li>reader interest/citation padding</li>
</ol>
<strong>Second Pass: Considering Simulations</strong><br>
Simulations may or may not be relevant, depending on your field, but they are crucial for brain modeling.  One key question to ask: how much of the relevant experimental data available is explicable using various parameter settings for the model?  This will separate data into the explicable and inexplicable.  Inexplicable data doesn't necessarily doom the model to failure.  Certain data may be considered outside the model's area of applicability or be simply left as an open question for future work and refinement.  Its crucial here though to honestly ask yourself: what does this model accomplish?  Can it simulate results that others can't?  Is it faster than older models?  Are its mechanisms more biologically plausible than older models?  One important consideration I noticed in considering brain models is that there are many very powerful computational models of brain function capable of giving the same results.  However, only some researchers build their models with biological experiments in mind and are making an honest attempt to model biological mechanisms.  There are many tasks that the brain performs in one way that we can model with computers in a different way.  Whether you care about biological realism depends on your field and your goals.  Many AI researchers just want to model intelligent decision making and could care less how biological their models are.  However, a computational neuroscientist trying to build models of the brain better look to an experiment or two.  So in summary, ask yourself:
<ol>
	<li>what data is explained by the simulations?</li>
	<li>what data is left unexplained by the simulations?</li>
	<li>does this unexplained data doom the model?</li>
	<li>how do the simulation results compare to related models?</li>
</ol>
<strong>Second Pass: Considering Related Models</strong><br>
Many models are simply extensions of old ones.  They add a new level of detail or a new mechanism to lets them explain more data.  Sometimes the goal is to more accurately explain old data.  Other times the goal is to incorporate qualitatively new data.  Still other times the goal may be to update the mechanisms to make them more realistic given new experiments or data.  In summary, good questions to ask are:
<ol>
	<li>which model(s) served as a basis for this model?</li>
	<li>how does this model improve upon related models (i.e. why was it introduced in the first place)?  speed?  explanatory power?  realistic mechanisms?</li>
</ol>

Feel free to add your own lessons in the comments!