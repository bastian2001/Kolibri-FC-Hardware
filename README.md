# RP2350 Flight Controller for FPV

This is the hardware part of the Kolibri Flight Controller. Currently there are two versions: A 30mm (V0.5) and a 20mm (V0.6) FC. They are both pretty similar in terms of features, and mostly differ in their form factor and ease of soldering, but also featurewise, they are slightly different. They both feature:

-   3-8S input voltage
-   RP2350 microcontroller
-   2.4GHz ELRS onboard
-   5V 2.5A, 10V 2.5A buck converters
-   Analog character based OSD similar to Betaflight/iNav
-   Barometer (STM LPS22HB)
-   Speaker driver up to VBat

They differ slightly:

-   Gyro: BMI270 (30mm), ICM-42688-P with separate LDO (20mm)
-   ELRS: Gemini with PA/LNA (30mm), only one antenna with no PA/LNA (20mm)
-   Blackbox: SD slot (30mm), 256MiB flash chip (20mm)
-   20mm has a switchable 10V rail, 30mm uses that pin for a current sensor

While the 30mm FC works really well, the 20mm FC is just ordered and completely untested. While most features are a size decision, I will probably phase out the BMI270 and switch over to the ICM-42688-P, and I'd count a switchable 10V rail as more important than a current sensor, so as long as a 2350 is used, I will probably do that in the future, too. An RP235xB (only feasible on 30mm FC) has more pins though and might offer more features down the line, too.

The firmware and configurator can be found [here](https://github.com/bastian2001/Kolibri-FC).

<img src="./PCB%20Version%200.6/export/front.png" alt="Front side of FC" style="display:inline-block; max-width: 49%;"/>
<img src="./PCB%20Version%200.6/export/back.png" alt="Back side of FC" style="display:inline-block; max-width: 49%;"/>
