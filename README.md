soundbank-pitch-shift
===

Simple pitch shifter for Web Audio API based on delay nodes. Extends [Jungle](https://github.com/cwilso/Audio-Input-Effects/blob/master/js/jungle.js) by [Chris Wilso](https://github.com/cwilso) (Copyright Google).

Intended for use as a processor in [soundbank](https://github.com/mmckegg/soundbank), but it is compatible with any [Web Audio API](https://developer.mozilla.org/en-US/docs/Web_Audio_API) AudioNode set up.

## Install

```bash
$ npm install soundbank-pitch-shift
```

## API

```js
var PitchShift = require('soundbank-pitch-shift')
```

### PitchShift(audioContext)

Create and return an [AudioNode](https://developer.mozilla.org/en-US/docs/Web/API/AudioNode) instance.

### node.transpose (get/set)

Specify semi-tones to transpose the input signal by.

### node.wet (AudioParam)

### node.dry (AudioParam)

## Example

```js
var PitchShift = require('soundbank-pitch-shift')

var audioContext = new AudioContext()

var pitchShift = PitchShift(audioContext)
pitchShift.connect(audioContext.destination)

pitchShift.transpose = 12
pitchShift.wet.value = 1
pitchShift.dry.value = 0.5

setInterval(function(){
  var source = audioContext.createOscillator()
  source.connect(pitchShift)
  source.start()
  source.stop(audioContext.currentTime + 0.5)
}, 2000)
```