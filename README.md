Download Link: https://assignmentchef.com/product/solved-comp341-assignment-4
<br>
<span class="kksr-muted">Rate this product</span>

Part 1: Programming

You are going to do the 11 (Q0-Q10) programming questions about reasoning over time given in the website. You are only required to change bustersAgent.py and inference.py. If you have any issues with other parts of the code let your instructor or TA know ASAP, even if you manage to solve your problem. If you think you have the right answer but the autograder is not giving you any points, try to run it on individual questions (examples on how to do this is given in the website).

1

Hints

The first 8 programming questions are fairly straightforward especially if you paid attention in class. Furthermore, both the website and the code comments include a lot of hints so make sure you read them!

Website and the Comments

I cannot stress this enough so I am just going to repeat. This homework has a lot of guidance, both in its webpage and in the code comments. I suggest you read them carefully.

Getting an error related to cgi.message If you get this exception, go to the corresponding file and add import html. Then change cgi.message to html.message. This would happen if you upgraded your Python version.

The DiscreteDistribution Class Be careful during normalization when the total is 0! Otherwise, you might get a divide-by-zero exception later on. Also, the doctest for sampling assumes you normalize within the sample function. This is not necessary if you always normalize before. If you do not want to normalize within the sample function you can add a dist.normalize() to the doctest comments. However, make sure you normalize before any sampling steps later on in the code! Also, do not forget to normalize any distributions you calculate as a final step.

Exact Inference

There is really nothing to hint at other than what is given in the website. One minor warning is to pay attention to the time elapse loop. The required summation can happen “out of sequence”. Also pay attention to jail positions, make sure to set probabilites for all the states (if a ghost is in jail, corre- sponding probability will be 1, all the other states will have 0 probability).

Uniform Initialization of Particles

As stated in the comments, do not initialize randomly (even with a uniform distribution!) but do it uniformly. Imagine I give you 10 slots and 100 balls. How would you fill those slots uniformly? Find the number of particles per ghost position you need to have and take it from there. There are cases analogous to having 104 balls for 10 slots. I leave it up to you to deal with the remainder (i.e 4) as you like, random is fine. A piece of information; the number of particles is typically much bigger than the legal ghost positions.

Particle Weight Representation and Particle Resampling

You may find it easier to use the DiscreteDistribution() class to keep track of particle weights instead of having another list. This will be indexed by the ghost positions. However, we have more particles than these positions. I leave it up to you to figure out how to deal with this in case you chose this. Note that this data structure can represent any number given an index in general, they do not have to be probabilities.

Note that you need to resample after updating the particle weights in the observeUpdate() method of the ParticleFilter class. The advantage of using the DiscreteDistribution() data structure is that the existence of the DiscreteDistribution.sample() function. Be careful about normalization.

You can always use another list or keep a combined list for the weights, in which case you will need to implement another sampling function.

Dynamic Bayes Nets

When you are done with the first 8 (Q0-Q7) questions, I suggest you take a break and answer the relevant questions in your report before working on these last 3 questions. I do not want to spoil all the fun for when you get back. So I will only briefly mention a few things.

For this part, a particle will include positions of two ghosts. The emission models are for individual ghosts. To get a particle weight, you need to multiply the emission probabilities together. Each ghost will also have its own jail cell. If a ghost is in a jail cell, then its emission probability becomes 1 for the jail location.

In the previous cases, a ghost had legal positions which you used to pick uniformly distributed particles. In the DBN case, this gets slightly tricky. Think carefully about what you need to pick from. We will give a small example without explaining it:

Let {(1,3),(2,2),(2,3)} be a list of legal positions. Assuming that two ghosts cannot be in the same position, you need to pick from {[(1,3)(2,2)],[(1,3)(2,3)],[(2,2)(1,3)],[(2,2)(2,3)],[(2,3)(1,3)],[(2,3)(2,2)]}.

2

The website is suggesting a solution using the itertools package. It also recommends to shuffle the resulting permutations. If you pass all the tests but the first one for Q8, lack of shuffling may be the culprit.

Note that the observations for the DBN part is multi-dimensional, based on the number of ghosts. Getting the unhashable type error If you get an unhashable type error, go and look at the way you represent your particles. In Python, lists are not hashable (since they are mutable) but tuples are (since they are immutable).

Part 2: Report

This part includes answering the following questions based on your program’s output on the given pac- man tests. You are expected to answer the questions concisely. Five sentences is more than enough for most of them. Limit yourself to 300 words. It is okay if you over-generalize, as long as your direction is clear and correct.

Create a PDF file named report.pdf containing your answers for submission. Write your name and your number on the report as well!

Written Q1:

Run the autograder on Q3 and watch the probabilities. Why do they settle even though the ghost is moving? Can you tell the two ghosts apart and if so how? (Hint: Run these test cases q3/1-ExactPredict, q3/2-ExactPredict, if you need to observe them individually)

Written Q2:

Try the following lines of code and watch the probabilities settle:

python autograder.py -t test cases/q2/2-ExactUpdate python autograder.py -t test cases/q2/3-ExactUpdate

Why is it the case that in one of them we can find the ghost but not in the other one?

Written Q3:

Run the autograder on q6 for the 5th and the 6th test case and watch the probabilities. Can you tell when the particles get re-initialized? Comment on the reason(s) on why pacman gets in that situation? Would increasing the number of particles be a solution?

Written Q4:

Compare how the probabilities evolve between the exact inference and the approximate inference cases (Q2, Q32 vs Q5, Q6). Also comment on if 5000 particles make sense for the problems you have seen.

Written Q5: