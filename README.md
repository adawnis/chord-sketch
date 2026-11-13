# Chord Sketch

Hum a tune, hear it with chords.

**Try it:** https://adawnis.github.io/chord-sketch/

Chord Sketch is a small web tool for the moment a melody shows up and there's no keyboard near. Hum, sing or tap a tune, and it:

- hears the notes and works out the key
- picks one chord per bar, in **Simple**, **Pop** or **Gospel** style
- plays it all back, with loop and tempo
- lights up each chord's notes on the keyboard as it plays
- moves the whole song up or down a key, to suit the singer
- counts you in with a metronome and keeps you in time
- has a sustain switch that works like a piano pedal

Tap any chord to try another one. Three colour themes: Warm, Cool and Night.

## Private by design

Everything runs in your browser. Your voice isn't recorded or sent anywhere. Only the notes are kept, and only until you close the page.

## How it works

It's one HTML file with no libraries and no build step.

- **Pitch:** the microphone is read with the Web Audio API, and each short slice is matched against itself (autocorrelation) to find the note.
- **Key:** note lengths are compared with the Krumhansl–Schmuckler key profiles.
- **Chords:** each bar scores the chords of the key by how well they fit the tune, then a short path search favours moves that sound natural (V to I, ii to V, and so on). Gospel adds 7ths and 9ths, a walking bass, and passing chords where the tune leaves room.
- **Sound:** a small synth built on Web Audio: electric piano, pad, bass and a lead for the tune.

To run it locally, serve the folder over `http://localhost` (the microphone needs a secure page or localhost), for example:

```bash
npx serve .
```

## Credits

Made by [Uche Ukachi](https://mrukachi.com/work/chord-sketch). Code under the MIT licence. The Geist font is under the SIL Open Font License (see `fonts/OFL.txt`).
