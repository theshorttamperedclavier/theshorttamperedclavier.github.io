---
layout: post
title: "Architecture, Bayes, Computation"
author: Shardul
---

> Sometimes it seems as though each new step towards AI, rather than producing
> something which everyone agrees is real intelligence, merely reveals what real
> intelligence is not.

-- Douglas Hofstadter, _Gödel, Escher, Bach_


In the first week of [9.13 The Human Brain][1], I was introduced to the
now-ubiquitous concept of Marr's three-levels approach to understanding the
human mind. The top level is computational, expressing what outputs are to be
inferred or computed from what inputs, e.g. recognizing the edges of an object;
the intermediate level is algorithmic, describing conceptual routines that can
be carried out to produce the desired results, e.g. the mathematics of a
convolutional edge-detection filter; and the bottom level is implementation,
showing physical hardware that can actually carry out the process, e.g. a group
of neurons connected in the right way with the right activation parameters. The
rest of the class focused mostly on the intermediate level and the tools we
possess to study it, but recently I've been reading and thinking about the
bottom level of hardware.

The substrate of human intelligence is made of neurons. And so far, the
substrate on which we are trying to build computer intelligence is made mostly
of transistors. As von Neumann pointed out over 60&nbsp;years ago in _The
Computer and the Brain_, the two are pretty different: neurons are inherently
noisy and imprecise, being biological systems, and they work with a continuous
range of potentials rather than the discrete ones and zeroes of binary logic,
and communication between them is much slower than electrical impulses in a
wire. Zooming out a little, the physical architecture of the brain involves
billions of neurons interconnected in every which way with only a few
centralized units for special functions, like the thalamus, which is contrasted
with modern chip architecture with organized levels of memory, well-defined
pipelined processing units, and a few communication buses between all the
components. (Computer architecture also dates back to [von Neumann (1953)][2],
interestingly.) Perhaps it is not surprising, then, that to create human-like
intelligence, our research is in the direction of simulating human-like neural
circuitry in digital hardware with neural networks, which end up consuming
quite a lot more power than their native brain counterparts.

This begs the question, why not use electronic hardware that is more like
neurons to begin with? Enter neuromorphic computer architecture. [This paper][5]
(Neftci et al. 2013) is an example of how we would 'program' such a computer
to perform a task like attending to a visual object on a screen and detecting
its motion (quite a different paradigm of programming!), and more references to
the structure of neuromorphic hardware can be found in its bibliography. I don't
find it hard to believe that a good set of abstractions on top of such hardware,
whether engineered for our convenience or adopted from discoveries in the
operation of the brain, can make it much easier to efficiently emulate processes
of perception in electronics. I don't know enough about cognitive processes
outside of perception to say whether the same holds generally.

----

But there is [mounting evidence][14] that a [deeper phenomenon][13] is behind
the intelligent behavior of a mess of neurons: Bayes' Theorem ([an excellent
tutorial][15] suitable for any level of math). It seems that the brain
essentially holds a fairly detailed hypothesis of what the world around it is
like, and all sensory input is counted as evidence in incrementally updating
this hypothesis, and what a person perceives is heavily colored by the
hypothesis/expectation of the surroundings unless sensory input is startling
enough that the hypothesis breaks down. For example, your skin is (probably)
feeling the weight of your clothes constantly, which your brain ignores under
the hypothesis that it is generally what clothes feel like. If you shift
position, the sensory input changes, but it still fits the hypothesis very well;
you probably don't notice that anything changed at all, you still have the same
percept of wearing clothes. However, if a bug drops onto your back, you are
suddenly aware of the weight and crawling movement, because that is definitely
not how clothes typically feel---the hypothesis that there is nothing else on
your body except clothes is abandoned. This exchange between mental models and
sensory input, driven by Bayesian updates of the likelihood of various events
and hypotheses, is conjectured to be a large component of the workings of the
mind.

