[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=19282383)
# COMP 122 Web Audio Player Project
This is a series of creative exercises designed to work together as a unified real-time interactive musical instrument implemented in the browser using Tone.js (for sound) and P5.js (for graphics).

Students will add their own content to the four sections of this project (sampler, synth, sequencer, generator) by uploading and editing media dependencies (sound files, etc.) and JSON data files describing the parameters for each section.

## Part 1 - Sampler

Students will locate and edit short soundfile samples (using online tools such as AudioMass) to be triggerd at will within the project interface. Each sample will be described within a JSON file with a prescribed structure. Sample properties may include tempo and pitch information (for time scaling and transposition), as well as offsets and loop points. The sampler player will read the student-provided JSON file and create Tone.player instruments with a graphical user interface, provided the sample files listed in the JSON file are uploaded into the project directory as well.

For example:
```json
[
  {
    "name" : "fear",
    "file" : "samples/FDR_fear_itself.mp3",
    "bpm" : 120,
    "duration" : "4m"
  },
  {
    "name" : "the only thing",
    "file" : "samples/FDR_the_only_thing.mp3",
    "bpm" : 120
  },
  {
    "name" : "Camden Rain Piano (ST)",
    "file" : "samples/Camden_Rain_piano.wav",
    "bpm" : 120,
    "duration" : "8m"
  }
]
```

## Part 2 (A and B) - Drum Patterns & Note Sequences
Students will describe a set of short musical seequences (chord progressions and/or melodies) and a set of rhythmic patterns (individual parts of a drum pattern). These patterns may be orginal compositions or transcribed from other sources into JSON.

**Part 2-A:** For example, a set of drum patterns:
```json
[
  {
    "name" : "kick",
    "pitch" : "A3",
    "pattern" : "1000",
    "synth" : "mySampler"
  },
  {
    "name" : "claps",
    "pitch" : "C4",
    "pattern" : "0000100000001000",
    "synth" : "mySampler"
  },
  {
    "name" : "hi-hat",
    "pitch" : "F4",
    "pattern" : "00010101110111010100110110010",
    "synth" : "mySampler"
  }
]
```
**Part 2-b:** and a set of note sequences:
```json
[
  {
    "name": "sequence 1",
    "octave": 0,
    "duration": "1:0:0",
    "sequence": [
      { "time": "0:0:0", "pitch": "C4", "dur": "8n" },
      { "time": "0:0:2", "pitch": "C4", "dur": "8n" },
      { "time": "0:1:0", "pitch": "G4", "dur": "8n" },
      { "time": "0:1:2", "pitch": "G4", "dur": "8n" },
      { "time": "0:2:0", "pitch": "A4", "dur": "8n" },
      { "time": "0:2:2", "pitch": "A4", "dur": "8n" },
      { "time": "0:3:0", "pitch": "G4", "dur": "4n" }
    ]
  },
  {
    "name": "sequence 2",
    "octave": 0,
    "duration": "1:0:0",
    "sequence": [
      { "time": "0:0:0", "pitch": "F4", "dur": "8n" },
      { "time": "0:0:2", "pitch": "F4", "dur": "8n" },
      { "time": "0:1:0", "pitch": "E4", "dur": "8n" },
      { "time": "0:1:2", "pitch": "E4", "dur": "8n" },
      { "time": "0:2:0", "pitch": "D4", "dur": "8n" },
      { "time": "0:2:2", "pitch": "D4", "dur": "8n" },
      { "time": "0:3:0", "pitch": "C4", "dur": "4n" }
    ]
  }
]

```

## Part 3 - Synthesizer
Students will create a series of Synthesizer preset modules described in a JSON document. These synthesizers are realized using the Tone.js library (based on the Web Audio API) and will be limited to several basic synthesizer types. Students will create one or more presets sounds that will be available to each of the subsequent modules that rely on synthesizer playback (sequences and generative music system).

for example:
```json
[
  {
    "name" : "megasynth",
    "type" : "AMSynth",
    "settings" : {}
  },
  {
    "name" : "FM Aliens",
    "type" : "FMSynth",
    "settings" : {}
  }
]
```

## Part 4 - Algorithmic Music Generator
Create a JSON describing Markov probability tables for both rhythm and pitch. The graph may be derived from an existing tune or may be entirely invented by the student. It is possible to create multiple Markov generators and to play them simultaneously (in time with the central Transport clock).

For example:
```json
[
  {
    "name" : "bass",
    "pitchSet" : {
    "state" : "C3",
    "matrix" : {
      "C3" : ["C3", "G3", "B2"],
      "G3" : ["C3", "G3", "B2"],
      "B2" : ["C3"]
      }
    },
    "rhythmSet" : {
      "state" : "4n",
      "staccato" : "true",
      "matrix" : {
        "4n" : ["4n", "16n"],
        "16n" : ["4n", "16n", "8n"],
        "8n" : ["4n", "16n", "8n"]
      }
    }
  },
  {
    "name" : "twinkle",
    "pitchSet" : {
    "state" : "C4",
    "matrix" : {
      "C4" : ["C4", "G4"],
      "G4" : ["G4", "A4", "F4"],
      "A4" : ["A4", "G4"],
      "F4" : ["F4", "E4"],
      "E4" : ["E4", "D4"],
      "D4" : ["D4", "C4"]
      }
    },
    "rhythmSet" : {
      "state" : "8n",
      "staccato": " true",
      "matrix" : {
        "8n" : ["8n", "8n", "8n", "2n"],
        "2n" : ["8n"]
      }
    }
  }
]
```
