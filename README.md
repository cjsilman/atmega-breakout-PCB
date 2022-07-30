# atmega-breakout-PCB
This PCB project is meant to replicate a simple atmega32u4 microcontroller board with GPIO pinouts. It contains a peripheral USB for programming and powering.

![image](https://user-images.githubusercontent.com/75451857/181871264-cc567129-c8c9-423a-ae4a-b7c5cdc2666f.png)

This is the first MCU PCB I designed on my own.

Here are a couple things I learned along the way:
1. For each VCC pin, you typically want a 100nF decoupling capacitor and 10uF bulk decoupling capacitor to help with the stabilization of the input voltage.

![image](https://user-images.githubusercontent.com/75451857/181871890-8593983c-c843-45ff-a511-f837e8bc1700.png)

2. The load capacitance of the crystal oscillator is used to calculate the decoupling capacitors associated with it. While 22pF capacitors is quite common, it is important to choose proper capacitor values to allow for more accurate and stable results of the crystal.

 The capacitor values can be broken down into a formula like this:
 - C1, C2 = 2*Cload-2*Cstray

 Cload, or the load capacitor, is retrieved from the datasheet of the specific crystal you choose.
 - Cstray, or the stray capacitance, is the typically between avalue of 3-5pF.
 - Cstray is the parasitic capacitance formed between two traces separated by a dielectric (caused by potential different genred by current carrying traces running in   close proximity to one another)
 
 ![image](https://user-images.githubusercontent.com/75451857/181871896-023a45bc-4d45-4361-9f0d-b109608ca39e.png)
 
 3. The MCU datasheet will have a lot of guidelines for when it comes to designing with that specific IC. Make sure to follow them.
 
 4. Using a GND plane allows for better signal integrity and more resistance to interference.
 - Using one via per GND pin reduces the issue of potentially creating a ground loop and minimizes noise.
