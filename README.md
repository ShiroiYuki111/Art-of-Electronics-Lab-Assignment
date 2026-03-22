# Circuit Challenges: Resistors, LEDs, and Ohm's Law

This repository documents the physical circuit builds, theoretical explanations, and answers to the conceptual questions posed during the "Resistors, LEDs, and More" lab.

---

## Challenge 1: Bright Bright Lights

**The Problem:** When wiring multiple LEDs in a single path (in series), we observe two major issues:
1. **What happens to the overall brightness?** The overall brightness decreases drastically. Each time current meets a resistor or an LED, the power source must use some of its voltage to push charge through it. With 4 LEDs in series, the voltage drops are split across all components, leaving barely enough voltage to turn the LEDs on.
2. **What happens if you remove just one LED?** All the LEDs go out. Because they are all wired on the exact same path, removing one breaks the closed circuit loop necessary for electrons to flow.

**The Solution:**
To make 4 LEDs shine at maximum brightness so that removing one doesn't turn off the rest, they must be wired in **parallel**. 

I wired the circuit so that each LED has its own independent path from the 9V power source to ground. To ensure the LEDs do not blow out (as LEDs are not Ohmic devices and will pull too much current if left unchecked), each individual path includes its own 200 ohm current-limiting resistor. Because each path is connected directly to Vcc and ground, the voltage drop across each resistor/LED combo is the same as the battery voltage, allowing for maximum safe current to flow through each LED individually.

![Challenge 1 Circuit]  (![20260317_125637 jpg](https://github.com/user-attachments/assets/52045d94-fc75-4141-807f-4bb29ba1c564))


---

## Challenge 2: Meter Mystery

**The Goal:** Generate exactly 9.0 mA of current in a circuit using only a 9V battery and 200 ohm resistors. 

**The Math & Solution:**
Resistors are Ohmic devices, meaning they follow Ohm's Law: V = IR. 
We know our voltage (9 V) and our target current (9.0 mA, or 0.009 A). Using Ohm's Law, we can calculate the total required equivalent resistance:
* 9 V = 0.009 A * R
* R = 1000 ohms

Since we only have 200 ohm resistors available, we must wire them in series. When resistors are in series, their total resistance is the sum of the individual resistances (Rt = R1 + R2 + R3...). 
To reach 1000 ohms, we place five 200 ohm resistors in a single path:
* 200 + 200 + 200 + 200 + 200 = 1000 ohms

I wired the five resistors in series and connected the multimeter in series (acting as an ammeter) to close the loop and verify the current. The meter reads approximately 9.0 mA, proving the calculation correct.

![Challenge 2 Circuit]( **note** We did the circuit and showed it to sir but we forgot to any picture of it)

---

## Challenge 3: Turn the Lights Off

**The Goal:** Instead of an LED turning *on* when a push button is pressed, wire the circuit so the LED is normally *on*, and turns *off* only when the corresponding button is pressed.

**The Solution:**
This is achieved by intentionally creating a "short circuit" across the LED. 

Normally, the current flows from Vcc, through a current-limiting resistor, through the LED, and down to ground, keeping it lit. To change this behavior, I placed a push button in parallel with the LED. When the button is pressed, it connects the path before the LED directly to ground via a jumper wire. 

Current always favors the path of least resistance. The jumper wire has virtually zero resistance compared to the LED, so the current bypasses (or "shorts") the LED entirely, flowing through the button instead and causing the light to turn off while the button is held.

![Challenge 3 Circuit](https://github.com/user-attachments/assets/97fc6cce-9d6c-43ed-8d2c-d33631249861)


---

## Challenge 4: Color the Rainbow

**The Goal:** Wire a Tri-Color (RGB) LED using different analog control methods for each color channel to experiment with color mixing. 

**The Solution:**
A tri-color LED consists of three individual LEDs (Red, Green, Blue) sharing a common ground (the longest leg). I grounded the common terminal and wired the other color channels as follows:

* **Red Channel:** Wired from Vcc -> 200 ohm resistor -> Push Button -> Red terminal. This acts as a simple binary on/off switch.
* **Green Channel:** Wired from Vcc -> 200 ohm resistor -> Light Dependent Resistor (LDR) -> Push Button -> Green terminal. An LDR's resistance increases in darkness and decreases in light. By casting a shadow over the LDR, the resistance increases, restricting the current and effectively dimming the green LED while the button is pressed.
* **Blue Channel:** Wired from Vcc -> 10K Potentiometer -> 200 ohm resistor -> Push Button -> Blue terminal. The potentiometer acts as a variable voltage divider. By turning the knob, I can manually adjust the resistance and smoothly vary the brightness of the blue light. *(Note: The fixed 200 ohm resistor is critical here; if the potentiometer is turned all the way down to zero resistance, the 200 ohm resistor prevents the blue LED from burning out)*.

By combining the button presses and varying the physical resistance on the Green and Blue channels, a wide spectrum of mixed light colors can be generated.

![Challenge 4 Circuit](![IMG-20260318-WA0004 jpg](https://github.com/user-attachments/assets/04a3c00e-955c-445b-afe4-6e386a8b2e03)
