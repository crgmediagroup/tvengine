# tvengine
TextVentureEngine is a dynamic, powerful engine that can be used to play and make text-adventures playable in the command line.

## How to use
Open the app, then type /game <path at which a .tves is located>, obviously replacing the text in <> with a path to a tves. For example, /game C:\Users\Your Username\Desktop\example.tves

## How it works
TVEngine is written in C#. It loades JSON-like files called TVEScripts, or TVEHexes. Compiled files called TVECompiles are a planned add in the future. These contain various "labels" that ask the player a question and gets responses, which can in turn direct the player to other labels.

## File type
.tves - Standard files containing a JSON-like script. These are **great** for testing but not so great for any production release, as the user can edit them easily.<br>

## Developing
The .tves format has not been finalized, as we are still in active development. .tves are the only supported files at the moment. Here is an example:
```
{
  "labels": {
    "start" : {
      "action" : "ASK",
      "message" : "What do you want to do, {name}? \"kill\" or \"run\"?",
      "responses" : {
        "kill" : "label3",
        "run" : "label4"
      }
    },
    "label3" : {
      "action" : "ASK",
      "message" : "We are on Number 2! \"proc\" to proceed!",
      "responses" : {
        "proc" : "label4"
      }
    },
    "label4" : {
      "action" : "ASK",
      "message" : "We are on the final one. \"end\" to finish up.",
      "responses" : {
        "end" : "final"
      }
    },
    "final" : {
      "action" : "END"
    }
  }
}
```
"action" is required for both types. "message" and "responses" are required for ASK types. An END label will quit the game. A label called "start" **must** exist as this is where the engine starts looking.

## TVEngine Make
Make is a separate program for easy, flowchart-like development of your TextVentures. It will be built into the TVE Development Kit.

## TVEDevKit
TVEDevKit will be a distribution of TVEngine, containing several development utilities including:
* TVEngine - Base player system.
* TVEngine Make - GUI TextVenture Creator.

## Expected Release
TVEngine 1.0 is expected to release mid-2021.
