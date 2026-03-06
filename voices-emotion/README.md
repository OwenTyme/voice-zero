# Sources for this Directory

All of the files here are synthetic in nature, using [Chatterbox](https://github.com/resemble-ai/chatterbox) to impart some specific emotion to the files from the [voices](../voices/) directory, using the emotional presents from [this file](https://github.com/dwain-barnes/chatterbox-fastrtc-realtime-emotion/blob/main/realtime_emotion.py).

Something akin to the intensity of a shout was achieved for the 'shout' emotion, by starting from the 'neutral' settings, except exaggeration was set to 1.2, to make it as intense as possible.

Once the samples were produced, they were run through [Resemble Enhance](https://github.com/resemble-ai/resemble-enhance), to improve the quality, because Chatterbox sometimes introduces a small measure of random noise, especially when getting a little emotion out of it.

The emotions currently available are: anger, calm, confused, enthused, excited, frustrated, happy, neutral, sad, shout, surprised, tired and worried.  That should cover most needs, at least in the way of standard emotions.  Small speed changes with the final TTS engine could possibly push things a little further, with slow anger serving as menace and fast anger potentially coming across as rage.

Some voices worked better than others this way and some specific combinations were quite difficult to get sane results with.  Along the way, it was discovered that Chatterbox has a strange tendency to babble incoherently, scream, laugh and giggle.  It also randomly shouts curse words and other foul language, leaving one wondering what in the world it was trained on.

The following emotions were the most troublesome: 'anger','enthused' and 'excited'.

In a strange turn of events, the voices that gave the least trouble were those that started out calm and at a slow pace.  Donald Malone is an excellent example of that, which is the only voice that wasn't at all problematic, producing usable results on the first try, for all emotions.


## Notes on File Layout

The files here are arranged in directories by voice name, in lowercase, without accent marks and underscores in place of spaces, then files with the name of an emotion, which end with `.flac`.  For example, for the voice actor Kristin Hughes and the emotion 'calm', the file name would be `kristin_hughes/calm.flac`.


## Future Plans

* New Emotion: narrator
	- This would be tuned for a professional tone
	- [This](https://www.scribd.com/document/951198068/Chatterbox) has some ideas that may be helpful with that
* Shout Variations
	- Shouting versions of angry, and surprised might be appropriate
* New Emotion: whisper
	- Would very much like to do this, but don't know how yet
	- Idea: find a whispering voice sample and use the [Chatterbox](https://github.com/resemble-ai/chatterbox) voice changer to combine it with other voices
	- Another idea: find a set of [SoX](https://en.wikipedia.org/wiki/SoX) filters that mimic whispering
		+ It might be possible to feed that to [Chatterbox](https://github.com/resemble-ai/chatterbox), which would probably make it sound more realistic (that's a trick that works well for pitch shifts)
		+ `highpass 500` seems to be a decent start, but it lacks the breathy quality