Explicitly modelling the real world in a Bayesian way is hard. Consider this
example from a [talk][16] I recently attended (which, incidentally, led to me
writing this post). The speaker (Abby Liu) built a map tool that starts out in a
view of, say, the entire United States, and the user wants to end up in a view
of, say, Austin. The traditional way to do this is that the user does a sequence
of zooming and panning actions that the map executes. The speaker asked, what if
the map actively tried to figure out where the user wanted to go? So the map
starts with some prior probability distribution about which cities the user is
most likely to want to go to, say, proportional to population, and instead of
the map responding to the user's inputs, we model it as the user responding to
the map's questions: "If I (the map) zoom in to the Northeast, what do you (the
user) do?" -- "I pan west." -- "Ah, so I have inferred that you do not want to
look at a Northeast city." And so on until the city is reached, the map keeps
updating its probability distribution for where the user wants to go, and asks
questions (by moving the map) that maximize the information gain at each step.
One of the major challenges the speaker mentioned was that this is currently
only practical for a _small, discrete_ range of user actions (say, panning in
one of eight compass directions) and a _small, discrete_ hypothesis space (say,
only major cities) because doing Bayesian updates for more general cases is
mathematically tricky and computationally expensive. Imagine maintaining a
probability distribution over every block in the country, and updating for every
tiny motion of the user's cursor&hellip;

Again, this begs the question, why not use hardware that works with probability
distributions and Bayesian updates to begin with, instead of trying to emulate
that with finicky binary bits and logic gates? This time my 'original idea' is
not that far behind the research curve! Here are some papers describing various
approaches to Bayesian hardware:
+ [Bayes with memristors][6] (Serb et al. 2017). A [memristor][9] is the elusive
  (until this millenium) 'missing element' of electronics, the others being
  resistors, capacitors, and inductors, postulated in 1971 by Leon Chua (not von
  Neumann this time, honestly that would have been too much). As far as I
  understand (which is not very far at all), a memristor's resistance depends on
  how much current has passed through it, so it can be 'set' to 'store' a
  desired resistance than can then be 'recalled' by applying small voltages
  across it and measuring current flow. Serb et al.'s theoretical hardware does
  a sort of matrix multiplication between a vector of priors and a matrix of
  conditional probabilities, using memristors as the multiplicative elements,
  and you should read the (short and mostly simple) paper to understand how this
  works.
