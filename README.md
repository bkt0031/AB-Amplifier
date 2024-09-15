# Class AB Monaural 2 Watt Amplifier

With regards to class AB audio amplifiers there is really nothing new under the sun, and this design is no exception.

I have a collection of amateur radio transceivers I built as kits from QRP Labs that the audio ouput can only drive small
headphones (earbuds). Personally I cannot stand having earbuds in my ears for long durations, so I wanted to make an
audio amplifier to drive a speaker I reprovisioned from a commercial mobile radio. 

My requirements for the audio amplifier was:

* Run off of a 12 VDC, single rail, power supply
* Drive a 4 Ohm speaker
* Loud enough for a typical size room with enough volume to overcome any incidental noise/sounds
* Needs to be an analog class of operation - please, no switching...
* I don't want to waste power - needs efficiency
* Power switch
* Power input on a 2.1x5.5 mm panel jack
* Power indicator
* Volume control

Loudness requirements is a bit nebulous to me as I have no clue as to how the sound pressure levels from
the speaker relate to the wattage applied to the speaker. In this case I decided to just go for the maximum
that I could get from a 12 VDC single rail supply, which I know is not much really in my way of thinking.

My general conclusion is to use a class AB amplfier, and the ultimate circuit I ended up with is
based on the design of *The Tube Roaster* channel on [YouTube](https://www.youtube.com/watch?v=THRFZiEfnnA). 
The largest difference was the supply voltage he was using and my 12 VDC supply requirement. I ended
up entering the circuit in [QSpice](https://www.qorvo.com/design-hub/design-tools/interactive/qspice/), tweaking
the bias resistors till I got even clipping on the output. The resulting circuit looks like:

![QSpiceSchematic](https://github.com/user-attachments/assets/6c12eb80-39d9-497d-acdb-365f576a032b)

The net simulate results were maximum unclipped output voltage across the 4 Ohm load of 8.1 Vp-p which results in around
2 Watts being delivered to the load. The simulated unclipped gain was 23.1 dB at 1 KHz.

The only oddity of this circuit is the boostrapping capacitor C4. Based on what little I know about boostrapping it has
the effect of reducing the AC current through R7 which effectively raises the collector AC resistance on the input common-emitter
amplifier (Q1). Running the simulation with and without C4 show the gain to increase around 3 dB with the bootstrapping circuit
in place.

After building this circuit I ended up with about 8.23 Vp-p unclipped maximum output voltage which will deliver 2.1 Watts to
the 4 Ohm speaker.

The external case mounted parts used were:

| Qty   | Description                       | Distributor  | Part Number          | Notes                |
| :---- | :-------------------------------- | :----------- | :------------------- | :------------------- |
| 1     | POT 1K OHM 1/2W PLASTIC LINEAR    | Digi-Key     | 53AAD-B28-B10L-ND    | Overkill - lol       |
| 1     | Toggle Switch SPST Panel Mount    | Digi-Key     | 360-MN11ES1W01-ND    |                      |
| 1     | LED 3MM PANEL MNT W/24AWG LEADS   | Digi-Key     | SSI-LXR3612ID-150-ND |                      |
| 1     | CONN JACK MONO 3.5MM PNL MNT      | Digi-Key     | SC1455-ND            |                      |
| 1     | CONN RCA JACK MONO 3.2MM PNL MT   | Digi-Key     | CP-1412-ND           | No locating features |
| 1     | CONN PWR JACK 2.0X5.5MM SOLDER    | Digi-Key     | CP-5-ND              |                      |

The case was printed using ABS filament. I always have a problem with determining hole size for the threaded heat
inserts. In my case the standoff hole sizes were a tad small and I needed to increase the hole size so that 
the head insert would go in without deforming the standoff.
