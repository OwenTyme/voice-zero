# Sources for this Directory

All of the files here are synthetic in nature, using [Chatterbox](https://github.com/resemble-ai/chatterbox) to impart some specific emotion to the files from the [voices](../voices/) directory, using the emotional presents from [this file](https://github.com/dwain-barnes/chatterbox-fastrtc-realtime-emotion/blob/main/realtime_emotion.py).

Once the samples were produced, they were run through [Resemble Enhance](https://github.com/resemble-ai/resemble-enhance), to improve the quality, because Chatterbox sometimes introduces a small measure of random noise, especially when getting a little emotion out of it.

The emotions provided are: anger, calm, confused, enthused, excited, frustrated, happy, neutral, sad, surprised, tired and worried.  That should cover most everything, except shouting.

Some voices worked better than others and some specific options were quite difficult to get sane results for.  Along the way, it was discovered that Chatterbox has a strange tendency to babble incoherently, scream, laugh and giggle.  It also randomly shouts curse words and other foul language, leaving one wondering what in the world it was trained on.

'Anger' was often trouble, as were 'enthused' and 'excited'.

In a strange turn of events, the voices that gave the least trouble were those that started out calm and at a slow pace.  Donald Malone is an excellent example of that, which is the only voice that wasn't at all problematic, producing usable results on the first try, for all twelve emotions.


## Note on File Layout

The files here are arranged in directories by voice name, in lowercase and with underscores in place of spaces, then files with the name of an emotion, which end with `.flac`.  For example, if the voice actor is Kristin Hughes and the emotion is calm, the file name would be `kristin_hughes/calm.flac`.


## Future Plans

* New emotion: narrator
	- This would be tuned for a professional tone
	- [This](https://www.scribd.com/document/951198068/Chatterbox) has some ideas that may be helpful with that
* New emotion: shout
	- Can be achieved with exaggeration at 1.2
	- Unfortunately, this would be quite error-prone
