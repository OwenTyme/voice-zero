# Voice-Zero

<img align="right" width="256" src="icon.svg">

This is a collection of open source compatible voice samples mostly from public domain and Creative Commons works, which are suitable for use with zero-shot text to speech engines.

The primary goal of this repository is to provide high quality voice samples that are ready to use, as-is, with zero-shot TTS engines like [Chatterbox](https://github.com/resemble-ai/chatterbox) and [Pocket TTS](https://github.com/kyutai-labs/pocket-tts).

The secondary goal is to provide a very clear trail from the final voice samples all the way back to not only the voice actor, but the original source files, for the sake of giving credit where credit is due.  That's not always possible, because some voice datasets seem to be anonymized, or have not been tracked very well, but whenever it can be done, that data will be provided.

A variety of tools were used to clean up the source data as much as possible, including the following:

* [Audacity](https://www.audacityteam.org/)
	- The built-in noise remover can be handy
	- Very rarely, this is also used to make slight speed changes
		+ Via tempo changes
* [Kanade Tokenizer](https://github.com/frothywater/kanade-tokenizer)
	- Amazing tool that operates in two modes:
		+ Voice Conversion
		+ Voice Resynthesis
			* This analyzes the voice, producing an ideal, noise-free version
			* That is then used to voice-convert the original sample, removing noise, which even works on reverb!
		+ It's extremely fast, especially compared to the [Chatterbox](https://github.com/resemble-ai/chatterbox) voice converter
* [SoX](https://en.wikipedia.org/wiki/SoX)
	- Involved in scripting the other tools, mostly for on the fly format conversion
* [Resemble Enhance](https://github.com/resemble-ai/resemble-enhance)
	- AI noise remover and audio up-scaler
	- This is used as the final step for each voice sample
	- It does a good job removing the noise [Chatterbox](https://github.com/resemble-ai/chatterbox) tends to introduce
* [RNNoise](https://github.com/xiph/rnnoise)
	- AI noise remover
	- Works quite well with VAD% set to 99
		+ The default of 50% is terribly ridiculous


## Notes on Directories

The [voices directory](voices) holds audio samples from [LibriVox.org](https://librivox.org), which have been noise reduced and trimmed to between seven and roughly twelve seconds, a length that works well for zero-shot TTS engines.  This directory will *always* hold [CC0-licensed](https://creativecommons.org/public-domain/cc0/) samples.

The [voices-emotion directory](voices-emotion) holds synthetic audio samples produced by using [voices directory](voices) with [Chatterbox](https://github.com/resemble-ai/chatterbox), to produce emotional variations.

If there are ever samples under other licenses, they will be placed in other directories, to keep the licensing issues clear and easy to work with.


## How Voice Samples Are Cleaned

For the curious, here's the current process used for cleaning up new voice samples, before they're fed into [Chatterbox](https://github.com/resemble-ai/chatterbox):

1) Import into [Audacity](https://www.audacityteam.org/)
2) Trim sample to between 1 and 3 sentences at 8-11 seconds in length
3) Remove the worst noise with [Audacity's](https://www.audacityteam.org/) noise removal tools
4) Use [RNNoise](https://github.com/xiph/rnnoise) with VAD% set to 99
5) Adjust speed via tempo changes to fix overly slow or fast speakers
	* Fast and slow voices become highly problematic for producing emotional variations with [Chatterbox](https://github.com/resemble-ai/chatterbox)
6) Normalize at -8 dB
7) Save the sample
8) Use [Kanade](https://github.com/frothywater/kanade-tokenizer) to resynthesize the sample, to remove reverb and other things [RNNoise](https://github.com/xiph/rnnoise) can't handle
9) Normalize again, via [SoX](https://en.wikipedia.org/wiki/SoX)
	* [Kanade](https://github.com/frothywater/kanade-tokenizer) is run via a script, so it was easy enough to add an automated normalization step
10) Upscale the sample to 44 kHz via [Resemble Enhance](https://github.com/resemble-ai/resemble-enhance)
	* [Kanade](https://github.com/frothywater/kanade-tokenizer) produces 24 kHz samples

Most of the steps are optional and applied more or less as needed.  For example, manual noise removal via [Audacity](https://www.audacityteam.org/) is rarely needed, because the combination of [RNNoise](https://github.com/xiph/rnnoise) and [Kanade](https://github.com/frothywater/kanade-tokenizer) generally wipe out all noise, even reverb.


## Contributing

This repository is a one-man show, but there are two areas in which contributions are welcome:

* Accent Classification
	- In particular, help would be appreciated with classifying the various American accents by region
		+ There may be some Canadians mixed in, which should be clarified, if possible
	- Some of the various UK accents may be incorrectly listed as English, when they're from other areas
		+ Sorry, but one does the best one can, with limited knowledge!
* Voice Suggestions
	- LibriVox voice suggestions will always be welcome
	- Voice samples from other source will also be considered
	- **DO NOT** suggest voice samples that aren't in the public domain
	- Accented voices are both desirable and useful
	- Keep the following in mind, however:
		+ The maintainer only speaks English and won't accept suggestions for voices in other languages
			* The noise removal steps **require** understanding what's been spoken

If you wish to clarify the accent of a voice or suggest a new voice, please file an issue.

When suggesting a new voice, please try to determine the accent, based on country of origin and region, because the maintainer has little direct experience with such things.


## License

Unless otherwise noted, all files in this repository are under the [CC0 license](https://creativecommons.org/public-domain/cc0/).  Currently, everything is based on samples from [LibriVox.org](https://librivox.org/) and [Archive.org](https://archive.org).

For more specific details, please examine the `README.md` files in each subdirectory, which will also provide the names of the voice actors and links to the original sources.
