# Circuitry-Based Sound




"Circuitry-Based Sound" is an ongoing seminar at [University of Arts and Design Karlsruhe](https://www.hfg-karlsruhe.de/ "University of Arts and Design Karlsruhe"). It focuses on electronic sound synthesis and parametric interfacing. It's examining musical characteristics of electronic instruments and comparing different approaches on how to design electronic sound modules. Due to the measures against the coronavirus spread in 2020, the seminar’s workflow had been adapted to the restrictions and is partially held online.

The course is covering electrical and electronic basics, computer aided circuit design and professional PCB manufacturing processes with the aim of building custom-made instruments. The emphasis is on studies of logic chips for sound creation and its musical applications. Participants are guided to use the latest technology, production chain and global logistics to develop, design and produce circuit boards for musical use. This allows the participants to easily create circuit boards with more variable features and adjustable parameters than hand soldered protoboards or solderless breadboards.

The following is a documentation of the seminar's study materials and findings.

# Unconventional Electronic Sound

Aside from the established way of using electronics to generate and process sound, which can be found in analog synthesizers, there are also unconventional applications of electronics to create sound or experimental music, which will be introduced below. Analog synthesizers apply techniques like [subtractive synthesis](https://en.wikipedia.org/wiki/Subtractive_synthesis "subtractive synthesis") to produce audio. A common concept of the analog signal flow is filtering the output of an oscillator and shaping the overall volume. Variations of this concept can be found in most synthesizers, both analog and digital. Parameters can be altered through control signals. This offers a wide range of musical expression, like tuning oscillators in a 12-tone musical scale or key triggered [envelopes](https://en.wikipedia.org/wiki/Envelope_(music) "envelope") for amplifiers, filters or other effect processors. To obtain these functionalities, circuits of analog synthesizers are relatively complex, involve a high part count and often require precision components.

Another concept of creating sound with electronics derived from techniques like hardware hacking and circuit bending. Especially the use of digital integrated logic circuits outside of their typical field of application is a remarkable approach to build customized instruments for artistic sound production and interactive music. The required components are easy to source and low cost.

## CMOS Chips for Sound Creation

<img src="https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/CMOS-chips.jpg">


[CMOS chips](https://en.wikipedia.org/wiki/4000-series_integrated_circuits/ "4000-series integrated circuits") are designed to execute boolean functions. Complementary metal–oxide–semiconductor (CMOS) is a technique where p-type and n-type MOSFETs are used for manufacturing logic gates. Voltage levels represent the binary states 0 and 1. Produced as integrated circuits, individual components relate to basic logical functions like [NOT](https://en.wikipedia.org/wiki/Inverter_(logic_gate) "Inverter"), [AND](https://en.wikipedia.org/wiki/AND_gate "AND gate"), [OR](https://en.wikipedia.org/wiki/OR_gate "Or gate"), [NAND](https://en.wikipedia.org/wiki/NAND_gate "NAND gate"), [XOR](https://en.wikipedia.org/wiki/XOR_gate "XOR gate"), [XNOR](https://en.wikipedia.org/wiki/XNOR_gate "XNOR gate") or implement [multiplexers](https://en.wikipedia.org/wiki/Multiplexer "multiplexer"), [counters](https://en.wikipedia.org/wiki/Counter_(digital) "counter"), dividers, [flip-flops](https://en.wikipedia.org/wiki/Flip-flop_(electronics) "flip-flop") and [registers](https://en.wikipedia.org/wiki/Shift_register "shift register"). When logical operations and their relation to voltage and sound are understood, CMOS-logic chips are an inexhaustible source for unconventional electronic sound. They produce digital signals - square waves - that can be modified, shaped, gated, sequenced and many more. Combining different logic functions allows generating a multitude of unique sounds and temporal music structures, while they produce the richness of analog sound. These circuits also yield unpredictable behavior, produce rhythmic glitches or digital noise.

Due to its simplicity, CMOS chips can be used for educational reasons, since most of its technical operations can easily be understood and relate to basic electronic knowledge. This subject is also a matter of various publications, most notably [Nicolas Collins'](https://en.wikipedia.org/wiki/Nicolas_Collins "Collins") „Handmade Electronic Music, The Art of Hardware Hacking" (2006). American Composer [David Tudor](https://de.wikipedia.org/wiki/David_Tudor "David Tudor") (1926 - 1996) is considered a pioneer of self-made electronic circuits and instruments, which he used for his compositions.

## Basic Example

<img src="https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/CD40106_Fritzing.jpg">

The „hello world“ of CMOS-Synthesizers as a measure of how simple it is to produce sound is illustrated through the picture above:

It shows a [square wave](https://en.wikipedia.org/wiki/Square_wave "square wave") sound generator that can be built with only three components, jumper wires and a power supply:
* inverting [Schmitt trigger](https://en.wikipedia.org/wiki/Schmitt_trigger "Schmitt trigger") IC, e.g. CD40106
* capacitor C
* resistor R

An inverting Schmitt trigger is an active electronic component whose output state can be triggered complementarily through an input signal, while the positive trigger threshold differs from the negative one. Feeding the output back to its input via a resistor and connecting a capacitor between the input and ground, known as RC circuit, creates a relaxation oscillator or [astable multivibrator](https://en.wikipedia.org/wiki/Multivibrator#Astable_multivibrator "astable multivibrator"). The resistor limits the current for charging the capacitor and both together determine the charging time.

<img src="https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/ST_inv.gif">

The frequency can be roughly calculated with this formula:

f=0,72/RC

However, manufacturing tolerances of all involved parts make it difficult to achieve exact results based on the formula. Since the field of application is artistic sound production, circuits should be evaluated by ear. But the formula shows that bigger RC values produce lower frequencies and vice versa. The frequency is determined through the capacitor C and the resistor R. Therefore, a [potentiometer](https://en.wikipedia.org/wiki/Potentiometer "potentiometer") instead of the latter enables pitch control. Other ways of controlling the frequency may be inserting [photoresistors](https://en.wikipedia.org/wiki/Photoresistor "photoresistor"), [force-sensitive resistors](https://en.wikipedia.org/wiki/Force-sensing_resistor "FSR") (FSR) or [flex sensors](https://en.wikipedia.org/wiki/Flex_sensor "flex sensor"). Adding circuit points to alter the sound through interaction allows building customized and versatile instruments.


## Logic Control

<img src="https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/Square-Wave.jpg">


In digital electronics 2-level logic, [binary numbers](https://en.wikipedia.org/wiki/Binary_number "binary number") are represented by two defined voltage levels that are specified by the used technology and circuit. For example signal ground in a given circuit can represent "0" while the positive voltage rail can represent "1". The two states "0" and "1" are also often referred to as "(logical) high" and "(logical) low", "true" and "false" or "ON" and "OFF".

A logic gate is a single input - output device, designed to carry out a specific [boolean operation](https://en.wikipedia.org/wiki/Boolean_algebra "boolean algebra"), mapped to two voltage levels. Over time, the two  alternating voltage levels may form a periodic rectangular waveform and the speed of switching between the two levels is perceived as pitch. Aperiodic switching will produce other sonic qualities such as noise or all kinds of texturized sounds. The ratio between the on-and-off states is by default 1:1, a 50% [duty cycle](https://en.wikipedia.org/wiki/Duty_cycle "duty cycle"). Further circuitry is needed to change this ratio, which alters the audio spectrum of the square wave.


## Electronic Components


The following is a list of CMOS chips and other integrated circuits for sound creation and processing. This list will be constantly extended during the seminar. It outlines for each chip its main applications and gives a short explanation. Pinout, functional diagram, truth tables and some basic example circuits are also shown. However the overview is not completed with theses examples and the main approach is to find variations, modifications or new creative combinations for experimental sound and music. Please refer to the manufacturer's technical data sheet for more detailed information.



### CD40106

The inverter is a basic part in digital electronics and performs the logic operation of negation. When the input is connected to ground, the output is pulled to V<sub>DD</sub> and vice versa. The CD40106 hex Schmitt trigger inverter offers six separate inverters in one chip that can be wired externally to build square wave oscillators. When using a potentiometer for frequency control, an offset resistor should be placed in series in order to prevent too low resistance between output and input.

*Applications:*
* oscillator
* clock signals

<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/CD40106.jpg>

Truth table
|Inputs|Outputs|
|----|----|
|0|1|
|1|0|

"1" = High Level  
"0" = Low Level


[CD40106 Sheet](https://www.ti.com/lit/ds/symlink/cd40106b.pdf?ts=1599062729936&ref_url=https%253A%252F%252Fwww.google.com%252F "CD40106")

### CD4093

The CD4093 contains 4 NAND Schmitt triggers, each providing 2 inputs and 1 output.

It acts as a square wave oscillator when the inputs are connected to form an inverter. The last two rows of the truth table indicate that one input has to be set to a logical high in order to attain inversion of the signal being present at the other input. When the second input is then wired like the CD40106 in the previous example, the CD4093 generates square waves too. In this configuration, oscillation can be inhibited by setting the first input to a logical low. This way, the first input acts as a control input for gating the oscillator.

*Applications:*
* gated oscillator / modulated square waves
* clock signals

<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/CD4093.jpg>

Truth table for NAND

|A|B|J=A NAND B|
|----|----|:----:|
|0|0|1|
|0|1|1|
|1|0|1|
|1|1|0|





[CD4093 Data Sheet](https://www.ti.com/lit/ds/symlink/cd4093b.pdf?ts=1599062791398&ref_url=https%253A%252F%252Fwww.google.com%252F "CD4093")



### CD4070

The CD4070 contains four Exclusive-OR logic gates. Each gate has two inputs and one output. The output is high when only one of the inputs is high and the other is low and vice verca. If both inputs are high or low, the output is low. If two square wave signals are connected to the input, the output extracts the difference which results in a frequency mixer like output signal. Frequency doubling can be achieved if one square wave is applied directly to one input and connected via a resistor to its second input with a capacitor to ground. The positive and negative edge of an incoming square wave now force the output to high, hence doubles the incoming frequency.


*Applications:*
* digital frequency mixer
* frequency doubler
* duty cycle adjustment


<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/CD4070.jpg>

Truth table for XOR

|A|B|Y = A XOR B|
|----|----|:----:|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|0|


[CD4070 Data Sheet](https://www.ti.com/lit/ds/symlink/cd4077b.pdf?ts=1606308007892&ref_url=https%253A%252F%252Fwww.google.com%252F "CD4070")


### CD4015

CD4015 IC consists of two four stage shift registers.

A shift register is built of a series of interconnected [flip-flops](https://en.wikipedia.org/wiki/Flip-flop_(electronics) "flip-flop"). A flip-flop or latch is a bistable multivibrator circuit. This means it has two stable states which represent either 0 or 1. The state of a flip-flop can be controlled by an input signal. A flip-flop is used to store 1 bit. In a shift register the incoming serial input data **D** is transferred to a parallel output register **Qn**. More specifically, when a memory content is stored in the first flip-flop, it is shifted to the next one, synchronized to the rising edge of a clock signal **CL**. A logical high at the reset pin is setting all outputs to zero. The reset pin should be set to low for a continuous operation.

*Applications:*
* sequencer / pattern generator


<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/CD4015.jpg>

Truth table for four stage shift register

|CL|D|R|Q1|Qn|
|:----:|:----:|:----:|:----:|:----:|
|/|0|0|0|Qn-1|
|/|1|0|1|Qn-1|
|``\``|X|0|Q1|Qn|
|X|X|1|0|0|

X   = Don't Care Case  
/   = Rising Edge  
\   = Falling Edge  

[CD4015 Data Sheet](https://www.ti.com/lit/ds/symlink/cd4015b.pdf?ts=1607676770686&ref_url=https%253A%252F%252Fwww.google.com%252F "CD4015")


### CD4022

CD4022 IC implements a binary counter/divider function. The positive edge of an incoming square wave, usually referred to as "clock signal", triggers successively the outputs. "Carry out" is outputting one cycle over 8 clock pulses.

*Applications:*
* counter
* wave shaper and staircase wave form generator
* sequencer

<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/CD4022_animated.gif>



<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/CD4022_Timing_Diagram.jpg>

[CD4022 Data Sheet](https://www.ti.com/lit/ds/schs027c/schs027c.pdf?ts=1599062824246&ref_url=https%253A%252F%252Fwww.google.com%252F "CD4022")

### CD4040

This IC performs frequency division. If a square wave is applied to the input, each output creates square waves at half the frequency of its preceding output, at which the first output Q1 applies its division to the input signal and oscillates at a rate at one half, Q2 at one quarter, Q3 at one eighth Q4 at one sixteenth and so on.

Control input "reset" triggers all output stages to "low". For continuously frequency division it should be kept at a logical low.

*Applications:*
* subharmonic oscillator

<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/CD4040.jpg>


Each output producing one octave lower than its previous output, respectively input.


The timing diagram shows the relation of voltage levels between all outputs of the CD4024 IC, a 7 output stage version:
<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/CD4040_Timing_Diagram.jpg>

[CD4040 Data Sheet](https://www.ti.com/lit/ds/symlink/cd4040b.pdf?ts=1600261370155&ref_url=https%253A%252F%252Fwww.ti.com%252Fproduct%252FCD4040B "CD4040")

### CD4046


Phase locked loop

*Applications:*
* tone distortion
* pitch tracking
* frequency multiplication


<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/CD4046.jpg>

[CD4046 Data Sheet](https://www.ti.com/lit/ds/symlink/cd4046b.pdf?ts=1599062962750&ref_url=https%253A%252F%252Fwww.google.com%252F "CD4046")


### CD4051

Multiplexer/Demultiplexer. All channels are off when inhibit input is set to "high".


*Applications:*
* wave shaping
* digitally-controlled analog switching
* signal routing

<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/CD4051_animated.gif>

Truth table
|C|B|A|ON CHANNEL(S)|
|----|----|----|:----:|
|0|0|0|0|
|0|0|1|1|
|0|1|0|2|
|0|1|1|3|
|1|0|0|4|
|1|0|1|5|
|1|1|0|6|
|1|1|1|7|

[CD4051 Data Sheet](https://www.ti.com/lit/ds/symlink/cd4051b.pdf?ts=1599079621658&ref_url=https%253A%252F%252Fwww.google.com%252F "CD405xB")


## Mixer
There are two ways of mixing signals together, active and passive mixing. Active mixing involves components, such as operational amplifiers, that need a power supply. Passive mixing works without an additional power supply, but introduces a voltage drop.

### Passive Mixer

Passive mixing is a very simple method that can be accomplished by using resistors for each source. The mixing resistors work as a voltage divider network and lower the amplitude of each signal. Therefore, the passive mixer doesn't give the sum of all input signals but the average. This is shown by the graph below, comparing one input signal to the output with a sine wave. To make it clearer, the other two input sources have 0 volts in the example. Small resistance values will drain more current and create distortion. Good values are between 10kΩ - 50kΩ. The advantage of this method is its low part count. To avoid attenuation and interaction between the signals and to obtain individual gain control, active mixing using an operational amplifier is preferred.

<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/passive_mixing.jpg>

<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/passive_mixing_plot.jpg>


### Active Mixer


For most audio applications it is desired to control the portion of each input signal in the sum of the output mix. For this, another class of active electronic components can be used, the [operational amplifier](https://en.wikipedia.org/wiki/Operational_amplifier "op amp") (op amp). The basic wiring is shown below. Besides its function as a mixer with gain control over every individual input by adding voltage dividers or potentiometers, it can also be used to achieve a desired output gain by modifying the the feedback resistor R<sub>F</sub> in relation to the input resistors R<sub>IN</sub> of each input. The minus sign in the formula indicates that the output voltage is inversed. To undo inversion, a second stage following the shown circuit can be used.

*Applications:*
* signal mixing
* gain control

<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/Summing_Inverting_OpAmp.jpg>

## Passive Filter

Tone control, modifying the frequency of a signal or creative equalization are very important processes when working with audio. A filter is frequency-selective and passes only a desired range of frequencies, which is called the pass band. Outside of this pass band, frequencies are attenuated or ideally completely reduced. The point between pass and stop band is called cutoff frequency. The simplest way to shape an electronic signal is the use of a combination of resistor and capacitor, an RC circuit. The circuit can be considered as a frequency dependent potential divider. Since no amplifying components are involved, the amplitude of the output is lower than the input amplitude. When a filter is designed with two passive components, the transition from pass to stop band is rather smooth.

<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/Passive_Filter.jpg>


## Potentiometer

A potentiometer is a passive component with three terminals, of wich one is connected to a movable contact, called wiper, that can be adjusted on a resistive track. The other two terminals are the ends of the resistor. If one end and the wiper are used, it forms a variable resistor. Configured as a voltage divider, potentiometric devices are used for volume control in audio applications.

<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/Potentiometer_Voltage_Divider.jpg>

<img src=https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/Volume_Control_Variable.jpg>


## Bill of Material

Below are examples of parts that can be used for this project.
All parts can be substituted with alternative components and equivalent foot prints.




No|Description|Package|Value|Manufacturer Part Number|Mouser-Nr.
| --- | --- | --- |--- | --- | --- |
1|Logic Gates CMOS Quad 2-In|DIP-14||CD4001BE|[595-CD4001BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4001BE?qs=Tv815z3GeNSKspfG7F34rg%3D%3D "CD4001")||
2|Specialty Function Logic Dual Comp Pair Plus|DIP-14||CD4007UBE|[595-CD4007UBE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4007UBE?qs=LfG3tU9ud8BdeBYIAnqsKQ%3D%3D "CD4007")||
3|Inverters Hex Inverter Buffer|DIP-16||CD4009UBE|[595-CD4009UBE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4009UBE?qs=VolsR0DjNPrED2AO%2FOVdHw%3D%3D "CD4009")||
4|Inverter Hex Schmitt Trigger|DIP-14||CD40106BE|[595-CD40106BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD40106BE?qs=YhsVCygOPE1CyKyInx%252Bh3Q%3D%3D&gclid=EAIaIQobChMIgtOchp_K6wIVBt-yCh0zXgXAEAAYASAAEgIDAPD_BwE/ "CD40106BE")||
5|Logic Gates Quad 2-Input|DIP-14||CD4011BE|[595-CD4011BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4011BE?qs=st7IWvlL5%2FgbunuzXw39Lg%3D%3D "CD4011")||
6|Flip-Flops Dual CMOS|DIP-14||CD4013BE|[595-CD4013BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4013BE?qs=pt%2FIv5r0EPc2Chv9B9JKAA%3D%3D "CD4013")||
7|Counter Shift Registers Dual 4-Stage Static|DIP-16||CD4015BE|[595-CD4015BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4015BE?qs=j01uVdFEFjH4vzjiL7DJWw%3D%3D "CD4015")||
8|Counter IC 10 Decade/Divider|DIP-16||CD4017BE|[595-CD4017BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4017BE?qs=IF4wzcbwb3rdXSZhHlgcJw%3D%3D "CD4017")||
9|Counter ICs CMOS Presettable Bin UP/Down Counter|	PDIP-16||CD40193BE|[595-CD40193BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD40193BE?qs=D5pVkbrsqqK9UQwfGopiNQ%3D%3D "CD40193")||
10|Counter IC CMOS Octal Counter|DIP-16||CD4022BE|[595-CD4022BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4022BE?qs=LU5rZWrBGo2Wnh%252BM60ZqEA%3D%3D "CD4022")||
11|Counter ICs 7-Bit Ripple-Carry|DIP-14||CD4024BE|[595-CD4024BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4024BE?qs=j%2FZo4ajzVJJKX%2F7efvSm1w%3D%3D "CD4024")||
12|Flip-Flops Dual Master/Slave|DIP-16||CD4027BE|[595-CD4027BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4027BE?qs=nMmhAzRCgdBAU0RPgOaejQ%3D%3D "CD4027")||
13|Counter ICs Preset UpDn Binary|DIP-16||CD4029BE|[595-CD4029BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4029BE?qs=q2XTDbzbm6C3NEJn1CP1SA%3D%3D "CD4020")||
14|Logic Gates Quad Exclusive|DIP-14||CD4030BE|[595-CD4030BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4030BE?qs=JHHQeKcAU3C7Kmjg3SCYVA%3D%3D "CD4030")||
15|Counter ICs 12 STAGE BINARY CNTR|DIP-16||CD4040BE|[595-CD4040BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4040BE?qs=L4Mc90zKIpgVInmXWEixLQ%3D%3D "CD4040")||
16|Phase Locked Loop|DIP-16||CD4046BE|[595-CD4046BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4046BE?qs=fvkeCqCHl3AX2sxIYB2bdg%3D%3D "CD4046")||
17|Multiplexer Switch ICs 8-Channel Analog|DIP-16||CD4051BE|[595-CD4051BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4051BE?qs=q2XTDbzbm6DxulBsMcV7tA%3D%3D "CD4051")||
18|Multiplexer Switch ICs 4-Ch. Analog|DIP-16||CD4052BE|[595-CD4052BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4052BE?qs=Tv815z3GeNSSxm5loQgO7w%3D%3D "CD4052")||
19|Counter ICs 14-Bit Ripple|DIP-16||CD4060BE|[595-CD4060BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4060BE?qs=5BZzbFV4k2vIRvFJ20ZWwg%3D%3D "CD4060")||
20|Analogue Switch ICs Quad|DIP-14||CD4066BE|[595-CD4066BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4066BE?qs=mTHRaKC2c7ObpofRtjqLig%3D%3D "CD4066")||
21|Logic Gates 8-Input NAND/AND|DIP-14||CD4068BE|[595-CD4068BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4068BE?qs=FM6NhYOeeBUbd80VDCMlFg%3D%3D "CD4068")||
22|Logic Gates Quad Exclusive OR|DIP-14||CD4070BE|[595-CD4070BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4070BE?qs=5WY7Uqh921w5Ya0dPgjorQ%3D%3D "CD4070")||
23|Logic Gates Quad 2-Input|DIP-14||CD4071BE|[595-CD4071BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4071BE?qs=D5pVkbrsqqJag2QszZHFMA%3D%3D "CD4071")||
24|Logic Gates Quad 2-Input|DIP-14||CD4081BE|[595-CD4081BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4081BE?qs=dQbkqP7qjaZ0jSz5I7zHYA%3D%3D "CD4081")||
25|NAND Logic Gates Schmitt Trigger|DIP-14||CD4093BE|[595-CD4093BE](https://www.mouser.de/ProductDetail/Texas-Instruments/CD4093BE?qs=X1HXWTtiZ0QxcrKuDdZ5rg%3D%3D "CD4093")||
26|Dual Op Amp|DIP-8||TL072IP|[595-TL072IP](https://www.mouser.de/ProductDetail/Texas-Instruments/TL072IP?qs=5BZzbFV4k2v7IBrcArRPQw%3D%3D "TL072")||
27|TL074|DIP-14||TL074CN|[595-TL074CN](https://www.mouser.de/ProductDetail/Texas-Instruments/TL074CN?qs=AMJt07B76uv7dLYnj7iLiQ%3D%3D "TL074")||
28|Operational Amplifiers - Op Amps Quad|DIP-14||LM324N|[595-LM324N](https://www.mouser.de/ProductDetail/Texas-Instruments/LM324N?qs=VolsR0DjNPqtt3qB38bTqw%3D%3D "LM324")||
29|Dual Op Amp|DIP-8||LM358P|[595-LM358P](https://www.mouser.de/ProductDetail/Texas-Instruments/LM358P?qs=X1HXWTtiZ0QtOTT8%252BVnsyw%3D%3D "LM358")||
30|Timers & Support Products Precision|DIP-8||NE555P|[595-NE555P](https://www.mouser.de/ProductDetail/Texas-Instruments/NE555P?qs=rkhjVJ6%2F3EIf4CWgjIKuKQ%3D%3D "NE555")||
31|Bipolar Transistors - BJT NPN|TO-92||BC547CTA|[512-BC547BTA](https://www.mouser.de/ProductDetail/ON-Semiconductor-Fairchild/BC547BTA?qs=TABiY4F6Vcf01oKZdNLa0w%3D%3D "BC547")||
32|Bipolar Transistors - BJT PNP|TO-92||BC557BTA|[512-BC557BTA](https://www.mouser.de/ProductDetail/ON-Semiconductor-Fairchild/BC557BTA?qs=Lnpu0ExxCB4xDNL%2Fw990%2FQ%3D%3D "BC557")||
33|3mm LED||Blue|151033BS03000|[710-151033BS03000](https://www.mouser.de/ProductDetail/Wurth-Elektronik/151033BS03000?qs=2kOmHSv6VfSefdpzrMLWSw%3D%3D "Standard LEDs - Through Hole WL-TMRW THT Mono Waterclr Rnd 3mmBlue")||
34|Diode|DO-35	||1N4148|[512-1N4148](https://www.mouser.de/ProductDetail/ON-Semiconductor-Fairchild/1N4148?qs=i4Fj9T%2FoRm8RMUhj5DeFQg%3D%3D "Dioden (Allzweck, Leistung, Schaltung) 100V Io/200mA BULK")||
35|3mm LEDs||Assorted Values|COM-12062|[474-COM-12062](https://www.mouser.de/ProductDetail/SparkFun/COM-12062?qs=WyAARYrbSnZzv4I0CztaEg%3D%3D "SparkFun Accessories LED - Assorted (20 pack)")||
36|3mm LED||Red|LTL-4222|[859-LTL-4222](https://www.mouser.de/ProductDetail/Lite-On/LTL-4222?qs=PaUBgWdAOGEl%252Bf85PeEXqA%3D%3D "Standard LEDs - Through Hole Red Transparent")||
37|MLCC|2.5mm |0.1µF|K104K15X7RF53K2|[594-K104K15X7RF53K2](https://www.mouser.de/ProductDetail/Vishay-BC-Components/K104K15X7RF53K2?qs=%2Fha2pyFadujQ%252Bv0xHOEo91Fp6rFGP5krxuyVhQ%252B1w%252BsnJ7knhvdeQDps3CPFUP6U "Multilayer Ceramic Capacitors")||
38|Aluminum Electrolytic Capacitors|2mm |10µF|ECE-A1HKA100I|[667-ECE-A1HKA100I](https://www.mouser.de/ProductDetail/Panasonic/ECE-A1HKA100I?qs=rMMd5vBiahpRBI%252BQ5jocrQ%3D%3D "Aluminum Electrolytic Capacitors")||
39|Leaded Resistors (Metal or Carbon Film)|| Assorted Values (12 Ω - 1 MΩ) ||||
40|Leaded Capacitors (Ceramic, Film and Electrolytic)|| Assorted Values (56pF - 47µF)||||
41|Potentiometer|9mm|20kΩ|PTV09A-1015U-B203|[652-PTV09A-1015UB203](https://www.mouser.de/ProductDetail/Bourns/PTV09A-1015U-B203?qs=pxDZlBjcsCjw%252BRGNXMHqEQ%3D%3D "Potentiometers PANEL CONTROL - 9MM-ST-CARBON 20 kohms 15 mm")||
42|Potentiometer|9mm|100kΩ|PTV09A-4015U-B104|[652-PTV09A-4015UB104](https://www.mouser.de/ProductDetail/Bourns/PTV09A-4015U-B104?qs=pxDZlBjcsCi2tw983aFXVQ%3D%3D "Potentiometers PANEL CONTROL - 9MM-ST-CA 100 kohms 15 mm")||
43|Potentiometer|9mm|500kΩ|PTV09A-4015U-B504|[652-PTV09A-4015UB504](https://www.mouser.de/ProductDetail/Bourns/PTV09A-4015U-B504?qs=pxDZlBjcsCherlTtJcuegw%3D%3D "Potentiometers PANEL CONTROL - 9MM-ST-CA 500 kohms 15 mm")||
44|Potentiometer|9mm|1MΩ|PTV09A-4020F-B105|[652-PTV09A4020FB105](https://www.mouser.de/ProductDetail/Bourns/PTV09A-4020F-B105?qs=%252B9%2Fcbd0IE0TagBKq%252BGRbqw%3D%3D "Potentiometers 1M 20% 9MM CARBON POT")||
45|Potentiometer|9mm|10kΩ|PTV09A-6230F-B103|[652-PTV09A-6230FB103](https://www.mouser.de/ProductDetail/Bourns/PTV09A-6230F-B103?qs=pxDZlBjcsCg8U96haor%252BfA%3D%3D "Potentiometers PANEL CONTROL - 9MM-ST-CARBON 10 kohms 30 mm")||
46|Potentiometer|9mm|50kΩ|RK09D113000K|[688-RK09D113000K](https://www.mouser.de/ProductDetail/Alps-Alpine/RK09D113000K?qs=oKW7zmyQiO5%2FMNsP8zcsfA%3D%3D "Potentiometers 9MM 50K V/ADJ")||
47|Photoresistor|||SEN-09088|[474-SEN-09088](https://www.mouser.de/ProductDetail/SparkFun/SEN-09088?qs=WyAARYrbSnbNBfpKra%2FIvQ%3D%3D "Photoresistor")||
48|Photoresistor|||161|[485-161](https://www.mouser.de/ProductDetail/Adafruit/161?qs=GURawfaeGuDpQ5XPTNqKUw%3D%3D "Photoresistor")||
49|Force Sensitive Resistor|||1075|[485-1075](https://www.mouser.de/ProductDetail/Adafruit/1075?qs=GURawfaeGuDaOmXus2Zwlg%3D%3D "Force Sensitive Resistor")||
50|Flex Sensor|55.37 mm ||FS-L-0055-253-ST|[744-FS-L-0055-253-ST](https://www.mouser.de/ProductDetail/Spectra-Symbol/FS-L-0055-253-ST?qs=avFSO%252B7Rp3iBf0lmBypxdg%3D%3D "Industrial Motion & Position Sensors Flex Sensor 55.37mm Linear")||
51|Force Sensors|||FSR06BE|[588-FSR06BE](https://www.mouser.de/ProductDetail/Ohmite/FSR06BE?qs=0lSvoLzn4L%252BLr%252BqMretnhw%3D%3D "Force Sensors & Load Cells 14.7mm Round Solder Tab")||
52|Position Sensors SoftPot|500mm|20kΩ|SP-L-0500-203-3%-ST|[744-SP-L-0500-2033ST](https://www.mouser.de/ProductDetail/spectra-symbol/sp-l-0500-203-3-st/?qs=rVuZtzXoae5%2FClXxQbhQtw==&countrycode=DE&currencycode=EUR "SoftPot")||
53|Position Sensors SoftPot Low Form-Factor|50mm|10kΩ|SP-L-0050-103-1%-ST|[744-SPL00501031%ST](https://www.mouser.de/ProductDetail/spectra-symbol/sp-l-0050-103-1-st/?qs=rVuZtzXoae5IELdwVMEdkA==&countrycode=DE&currencycode=EUR "SoftPot")||
54|Push Button|5,9mm|OFF - (ON)|1-1825910-4|[506-1-1825910-4](https://www.mouser.de/ProductDetail/TE-Connectivity-PB/1-1825910-4?qs=pffCcXpkxLwYJJd3DYaJ7Q%3D%3D "Tactile Switches 6MM ACTHIGH TEMP TACT SWITCH")||
55|Pin Header|1 x 36 2.54mm ||68797-436HLF|[649-68797-436HLF](https://www.mouser.de/ProductDetail/649-68797-436HLF "Headers & Wire Housings BREAKAWAY HEADER 36")||
56|Pin Socket|1 x 32 2.54mm ||61303211821|[710-61303211821](https://www.mouser.de/ProductDetail/710-61303211821 "Headers & Wire Housings WR-PHD 2.54mm 32Pin Socket Header")||
57|Pin Socket|1 x 36 2.54mm ||801-87-036-10-001101|[437-8018703610001101](https://www.mouser.de/ProductDetail/437-8018703610001101 "Headers & Wire Housings")||
58|Pin Socket|1 x 8 2.54mm ||8Fx1L-254mm|[992-8FX1L-254MM](https://www.mouser.de/ProductDetail/992-8FX1L-254MM "8-pin wire wrap fem header")||
59|Socket||1 Row 21 Positions|801-83-021-10-001101|[437-8018302110001101](https://www.mouser.de/ProductDetail/Preci-dip/801-83-021-10-001101?qs=FtMuP6KVi2SB4UyszASQfQ%3D%3D "Headers & Wire Housings")||
60|Component Sockets|DIP-8||1-2199298-2|[571-1-2199298-2](https://www.mouser.de/ProductDetail/TE-Connectivity/1-2199298-2?qs=%2Fha2pyFadugJp%2F0oQpeWgcdKbmhfM%252BG5f2aD9jt0RGQdskDEwvmLNQ%3D%3D "Component Sockets 8P DIP")||
61|Component Sockets|DIP-14||1-2199298-3|[571-1-2199298-3](https://www.mouser.de/ProductDetail/TE-Connectivity/1-2199298-3?qs=%2Fha2pyFadugJp%2F0oQpeWgR9Lzm5j4WzFAMc1jcrVNfu7vZxg2U3Y3Q%3D%3D "Component Sockets 14P DIP")||
62|Component Sockets|DIP-16||1-2199298-4|[571-1-2199298-4](https://www.mouser.de/ProductDetail/TE-Connectivity/1-2199298-4?qs=%2Fha2pyFadugJp%2F0oQpeWgVBpv3LzMBBwVqoB59rQ35Apde3oZfgpGA%3D%3D "Component Sockets 16P DIP")||
63|Jumper Cable|15cm||MIKROE-513|[932-MIKROE-513](https://www.mouser.de/ProductDetail/932-MIKROE-513 "Jumper Cable")||
64|Pin Header|1 x 36 2.54mm ||10129378-936002BLF|[649-1012937893602BLF](https://www.mouser.de/ProductDetail/649-1012937893602BLF "Headers & Wire Housings ECONOSTIK HEADER SR VT TH 1X36")||
65|Piezo Buzzers & Audio Indicators|12mm||7BB-12-9|[81-7BB-12-9](https://www.mouser.de/ProductDetail/Murata-Electronics/7BB-12-9?qs=PSBlsCV0pRZoIir08fDstg%3D%3D "Piezo disk")||
66|Piezo Buzzers & Audio Indicators|20mm||7BB-20-3|[81-7BB-20-3](https://www.mouser.de/ProductDetail/Murata-Electronics/7BB-20-3?qs=JJeuIrkYhekHouIxq0fvsw%3D%3D "Piezo disk")||
67|Piezo Buzzers & Audio Indicators|27mm||7BB-27-4L0|[81-7BB-27-4L0](https://www.mouser.de/ProductDetail/Murata-Electronics/7BB-27-4L0?qs=PkW2zKsTBmE%2F8VGC6sKDJA%3D%3D "Piezo disk")||
68|Piezo Buzzers & Audio Indicators|35mm||7BB-35-3C|[81-7BB-35-3C](https://www.mouser.de/ProductDetail/Murata-Electronics/7BB-35-3C?qs=gRcAz2mAxnN1kUKNPnYYbw%3D%3D "Piezo disk")||
## Requirements

Helpful tools and useful materials:


* Small mixing desk.
* Active loudspeakers.
* Worktables.
* Screw drivers.
* Metric screw assortment (M3, ~12mm) and nuts.
* ESD electronic diagonal cutter.
* Precision cutter.
* Stranded wires.
* Laboratory power supply & connectors (preferable 4mm banana laboratory connectors).
* Jumper cables and jumper wires.
* Digital multimeter (DVM).
* Digital storage oscilloscope (DSO).
* Temperature-controlled soldering station.
* Breadboards.
* Good light conditions.


# Projects

The artistic range of applications for electronic projects in the fields of experimental sound, interactive music and sound art is quite large. The next sections feature works made in the context of this seminar.

## CMOS Experimenter Boards

During the summer semester 2020, experimenter boards for CMOS logic chips and a  prototyp of a corresponding musical interface were conceived and built. The boards and interfaces were used for a group live performance in front of the Federal Prosecutor's office in Karlsruhe.

The motivation behind this project was to produce a set of PCBs to evaluate logic ICs for sound creation and composition in artistic and educational fields. The idea of providing a CMOS experimenter board was initiated particularly with regard to today's availability of PCB manufacturers and affordable prizes. PCB prototyping and production is now completely based on computer aided electronic design (EDA) while manufacturers offer professional quality at very low costs, even for small board quantities.

Each PCB is designed around individual standard CMOS chips and their particular functions in order to create sound. The boards provide inlets and outlets, testing points, sockets, vias and pads for changing values of electronic parts and wiring alternative external circuitry. The modules can be easily extended and interconnected. This allows the user to manipulate circuit points with potentiometers, buttons, switches or sensors and to apply control voltages at appropriate input points.

<img src="https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/CMOS_Synthesizer.jpg">

It simplified prototyping and made customized configurations highly flexible. The experimenter boards can serve as sound modules for interactive music in live performance or installative environments as well as for algorithmic compositions. By combining several boards with different logic functions, complex switching performance can be achieved, ranging from  modulated frequencies and interesting audio spectra to slow, rhythmic pulses or tone sequences. Audio and control signals are exchanged between boards via jumper cables or wires. A wide range of circuit examples with CMOS chips can be found on DIY websites and are a subject of discussion in various internet forums. These circuits can be a good basis for experimenting with CMOS chips. In addition, it is recommendable to use data sheets for all active components used in electronic projects. Power supply for the boards should comply with the power ratings of the used ICs, which is typically between 3V - 18V DC. LED series resistors need to be calculated accordingly. For the experimenter console, 9V power supply for guitar effects work well.

<img src="https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/Experimenter_Modules.jpg">

Furthermore, the project includes laser-cutting files for a desktop console on which the boards can be mounted with screws. A power supply can be connected through the frame via banana connectors and distributed to the each board.


<img src="https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/acrylic_transparent.jpg">

All involved files are made available online. This includes [ECAD](https://github.com/SCLW/Circuitry-Based-Sound/tree/master/PCB_Hardware/Schematics "Schematics"), [Gerber](https://github.com/SCLW/Circuitry-Based-Sound/tree/master/PCB_Hardware/Schematics "Gerber") and [vector files](https://github.com/SCLW/Circuitry-Based-Sound/tree/master/Case "Case") as well as [bill of materials](https://github.com/SCLW/Circuitry-Based-Sound#bill-of-material "BOM"). Please do take note that these files refer to a prototype which hasn't been evaluated yet in detail. The board and the laser cutting files work but can be optimized.


## Authors

Zhen Bian  
Hangyan Chen  
Jeongmin Han  
Anna Helsen  
Jihye Jang  
Xingchen Liu  
Su Lu  
Ruoyi Qiu  
Vivian Reuter  
Arno Schlipf   
Florian Schwarz   
Christina Vinke  
Yunfei Zhang  
Pei Zhou  

**Lorenz Schwarz** - *lecturer*

<img src="https://github.com/SCLW/Circuitry-Based-Sound/blob/master/img/Bread_Board.jpg">

## License

The content of this documentation is licensed under the [Creative Commons Attribution 3.0 Unported license](https://creativecommons.org/licenses/by/3.0/ "CC BY 3.0"), software is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details. Copyright remains with the author(s)

## Acknowledgment

* Thanks to Holger Förterer and Dr. Paul Modler


