---
layout: post-light-feature
title: The Statistics of Recipes (RecipEntropy)
description: "Of all possible combinations of ingredients, only a small fraction are used as recipes. What's special about those combinations?"
category: articles
tags: [statistics, recipes, information theory, entropy, culturomics]
image:
  feature: gatsby.jpg
---

<i>With: Ari Strandberg-Peshkin & Kelsi Lindblad</i>

This project started with a riddle:

<i>Can you think of a set of three types of food, in which each pair of foods tastes good together, but the combination of all three does not taste good?</i>

This riddle is harder than you might expect, and, ultimately, I have yet to hear a satisfactory answer (but if you think you have a candidate, please email me!).

Subjectivity in what "tastes good" aside, this riddle begs the question: can you construct recipes simply by combining ingredients that taste good as pairs? Or are there situations in which these pairwise relationships are not enough to predict the quality of a recipe?

Perhaps surprisingly, these questions can be formalized in a rigorous, quantitative way. Using the framework of maximum entropy modeling, we can ask how much of the information contained in the distribution of recipes is accounted for by pairwise interactions alone, and how much depends on triplet, quadruplet, or even higher order interactions. Using a database containing over 50,000 recipes (and over 300 ingredients), we are attempting to answer these questions. 

Maximum entropy modeling allows us to construct a model of the distribution of recipes that contains the minimum amount of information (and therefore the maximum amount of entropy), while constraining the overall frequencies of ingredients and the correlations between ingredients. 

We hope to use this framework to figure out how much higher order interactions between ingredients matter, to search for answers to the riddle that inspired us, and hopefully to predict (and synthesize in the "lab") some novel recipes!
