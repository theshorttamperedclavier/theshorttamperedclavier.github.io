---
layout: post
title: "Discovery-Based Learning: in Theory"
author: Shardul
---

*(Disclaimer: there's a huge body of research about this topic, which I do not
pretend to have read; this post is based purely on my experiences and a little
bit of reflective analysis. I'm consequently saying a lot about discovery-based
learning applied specifically to mathematics.)*

What is discovery-based learning?

The key principle of this learning process is that students discover
the material they're supposed to learn by themselves instead of it being
taught didactically as truth. This is fully and intensely collaborative:
students *must* work together to ask questions, make conjectures, present their
ideas and arguments to their peers, and be critical of each other to make
progress. Discussion and exploration is completely free-form.

Of course, students don't start from scratch (measuring learning time in
[decades][1] isn't, in my opinion, exactly optimal). What is provided to them,
and who provides it? In this model of learning, there are no 'teachers' *per
se*; there are no authorities or gatekeepers of knowledge that have the ability
or rights to tell right from wrong or to permit students the privilege of
knowing certain selected truths. Instead, there are 'facilitators' who:
 - provide only hints, only when needed;
 - make sure discussions don't go too far off-track, or equivalently, provide
   some long-term structure to the learning;
 - change the topic when work eventually slows down to prevent it dragging on
   and becoming boring or tiring;
 - catch missteps that the students don't, but only through asking the right
   questions or probing into something the students may have overlooked;
 - and above all, provide---through direct instruction, if necessary, not a
   discovery-based approach---the basic background knowledge and tools required
   to approach the material under consideration.

An example is in order. The objective is the introduction of very basic linear
algebra to students who already know basic algebra concepts, up to, say, how
systems of equations work. Note that a lot of knowledge is implicitly assumed
here, like arithmetic, and it is certainly a bit much to assume that
first-graders will be able to independently discover how to divide arbitrarily
large numbers by hand. In such cases, direct instruction, such as plainly
explaining to said first-graders the process of long division, is vastly more
effective than discovery-based methods.

The facilitator might begin by writing a simple system of equations on the
board and asking students to solve it. The students will do this easily (if not,
they are not ready for the following lesson). Then the facilitator will say:
"Solve the system again, but this time, whenever you perform any arithmetic
operation on the numbers, leave the expression unsimplified. Write '(2 − 5) × 4'
instead of '−12'." Then certain patterns will emerge in the solutions the
students come up with; the facilitator will ask, "Can you generalize? Can you do
the same with variables instead of numbers? Can you think of a way to extend
what you just did, or a convenient way to write it?" Students will most likely
*not* come up with the conventional expression of matrices, or anything
resembling it, but the facilitator should *proceed with whatever the class
decides to be best* until problems are encountered. And so the students and the
facilitator will make their way through basic linear algebra, with discussions
leading to a motivation for matrix multiplication, an investigation of matrices
as linear transformations, and so on.

The example above makes the limitations of discovery-based learning pretty
clear. A complete lesson plan for, say, a two-hour lesson, will clearly take a
large amount of preparation, with a single facilitator having to anticipate what
novelties an entire class of free young thinkers will come up with. (This will
not be sufficient, of course, without the facilitator being able to think on
their feet when something unexpected or derailing does happen.) For
discovery-based learning to work, facilitators have to be exceptionally
capable, both in such interactions with students and in the subject being
learned; training teachers on a large scale to be good facilitators might be
practically impossible because some might just not *get* it, not trust their
students' abilities enough, or not have a thorough understanding of the content.
([How many elementary teachers can motivate the formula for the area of a triangle?][3])

Further, this method of learning takes a *lot* of time. In the hour that
students would take to work their way to a rudimentary concept of a matrix, a
conventional teacher could have spent half an hour explaining matrices, matrix
multiplication, and how it relates to systems of linear equations, and assigned
enough exercises to keep the class busy (and bored) for the remaining half hour.
Discovery-based learning is guided research of sorts, and linear algebra was by
no means invented in an hour or even a decade.

