# Amazon SSML cheatsheet

[Full reference](https://developer.amazon.com/it/docs/custom-skills/speech-synthesis-markup-language-ssml-reference.html).

Wrap everything with `<speak>`:

```xml
<speak>Hello</speak>
```

Whispered voice:

```xml
<amazon:effect name="whispered">Whispered text</amazon:effect>
```

Include MP3 sound (max 240 seconds and no more than five):

```xml
Hi <audio src="https://yourdomain/audio.mp3" />
```

Pauses:

```xml
<break time="3s" />
<break time="500ms" />

<break strength="none" /> <!-- removes pause after period -->
<break strength="x-weak" />

<break strength="weak" /> <!-- like a comma -->
<break strength="medium" />

<break strength="strong" /> <!-- sentence break (period) -->
<s>Sentence</s>

<break strength="x-strong" /> <!-- paragraph break -->
<p>Paragraph</p>
```

Emphasis (speed and volume (?)):

```xml
<emphasis level="strong" /> <!-- slower and louder (?) -->
<emphasis level="moderate" />
<emphasis level="reduced" /> <!-- faster and softer (?) -->
```

Other languages:

```xml
<lang xml:lang="de-DE">Entschuldigung</lang>
<!-- en-US, en-GB, en-IN, en-AU, en-CA, de-DE, es-ES, it-IT, ja-JP, fr-FR -->
```

Phonemes:

```xml
<phoneme alphabet="ipa" ph="ˈbɑ.təl">bottle</phoneme>
<phoneme alphabet="x-sampa" ph="&quot;bA.t@l">bottle</phoneme>
```

Volume, pitch and rate:

```xml
<prosody rate="x-slow">Text</prosody>
<prosody rate="slow">Text</prosody>
<prosody rate="medium">Text</prosody>
<prosody rate="fast">Text</prosody>
<prosody rate="x-fast">Text</prosody>
<prosody rate="100%">Text</prosody> <!-- min 20% -->

<prosody pitch="x-low">Text</prosody>
<prosody pitch="low">Text</prosody>
<prosody pitch="medium">Text</prosody>
<prosody pitch="high">Text</prosody>
<prosody pitch="x-high">Text</prosody>
<prosody pitch="+10%">Text</prosody> <!-- max +50% -->
<prosody pitch="-10%">Text</prosody> <!-- min -33.3% -->

<prosody volume="silent">Text</prosody>
<prosody volume="x-soft">Text</prosody>
<prosody volume="soft">Text</prosody>
<prosody volume="medium">Text</prosody>
<prosody volume="loud">Text</prosody>
<prosody volume="x-loud">Text</prosody>
<prosody volume="+6dB">Text</prosody> <!-- max +4.08dB -->
```

Text interpretation:

```xml
<say-as interpret-as="characters">hello</say-as> <!-- or "spell-out" -->
<say-as interpret-as="cardinal">150</say-as> <!-- or "number" -->
<say-as interpret-as="ordinal">3</say-as>
<say-as interpret-as="digits">7124</say-as>
<say-as interpret-as="fraction">1/3</say-as>
<say-as interpret-as="unit">4dB</say-as>
<say-as interpret-as="date">20181031</say-as>
<say-as interpret-as="date" format="ymd">20181031</say-as> <!-- any combination of ymd -->
<say-as interpret-as="time">1'21"</say-as>
<say-as interpret-as="telephone">1234567</say-as>
<say-as interpret-as="telephone">1234567890</say-as>
<say-as interpret-as="address"></say-as> <!-- street -->
<say-as interpret-as="expletive">Becomes beeeep</say-as>
<say-as interpret-as="interjection">oh no</say-as>
<!-- https://developer.amazon.com/it/docs/custom-skills/speech-synthesis-markup-language-ssml-reference.html#supported-speechcons -->
```

Specify pronunciation:

```xml
<sub alias="magnesium">Mg</sub>
```

Voices (Amazon Polly):

```xml
<voice name="Emma">Text</voice>
<!-- https://developer.amazon.com/it/docs/custom-skills/speech-synthesis-markup-language-ssml-reference.html#voice -->
```

Voice + language:

```xml
<voice name="Emma"><lang xml:lang="en-GB">British</lang></voice>
```

Part of speech pronunciation:

```xml
<w role="amazon:VB"></w> <!-- present simple -->
<w role="amazon:VBD"></w> <!-- past participle -->
<w role="amazon:NN"></w> <!-- noun -->
<w role="amazon:SENSE_1"></w> <!-- use the non-default pronunciation -->
```