---
layout: post
title: "Audio Spatialization + Remote Collaboration"
author: Shardul
---

I've been thinking for a while about audio spatialization in the context of
remote collaboration[^sources].

[^sources]:
    Parts of this post are inspired by some research papers I read (ask me if
    you want to see them) and a brief conversation with Phillip Wang, one of the
    [founders][5] of [Gather/Online Town][6] which is a very cool related
    project, and another conversation with my dad. Also useful is the MDN docs
    page for the [HTML5 web audio API][7], which includes some nice
    spatialization capabilities, and the [OpenAL-soft project][8] which
    implements a cross-platform API for 3D sound, including spatialization among
    many other goodies.

Audio spatialization is when you process audio in such a way that it sounds like
it's coming from a location in space, around you, rather than from your device
loudspeaker or kind of 'inside your head' when you're using head-/ear-phones.
The effect is easier to achieve with -phones because then you have independent
control over what each ear hears and no interference between the two; but you
can also do it with an array of well-placed speakers, like a home theater
surround sound system, and it sounds more natural because natural audio usually
doesn't materialize directly inside your ear ('bzzzz' – 'aagh get out!' – &lt;a
vague disgust lingers&gt;).

The processing is a little complicated[^processing], but it is certainly
possible to get quite realistic, and modern technology makes it not that
computationally challenging either. (Although virtual reality research has
explored this topic since [at least 1993][1]. Really there was so much VR
research in the 90s—sadly, then nor now, the rest of the technological world
hasn't made it commonplace.)

[^processing]:
    Briefly, there are two ways to do it. The first is to use a dummy model of a
    person (a detailed one—the shape and material of the ears matters a lot!),
    play predetermined sound samples (pure sine waves) from various angles
    around the dummy, record just inside the ears of the dummy, and when you
    want to play actual audio, modulate (convolve) the source audio with the
    recorded samples.  You can read more about these [head-related transfer
    functions][9]. The second is to build a mathematical model to simulate the
    effect by playing with the millisecond delay between when sound reaches one
    ear or the other, the frequency-filtering effects of the outer ear and head
    (and sometimes torso), varying amplitude in relation to distance and how
    much sound is blocked by the head/body, etc. This is simpler to program and
    understand but can be computationally more expensive and less realistic.

Tying this into remote collaboration: it often happens over group video or voice
calls, and the majority of widely-used platforms don't do spatialization at
all[^platforms]. What would spatialization look like in this setting? My
proposal is that each person in a call would have a seat at a virtual table, and
would hear the others talking as if from their positions around the table. (This
can be optionally augmented by tracking the direction of the listener's head so
you can 'look at' someone who's speaking and the audio changes accordingly.
Could use the webcam stream or mobile phone accelerometer data or something
else.) Depending on the nature of the work/collaboration, there could be
multiple tables within earshot of each other, or each person could have their
own table where others can join if they want to talk (and this will be faintly
but not distractingly audible to others).

[^platforms]:
    They do other advanced stuff like automatic echo cancellation and background
    noise reduction and turning down people who aren't currently speaking. They
    also have to deal with the headaches of having so many different media
    formats and web media protocols and differing browser and system
    requirements and connection quality and encryption and aaagh.

For now let's stick with the single table. Why might a collaboration platform
want to support this? I conjecture:
1. The 'cocktail party' problem: real-life discussions can organically generate
   side-discussions and cross-talk. These are hard to manage in a superimposed
   mono stream of everyone's audio, but our brains have a lot of experience in
   focusing on some (spatial) sources of sound and tuning out others.
1. Keeping track of the conversation without video: if you can't or aren't using
   video, using positioning information can make it easier to tell who's
   talking, in addition to recognizing their voice. It's easier for someone to
   jump in when their half-word–interruption isn't mistaken for noise; it's
   easier for others to tell that they haven't spoken for a while.
1. Aesthetics: it just seems more natural. Like actually being at a table
   together. If not practical value, it has a sort of artistic
   value[^aesthetic].

[^aesthetic]:
    You could even add reverb to make it not only sound like people are
    positioned in space, but also like people are in a room, i.e. the sound
    effect of being in a small padded office vs. a large glass-window conference
    room. This leads me into another augmentation/variation: back when I took
    [21M.080 (intro to music technology)][10], my final project was to simulate
    the reverberation profiles of various spaces on the MIT campus (which I did
    with the jankiest recording equipment possible). You could play an audio
    file or speak into a microphone and have it sound like it was in Lobby 7.
    But what if you could have a conversation in Lobby 7? What if you could in
    addition play the background noise of people talking and passing through
    Lobby 7? What if you could have a conversation while 'walking through'
    campus, and the 'sound environment' changed accordingly as you entered a
    hallway or a classroom, stepped outside, etc.? I've been ruminating on this
    sort of thing since then.

Of course there are good reasons that major platforms have for not implementing
this, probably a big one being computation overhead, either on their servers or
on users' machines, the latter which may not always be capable and the former
which may not be worth the (perceived) benefit. But then I discovered that
someone has already started to work on just this: [High Fidelity][2]. They're in
a beta phase right now so I signed up for a trial, and tried it out with some
friends, but it didn't quite work. (*Edit:* I've since learned from my friends
of a bunch of platforms that do this, including [Hubs][3] and [CozyRoom][4].)
Interested in seeing where this technology goes in the next year or so!

----

 [1]: http://wiki.arl.wustl.edu/images/0/0f/Carlsson-virtualReality-1993.pdf
 [2]: https://www.highfidelity.com/
 [3]: https://hubs.mozilla.com/#/
 [4]: https://cozyroom.xyz/
 [5]: https://siemprecollective.com/
 [6]: https://gather.town/
 [7]: https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API
 [8]: https://github.com/kcat/openal-soft
 [9]: https://en.wikipedia.org/wiki/Head-related_transfer_function
 [10]: http://student.mit.edu/catalog/m21Ma.html#21M.080
