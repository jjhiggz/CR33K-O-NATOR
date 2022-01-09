# CR33K-O-NATOR

## Intro

The goal for this project is to make a VST plugin that does all of the stuff that makes this song sound cool. [CR∑∑KS Song found here](https://www.youtube.com/watch?v=P_Fx1yq3A8M). Being a long time produce I understand the idea from a black-box perspective. I just need to learn a whole ton about audio engineering in the process.

## The Algorithm ( Roughly )

Some people call this effect the prismizer, It's similar to a vocoder, but a bit fancier.

To my knowledge a vocoder works something like this (pseudocode)

```ts
const vocoder = (sound: Audio, midiNotes: MidiNote) => {
 const modifiedInputSounds: Audio[] = midiNotes.map( midiNote => {
  const pitch = pitchOf(midiNote);
  return forcePitch(sound, pitch);
 })
 return sumSounds(modifiedInputSounds);
}
```

But I'm thinking that a creek-o-nator would have to offer a bit more intense of a calculation

```ts
const creekONate = (sound: Audio, midiNotes: MidiNote, maxFormant: number, minFormant: number ) => {
 const modifiedInputSounds: Audio[] = midiNotes.map( midiNote => {
  const pitch = pitchOf(midiNote);
  let formant = getNaturalFormant(pitch);
 const pitchCorrected = forcePitch(sound, pitch);
 if(maxFormant < formant){
  formant = maxFormant;
 }
 if(minFormant > formant){
  formant = minFormant;
 }
 return forceFormant(sound, formant);
 })
 return sumSounds(modifiedInputSounds);
}
```

Computationally I think this is a pretty expensive calculation. I have a ton to do this is just day 1 notes. I was playing around with logic pro basically following this algorithm by hand (It's really annoying to do), and was able to replicate the sound.

[Here is a sample, of the hopeful eventual algorithm done in logic pro](https://soundcloud.com/jjmakesmusic/cr33konator-test-sound-1-no-piano)

## Why

I've been meaning to get into low-level programming, potentially rust as well. As a producer, it took me about 20 minutes to do something on a 10 second clip, that if automatable could save me HOURS AND HOURS of time producing for something like a 2 minute song. In theory, with concurrency, and algorithm, this could be done in real time. I'm pretty amateur at this type of programming so we'll see how this goes. Wish me luck
