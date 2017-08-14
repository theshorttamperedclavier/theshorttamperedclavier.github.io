---
layout: post
title: "Customer Care"
---

A little over four years ago, my school transitioned from paper-based prefect
elections to computerized elections, eliminating the process of hand-counting
that took a week of the time of several staff members. This was in itself
definitely an improvement, and what's more, the software they were using was
produced in-house by a 10th-grader in the Computer Applications [sic] class.
But 8th-grade me observed the rudimentary text-based interface, poor error
handling, lack of data robustness or recovery (yes, election data could simply
disappear in the middle of an election!), and the completely unsatisfactory
process of manually going to each election booth and collecting the results to
add them up; surely this could be improved. 8th-grade me took a look at the
code.

What a mess. 2000 lines of code for a text-based standalone Java application?
Why did the guy have to *copy and paste several blocks of code*? Not to mention
terrible formatting and programming practices, like *hard-coding the candidate
names* in the program.
([Like I said before]({{ site.baseurl }}{% post_url 2017-06-21-teach-kids-code %}),
this was definitely not the teacher's fault, but I wonder why they tend to name
variables things like <code>int a</code>---maybe because that's how math
variables are named?) Anyway, I realized things could be much better, and I
wrote [VoteCounter](https://gitlab.com/shardul.chiplunkar/vote-counter/) over
the summer: a decent-looking Java application with a GUI, operating over the
network with a server reliably recording results and taking care of client
connections/failures on the fly. Specifying arbitrary offices and candidates
was as easy as editing an XML file and you could add logos and nominee symbols
and whatnot as required. Everything was under the GPLv3 and the sources (under
1500 lines of code, by the way, excluding an XML parser library and a
command-line argument library) were pretty well-documented; a satisfactory
project on the whole.

It worked well in my school the next year and is being used every year since,
including just a month ago. And after the first two years, a school my aunt
teaches in in Goa was also interested, and so on my next visit to Goa, I set up
the system there and it worked for them too. All good so far.
(Just to clarify, this was four years ago; now I'm living in Fremont,
California, and currently I'm at MathILy-Er in Salem, Oregon.)

But a few days ago the Goa school ran into a minor issue with adding images to
the nominee buttons (the actual election stuff was working perfectly, and even
this shouldn't have had any issues), and contacted me around two days before
the actual elections were scheduled---to make matters worse, the twelve-hour
timezone difference meant that I either had to stay up late to help them or
narrowly catch a one-hour window when both of us had time. Of course I wanted to
help because this was, you know, my first 'product', and customer care is a
large part of developing software, so you can guess which option ended up
happening. First I sent a well-written email reply with phrases like

> If the VoteCounter file is on the Desktop, then the 'symbols' folder should
> also be on the Desktop; if the VoteCounter file is in some other folder, the
> 'symbols' folder should also be in that same folder ... For future reference,
> there are some instructions on this webpage:
> [link](https://gitlab.com/shardul.chiplunkar/vote-counter/blob/master/HELP.md)
> ...

To which I received as a reply

> But how to edit XML file for image <br>
> What we have to put in XML file for image

Quite understandably, there was some confusion. I explained that they did not
need to edit the XML file for images since the images were not sent over the
network (I did this to reduce network usage and client memory usage, perhaps it
was a bad idea) but simply had to put them in the appropriate folder with
appropriate names in the appropriate location.

> Still not working

Hmm, well,
[perhaps this discussion can be moved to chat?](https://meta.stackexchange.com/questions/96247/is-it-possible-to-import-comments-into-a-chat-room-without-the-link-appearing)
I invited the correspondent to a chat on WhatsApp.

> Now on what's app I will click photo n send u please guide meeee <br>
> by today let's us fix the exxor

To be fair, he suggested using
[TeamViewer](https://www.teamviewer.com/en/), which I would have
agreed to if the issue was (in my opinion) more complex, but this was just a
matter of file and directory naming so I declined. (Plus I would have had to use
my laptop while eating which is too much context-switching trouble.)

> *Him:* Now I have put it inside folder *(this was the correct folder)* <br>
> Still not working ... how to rename <br>
> *Me:* can you show me a picture of the client running? <br>
> *Him, with a picture:* Thai si my xmlfile

A few photos later, I found that the image files were <code>flower.jpg</code>
and not <code>candidatename.jpg</code> as I had advised previously. With the
renames, we tried a couple of times, but no success. (In retrospect I *really*
should have acquiesced to the TeamViewer suggestion at this point but I
didn't...)

> Is it working on ypur laptoo

Well, it was. But I was running stuff from the command line; maybe
W&#42;nd&#42;ws' JRE launches JARs outside their working directories? I
suggested that he also use the command line and see if it works.

> *Me:* in the command line, you have to go into the folder where the file is
> and type 'java -jar VoteClient.jar' and then the symbols should work <br>
> *Him:* Where to type <br>
> what is command line <br>

Oh dear.

> *Me:* it's called 'cmd' in the Start menu <br>
> *Him:* Where it is <br>
> Today ks the last day for meee help me please <br>
> *Me:* in cmd, you have to type <code>cd</code> and then the path to the
> folder, then press enter

A few messages back and forth with me dictating command-line directives later:

> *Me:* OK now type 'java -jar VoteClient.jar' <br>
> *Him:* With '👈 symbol???

No, without that symbol. It's a quotation mark.

> See what comes *(in a picture)*
> > 'java' is not recognized as an internal or external command, operable
> > program, or batch file

[Aaagghh](https://stackoverflow.com/a/16137745/1846915).

Finally he asked if I could send him the folder from my laptop so I zipped it
and sent a Drive link. It contained exactly the same JAR that he had so I was
skeptical of this action. (I have a 
[couple](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html)
of
[things](https://web.archive.org/web/20090412180717/http://www.stsc.hill.af.mil/CrossTalk/2008/01/0)
against
[Java](https://www.joelonsoftware.com/2005/12/29/the-perils-of-javaschools-2/)
but sending a ready-to-run program in another language and getting it to run on
his dated W&#42;nd&#42;ws machine would have been much harder.)

> *Me:* if that doesn't work I don't know what to do <br>
> *Him, a few hours later:* Thanks a ot it's working <br>
> Thanks a lor <br>
> Lot

Well, glad to be of help. I don't know what broke the program in the first place
and what fixed it (probably, guessing from my experience with W&#42;nd&#42;ws,
he simply rebooted his machine) but that was that. I now completely understand
why corporate customer care has to pander to the absolute lowest common
denominator and
[offend us all](http://verizonmath.blogspot.com/2006/12/verizon-doesnt-know-dollars-from-cents.html),
not to mention the 20-minute wait times listening to 10 kHz piped Mozart.
Timezone differences and sleep schedules, you know?
