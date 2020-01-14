---
layout: post
title: "Generating Door Decs"
author: Aalok
---

At the beginning of each new academic year any typical college expects new
incoming first-year students. The college goes to some lengths to customize the
students' experience, to look out for them, and to make them feel like they are
at the right place, like they _belong_. A small but potentially important part
of this is to create door decorations, or simply, nametags to put on students'
names to mark their living spaces---spaces that are their very own (in addition
to their roommates, of course). Additionally, 'door decs' are made uniform
across a community, such as a small _pod_ within a hallway, an entire hallway,
or even a floor, so that the residents of that community feel a sense of being
in a community together. This is not all, of course, there are many other
things, such as floor traditions, hall events, and even just casual hanging out
that actually build the community; but small things can matter.

I needed to create door decs. I was running slightly behind schedule, but at the
same time I didn't want to take the easy way out like many RAs do by just
picking stock cut-outs of arbitrary objects, such as pine trees or apples or
whatever and just writing their names in. Last year I had inserted an impossible
geometry drawing inspired from Escher's art next to each resident's door. This
year had to be something different (though I still have the templates from last
year lying on my machine, if anyone's interested).

I've had a habit of tinkering around with my mobile phone's operating system for
a while now. Something I always notice is that these operating system
modification operations have (sometimes very) long scripts that they run in
order to 'flash' the software on your device, and you keep staring at that
script hoping it terminates any second. The developers probably realize this and
for whatever reason, include some fun ASCII-art, usually just their stylized
developer name or online identity, but sometimes it can be entertaining to see
the stuff people come up with using just ASCII symbols. Last year, I went around
hunting for some Python package to generate ASCII-art from text (I knew there
had to be one). I kind of played around with it, didn't really do much other
than including some ASCII art in the license prompt of some tiny program, and
even forgot about it for a good semester, until this week, when I was told I
should have my door decs ready soonish.

Well, why not write residents' names in ASCII-art then? I had to be efficient,
however: the names shouldn't be too big, and so I'd rather fit many on a single
sheet of paper and cut them out later. However, I couldn't dump all the names in
a single text file and expect page breaks to not mess everything up. Not all the
fonts in te `art` package were appropriate for door decs---a font had to be
easily visible and readable in order for it to make it to my list; and oh of
course, I couldn't have used the same font for all my residents, because, well,
that would get boring. Even with the fonts I chose, not each font worked well
with each name, so there had to be some form of manual decision on that.

The result was a tiny tiny
[script](https://gist.github.com/aalok-sathe/5f1a4f15bc17127966605deda64fb386)
that takes my roster file (which is, of course, a csv), shows me a couple of
options for a name with a font from my list as it cycles through fonts (so that
I reasonably end up using distinct fonts), and asks whether that font is okay to
use.

Anyway, that was my quick recap of what's been going on; I'd best get back to
cutting out these prints and pasting them on the doors before move-in day.

```
 ____  __   __    __   
(_  _)(  ) (  )  (  )  
  )(   )(  / (_/\/ (_/\
 (__) (__) \____/\____/
 __ _  ____  _  _  ____   
(  ( \(  __)( \/ )(_  _)  
/    / ) _)  )  (   )(    
\_)__)(____)(_/\_) (__)  
 ____  __   _  _  ____      
(_  _)(  ) ( \/ )(  __)     
  )(   )(  / \/ \ ) _)  _   
 (__) (__) \_)(_/(____)(_)


```
