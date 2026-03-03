# Sources for this Directory

All of the files here are synthetic in nature, using [Chatterbox](https://github.com/resemble-ai/chatterbox) to impart some specific emotion to the files from the [voices](../voices/) directory, using the emotional presents from [this file](https://github.com/dwain-barnes/chatterbox-fastrtc-realtime-emotion/blob/main/realtime_emotion.py).

Once the samples were produced, they were run through [Resemble Enhance](https://github.com/resemble-ai/resemble-enhance), to improve the quality, because Chatterbox sometimes introduces a small measure of random noise, especially when getting a little emotion out of it.

The emotions provided are: anger, calm, confused, enthused, excited, frustrated, happy, neutral, sad, surprised, tired and worried.  That should cover most everything, at least in the way of standard emotions.

Some voices worked better than others and some specific combination were quite difficult to get sane results for.  Along the way, it was discovered that Chatterbox has a strange tendency to babble incoherently, scream, laugh and giggle.  It also randomly shouts curse words and other foul language, leaving one wondering what in the world it was trained on.

'Anger' was often trouble, as were 'enthused' and 'excited'.

In a strange turn of events, the voices that gave the least trouble were those that started out calm and at a slow pace.  Donald Malone is an excellent example of that, which is the only voice that wasn't at all problematic, producing usable results on the first try, for all twelve emotions.


## Note on File Layout

The files here are arranged in directories by voice name, in lowercase and with underscores in place of spaces, then files with the name of an emotion, which end with `.flac`.  For example, if the voice actor is Kristin Hughes and the emotion is calm, the file name would be `kristin_hughes/calm.flac`.


## Future Plans

* New Emotion: narrator
	- This would be tuned for a professional tone
	- [This](https://www.scribd.com/document/951198068/Chatterbox) has some ideas that may be helpful with that
* New Emotion: shout
	- Can be achieved with exaggeration at 1.2
	- Unfortunately, this will be quite error-prone
	- It might be worth it to produce angry, neutral and surprised variations
* New Emotion: whisper
	- Would very much like to do this, but don't know how yet
	- Idea: find a whispering voice sample and use the [Chatterbox](https://github.com/resemble-ai/chatterbox) voice changer to combine it with other voices
	- Another idea: find a set of [SoX](https://en.wikipedia.org/wiki/SoX) filters that mimic whispering