+ [Bayes with stochastic computing][3] (Friedman et al. 2016), and a more
  implementation-heavy [paper][4] (Thakur et al. 2016) with a different approach
  that I didn't really understand. [Stochastic computing][17] is a computing
  paradigm in sharp contrast to standard digital electronics, because it relies
  fundamentally on randomness to function: a number _p_ between 0 and 1 is
  expressed as an infinite random bitstream in which each bit independently has
  a _p_ chance of being a 1; two numbers can be multiplied by bitwise ANDing
  their bitstreams; two numbers can be averaged by alternating between their
  bitstreams; etc. Naturally, the result of a computation continually becomes
  more precise as more bits are processed, but the initial bits provide a good
  rough approximation as long as they are truly random. C.f. traditional adders
  that must start with the least significant bits and produce the entire answer
  in one go at the end. To implement Bayesian inference, the first paper uses an
  electronic component called a [Muller C-element][18] that again has a 'memory'
  of sorts, and corresponds very well to the fundamental statement of Bayes'
  Theorem. (In stochastic computing this memory creates 'autocorrelated'
  patterns in the random bit streams (now they remember their own history and
  aren't independent anymore?) that requires some clever math to fix, which is
  beyond me but not beyond the references in the paper.)
+ [Bayes with software optimization][7] (Murray 2013). The author creates a
  software library that compiles a specification of a Bayesian inference model
  into machine code, optimized for the specific high-performance hardware being
  used, such as a GPU. This is not as much a change in hardware substrate as
  writing software really close to that substrate to optimize how it is used.

An aside about stochastic computing: isn't it curious that neurons are also
stochastic, in a way? A passive neuron doesn't just sit there, it merely fires
(randomly) at a much lower rate than an activated neuron. On receiving new data,
neural computation must 'settle' into a decision after a few moments of
activation spike chain reactions. Hmmm&hellip;

Another aside about stochastic computing: it reminded me of [Marshall][10], a
robust real number computation framework (and a [theoretical exposition][19]).
Today's floating-point numbers give rise to today's infamous floating-point
errors, and with digital computers this is in some sense an unavoidable problem,
so Marshall bypasses it by representing a real number as the set of all numbers
smaller than it paired with the set larger than it. As the computation proceeds,
the range can be made smaller/more precise, until it is small enough for the
required application---and Marshall does this in a proven-to-be-correct way. Of
course, this is very different from stochastic computation, but in my head they
have the same flavor of increasing precision and ensuring robustness (tiny
changes in input don't cause unreasonable changes in output).

----

In what other ways can the substrate of computation be changed? Although this is
not what quantum computers do, what about exploiting the quantum mechanical fact
that atoms are really and truly made up of probability distributions (albeit
complex ones), which could be manipulated to perform computations much more
directly than trying to mimic the distributions in bits? What about using light
waves as the fundamental unit of computation, expressing quantities as
frequencies, multiplication as superposition, addition as amplitude modulation,
&hellip;?

But in all the discussion above we have been working towards some nebulous
'intelligence' that we presumably will recognize once we build it. I'd like to
ask the dual question: using this range of computation substrates, _what other
types of intelligence can we create?_ Recognizing an intelligence that is not
sufficiently 'human-like' could be extremely challenging, because we as humans
have never done it before. Eliezer Yudkowsky makes some very good points about
this in [his article][11] about what it really means to imagine an alien
intelligence that I very much recommend reading. To quote, "The only reason you
can try _at all_ to grasp anything as physically complex and poorly understood
as the brain of another human being, is that you configure your own brain to
imitate it. [&hellip;] [But] minds that feel emotions you've never felt
yourself, or that fail to feel emotions you would feel? [&hellip;] I can tell
you to imagine an alien that grew up in universe with four spatial dimensions,
instead of three spatial dimensions, but you won't be able to reconfigure your
visual cortex to see like that alien would see."

Yudkowsky's favorite example of an alien intelligence is
[natural selection][12]. It, as much as 'it' can be considered an entity, does
not operate with a 'purpose', no matter how much most humans thinking about
evolution attribute a purpose to it; genes that _happen_ to mutate to produce
incrementally beneficial changes, just statistically _happen_ to proliferate,
regardless of whether you think the purpose of our eyes is to help us see.
And it takes a great deal of effort and training to be able to reason about
natural selection processes correctly, without anthropomorphizing.

In the same vein, consider the 'intelligence' of a mobile phone, that can
calculate bigger numbers faster than any human, etc. etc. "Ah, but it is not
intelligent", you say, "because it cannot do X Y Z things that a human can." Yet
it takes years of training to be able to understand how it works and write
software that can use its full potential. To most people, its intelligence is as
incomprehensible as is the intelligence of evolution; the student biologist
arguing for why evolution 'should have' selected for a certain mutation is
equivalent to the student programmer writing comments explaining the intended
function of their code and complaining that the compiler seems to ignore them.

What other intelligences exist already, on whatever substrate, that we can learn
from? We've tried simulating neurons in digital electronics; can we gain
anything from simulating boolean logic in neurons? Some things could be
fundamentally difficult for one substrate yet trivially easy for another, just
like some computational constructs are easy in one programming language and
tedious in another. What can we learn from and about these differences?


  [1]: http://student.mit.edu/catalog/m9a.html#9.13
  [2]: https://en.wikipedia.org/wiki/Von_Neumann_architecture
  [3]: https://www.utdallas.edu/~joseph.friedman/Papers/FriedmanBayesianTCAS2016.pdf
  [4]: https://www.frontiersin.org/articles/10.3389/fnins.2016.00104/full
  [5]: https://www.pnas.org/content/pnas/110/37/E3468.full.pdf
  [6]: https://eprints.soton.ac.uk/425616/1/BayesianMachine_v12.pdf
  [7]: https://arxiv.org/pdf/1306.3277.pdf
  [9]: https://en.wikipedia.org/wiki/Memristor
  [10]: https://github.com/andrejbauer/marshall
  [11]: https://www.lesswrong.com/posts/Zkzzjg3h7hW5Z36hK/humans-in-funny-suits
  [12]: https://www.lesswrong.com/posts/pLRogvJLPPg6Mrvg4/an-alien-god
  [13]: https://slatestarcodex.com/2016/09/12/its-bayes-all-the-way-up/
  [14]: https://slatestarcodex.com/2017/09/05/book-review-surfing-uncertainty/
  [15]: https://arbital.com/p/bayes_rule_guide/
  [16]: https://www.csail.mit.edu/event/designing-intelligent-interactive-systems-information-theoretic-perspective
  [17]: https://en.wikipedia.org/wiki/Stochastic_computing
  [18]: https://en.wikipedia.org/wiki/C-element
  [19]: http://math.andrej.com/2008/08/24/efficient-computation-with-dedekind-reals/
