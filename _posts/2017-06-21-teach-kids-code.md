---
layout: post
title: Teaching Kids to Code
author: Shardul
---

This is probably a topic that has been extensively discussed by people much more
qualified to discuss it than I am, but I still felt like trying to argue for my
own take on it, hence this post.

What qualifies me to write this anyway? I started learning to code around the
end of 6th grade and have been coding since then, learning computer science in a
very fragmented way from multiple online sources in the process. In fact, most,
if not all, of my programming knowledge comes from Internet tutorials and
language documentation. In high school I have not taken (and do not plan to
take) a single programming or 'computer science' class. And I don't want to
boast or brag here, but for many of my peers, Mandar and I were the go-to
resources for programming help, which meant that I got a good idea of what sort
of questions or problems they usually had and what thought processes generated
them; I had a similar and more consistent experience when I informally coached a
few of my friends for the AP Computer Science A exam in April 2016.

In this post I point out a number of things that can be improved with
programming and computer science education, but I do wish to make it clear that
the problems lie with the curriculum and not necessarily with the teacher. Our
school computer teacher was a really good teacher---one of my favorites, even
though I had hardly had a class with her, because she used to be involved in
many of the outside-class programming activities we did---and it's not her
fault, or any teacher's fault, that programming education is so bad. Who should
be blamed is an entirely different question entangled in politics that I don't
want to talk about.

With that long preamble, I'll move on to the actual topic.

Firstly, CS/programming isn't for everyone. It is true that anybody
can learn to code, especially with resources like the excellent [Khan Academy
programming course](https://www.khanacademy.org/computing/computer-programming),
[Code.org](https://code.org/) (which I haven't tried out but have heard is
pretty good), [Codecademy](https://www.codecademy.com/), and a whole host of
[easy](https://docs.python.org/3/tutorial/index.html)
[tutorials](https://docs.oracle.com/javase/tutorial/)
[for](https://www.w3schools.com/js/DEFAULT.asp)
[most](http://www.cprogramming.com/tutorial.html)
[popular](https://golang.org/doc/) programming languages. But learning to code
often means learning a bunch of magic vocabulary and syntax rules that you mash
together in different ways until you come up with something that compiles and
produces the output you want for a couple of small test cases, if you bother to
test it at all. There's a difference between just programming and programming
well. A lot of 'anybody can code' initiatives have unreliable ways to check
whether true problem-solving abilities are fostered in students, the sort of
abilities that let you come up with the concept of binary search trees on your
own.

The skills required for successful programming are actually ones that you might
have more success picking up in an undergraduate mathematics or computer science
course: problem-solving, formal logic, reasoning with and about formal systems,
logical reasoning in general, and on a more personal level, persistence and
creativity. And while most people accept that undergraduate math courses are not
for everyone, programming somehow should still be something all kids can learn.
Working with computers means you need to understand how they function, why
your [incantations](https://stackoverflow.com/a/185803/1846915) cause certain
things to happen, and what precise things you need to tell the computer for it
to do exactly what you want. Sorting algorithms shouldn't be something that you
read and learn from a book, but that you discover for yourself (at least some of
them) from first principles, after you are introduced to computers and their
inner workings. (Which brings me dangerously close to discovery-based learning
which is a topic for another post. :P)

It is improbable that schoolchildren will learn these skills while learning to
code. Most likely, they will have to wait until college to take hard courses in
functional programming or operating system design to really wrap their heads
around the hard parts of theory. But children with the *aptitude* for these
skills will benefit from an education in programming, upon which they will build
their skills later.

Assuming you have some way to pick out programmatically-inclined students in a
class---which is certainly non-trivial; looking at their performance in the
class would be a bad way to do it because you don't know what factors are
involved---we come to the second point of keeping them interested. Programming
can be scary, intimidating, and un-fun if taught wrong. At this stage I feel
that the age of the students becomes an important factor.

Teaching young children programming concepts is by far not a modern idea. In
1967, [Seymour Papert](https://en.wikipedia.org/wiki/Seymour_Papert), a
mathematician, computer scientist, and educator working at MIT, designed the
[LOGO programming environment](https://en.wikipedia.org/wiki/Logo_(programming_language))
with other researchers specifically to teach elementary schoolchildren to code.
LOGO has come
[a long way](http://el.media.mit.edu/logo-foundation/what_is_logo/history.html)
since then, giving descendents like [Scratch](https://scratch.mit.edu/), which I
would recommend over LOGO today; [Alice](http://www.alice.org/) is built along
similar lines and with similar purpose.

(The recommendations in the previous paragraph are backed by decades of
research. Those in this paragraph are not.) For slightly older children, say,
maybe 8th and 9th grade, Scratch and friends can quickly get boring and
childish. However, I still feel that direct a direct association between writing
code and seeing cool things happen on the screen is important, so my suggestion
is to teach HTML/CSS/JS as one package. From an education perspective, none of
these is too hard or scary (OK, maybe JS is, but not as much as Java for
example), and since they're designed to work together smoothly in any browser on
any platform with no compilation or other programming hassles, they can be fun
to tinker with. Results are visually appealing and immediate: "Hey, I just
designed my own &lt;X> with cool animations and colorful fonts and dynamic
layouts!" And the practical benefits of learning HTML/CSS/JS are obvious because
these aren't some artificially constructed technologies, they run the entire
Internet. Two solid years of learning HTML/CSS/JS in school (along with all the
cool associated technology we have today, like JS frameworks and elegant NoSQL
DBs) could possibly be enough to get you into basic professional web dev. (Not
that I'm recommending it, two years could get boring.)

After that, keeping students interested is not an issue. The only thing you
shoud *not* do is teach everyone Java which is, for some reason, what high
schools do everywhere; Java is *not* a good choice for teaching either
programming or computer science. (Unless you want to teach Android development
later, but even that might now become [unnecessary](http://kotlinlang.org/).)
Some have
[harshly criticized Java](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html)
for reasons that I mostly agree with, and
[made interesting points](https://web.archive.org/web/20090412180717/http://www.stsc.hill.af.mil/CrossTalk/2008/01/0801DewarSchonberg.html)
about
[why Java should not be taught in schools](https://www.joelonsoftware.com/2005/12/29/the-perils-of-javaschools-2/),
which also I agree with. (If really necessary, a semester or two of
Python---non-scary, doesn't require advanced CS knowledge to fully grok, is
*useful* to build simple things---could be taught as a 'real' programming
language.)

Which brings us to the third and most important point of teaching CS theory
along with programming. If the two articles linked above about why teaching Java
in schools is bad haven't convinced you of it yet, I reiterate: theoretical
computer science education today needs more rigor. Both those articles talk
about college rather than high school; I argue that if the plan outlined in this
post is followed, high schools will receive talented students that already know
enough about programming and computers to take on the theory right from 10th or
11th grade. This will no doubt require a carefully tailored curriculum that
avoids all the pitfalls and possible gamifications that are too common in
education today (again, maybe this can be the topic of another post) and this is
well beyond the point where my competency ends, because I myself have not taken
a college computer science course yet, not being in college. But I still believe
that it is possible and will provide a wholesome, effective CS and programming
education to high-schoolers who can do so much more after it.

"High-schoolers who can do so much more": what an exciting phrase. Computer
science, and especially artificial intelligence, is among the biggest fields for
modern research. Programming constitutes an essential skills across disciplines,
in research and the industry alike. And I'm not saying that what I've proposed
for computer science and programming education is the best possible solution,
but I firmly believe that *something* has to be done to improve on the current
state of things today, and this is just an effort towards that.

Happy Summer Solstice!