I also mentioned that direct instruction for skills such as long division is
more effective than discovery-based methods. There are actually a bunch of
situations where I think discovery-based methods would do more harm than good:
 - for people just beginning to learn something, like children learning
   arithmetic, where you cannot just give them the [Peano axioms][4] and expect
   them to discover addition no matter how hard you prod because they simply
   lack the required experience for meaningful inquiry
 - for people who don't want to learn and are not motivated to spend their time
   doing academic things in a classroom at all (these may not actually need to
   learn linear algebra anyway)
 - for people who can't learn the same way most people learn because of learning
   disabilities

A final drawback of discovery-based learning is that the overall education can
lack structure in the long term. No matter how advanced a student is in linear
algebra, if they know nothing of [probability theory][5], they will be in a
difficult place if and when their work brings them to machine learning, and the
same can be said of geometry and number theory and... While this can be 'fixed'
with a good facilitator and long-term planning, the education may still lack the
structure required to e.g. adhere to a state curriculum, and for students
without a clear idea of what they like/want to explore further, a broad exposure
is essential along with in-depth discovery.

Now that I have presented the disadvantages without any empirical basis, you
must permit me to present the advantages in similar fashion. (For some reason
the former are much easier to digest than the latter though they are on the
same (non-existent) empirical footing. Anyway.)

First, students are *active* in the learning process and must *do* something to
learn, because knowledge is being generated by them and not handed to them. As a
result, even if they don't remember the details of a result years later, they
possess the tools and contextual information to re-derive it when needed,
because it's much easier to remember "oh we used to write the coefficients on
left and variables in a column and then use the jelly-bean method to find the
inverse ahaha I wonder why we called it 'jelly-bean'" than "x' = ax + by,
y' = cx + dy, d = ad − bc, ..." Questions like "why are matrices multiplied so
funny?" don't come up after discovery-learning because everything is deeply
motivated by context, not by 'just so' arbitrary manipulation of symbols.

It's worth noting that these skills---identifying what sort of previous
knowledge will be helpful for a problem and recollecting or researching this
knowledge---are key to solving problems. Although the chapters of a mathematics
textbook may depend very little on each other, the ideas and strategies in
mathematics, or any subject for that matter, keep recurring in various forms.
Discovery-based learning teaches problem-solving by exposing students to these
ideas and strategies first-hand and enabling retention.

Another consequence of active learning is that students feel like they've earned
their knowledge and their education, and they own it, instead of leasing it from
the authorities producing it via some magical process. The effort put into
gaining understanding makes knowledge and education valuable in itself just like
pocket money from washing the car is more valuable than an allowance (I never
received either). So students will want to keep learning by themselves, perhaps
even helping others learn just like they helped each other learn in the
classroom, and above all, they will know on what rigorous basis they should
accept or reject information outside the classroom; if you corner elementary
schoolchildren whose class has discovered the formula for the area of a triangle
and tell them that the area of a triangle is actually a third of the product of
its base and height, they should argue with you because it's not
[just something the higher-ups say][2], it's *real*, they *found it themselves*.

Responsibility for knowledge isn't just for the individual. As ideas are freely
exchanged, challenged, and verified in discovery-based learning, a group of
students as a whole feels responsible for their coëducation, encouraging
commitment to the shared goals of the group and responsible contributions to
that effect. And if you're working in a group, you can't be a snob or a
condescending know-it-all or an excessive introvert or a misunderstood genius
because you *have* to explain your ideas to everyone else and convince them and
listen to their ideas and inspect them for watertightness or otherwise you won't
be part of the fun at all. Interpersonal skills extend to interacting with the
facilitator too, who gets to know each student much better than in a traditional
classroom.

I guess if facilitators and students keep the goals in mind and make sure
they're compatible with discovery-based learning, it's an excellent method to
teach mathematics and probably many other things. In theory. Before drawing
conclusions from a theoretical standpoint, we should see what happens in
practice... (to be continued)

 [1]: https://en.wikipedia.org/wiki/Linear_algebra#From_the_study_of_determinants_and_matrices_to_modern_linear_algebra
 [2]: https://en.wikipedia.org/wiki/2_%2B_2_%3D_5
 [3]: https://www.maa.org/sites/default/files/pdf/devlin/LockhartsLament.pdf
 [4]: https://en.wikipedia.org/wiki/Peano_axioms#Formulation
 [5]: https://en.wikipedia.org/wiki/Probability_theory
