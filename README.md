# ALÉR-ION OPEN SOURCE HYDROGEN FUEL CELL
*Note: The full documentation for this project is in progress. Sections marked with "(...)" will be updated in a near future. Feel free to contact me at mederic.chalifour.1@ulaval.ca for any question.*

Alérion Supermilage is a student group at l'Université Laval who focusses on the developpement of high efficiency vehicles for various competitions. Up until 2024, the team always relied on an internal combustion engines. They then transitioned toward an electric-driven system with a battery.

In 2025, the project of a self-made hydrogen PEM fuel cell was born. With the spirit of sharing knowledge and helping others develop this technology, all the relevant design files are release as an open-source project.

This is a PEM open cathode fuel cell which turns pure (or prehumidified) hydrogen gas into electrical power.

**DISCLAIMER: At the moment of writing this, the prototype still has reliability issues. This stack is prone to leaking. Alérion Supermileage waives any responsability related to the usage of this fuel cell design. Note that hydrogen is a flammable gas. Use these files at your own risks.**

<img width="350" alt="{643E1C10-7D2D-44C4-A4DE-DCD97C1D8028}" src="https://github.com/user-attachments/assets/eed6cbb9-c54b-474c-95cf-ead6003d7253" />
<img width="200" alt="image" src="https://github.com/user-attachments/assets/e399f368-4ab9-4bef-b5a3-1159c8faaea8" />



# Stack general design
This project was realized as a "Projet de fin d'étude" and the final design report is available (in french) in [`Additional documentation/Rapport_final_PFE.pdf`](https://github.com/Alerion-SuperMileage-UL/ALER-ION-open-source-fuel-cell/blob/f2cdef219edfe725619d7147de9b8b1a14c1f4f9/Additional%20documentation/Rapport_final_PFE.pdf). 
(...)

# CAD files
(TO DO)

# Bill of material
(TO DO)

# Membrane Electrode Assembly (MEA)
  ## Proton exchange membrane
  The proton exchange membrane used was a [HP9-Pt ePTFE Reinforced, Pt Impregnated PFSA Membrane](https://www.fuelcellstore.com/eptfe-reinforced-pfsa-membrane-9-microns-pt-impregnated?search=78010010) from the [Fuel Cell store](www.fuelcellstore.com).

**Note:** 

* The membrane is shipped with a plastic cover film on one side. This film is useful to hold the membrane flat during the cutting and hot pressing steps, but should be remove before the stack assembly.
* Being only 9um thick, this membrane was selected aiming for high performances. However, even though it could handle the working pressure (~6 psi) when tested on in a single cell stack, it was shown to be a weak point when scaling up to multiple cells. It seams to be easily punctured or teared, either in the manual assembly process or by the hydrogen pressure.
* " [...] *This membrane has a cover film on one face in order to protect the membrane during shipping.  Platinum impregnation is done on the face that is away from the cover film. For best utilization of the Pt impregnation from the membrane manufacturer, it is recommended that the Pt side is placed toward the anode of the electrolyzer cell (cathode of the fuel cell) electrochemical cell.  This Pt impregnation is actually a Pt nanopowder that is incorporated into the entire surface of the membrane on the side opposite the single backing.  This platinum layer is not sufficient to sustain the electrochemical reactions of the cells, it is only intended to react the minute crossover gases that occur naturally in all membranes.* [...]" 

**Recommandation:** For future developpement, it might be wiser to start using a thickness closer to the industry standard of 50 um to obtain a reliable stack, and then go down in thickness to optimise the performances.

  ### Automated cutting
  In order to cut each membrane precisely and reliably, an *Ender 3* 3D printer was converted to a CNC drag knife using a "plotter blade". During this process, the membrane was left on its protective plastic film.

**Close up picture of the cutting process:**

<img width="156" alt="image" src="https://github.com/user-attachments/assets/7160e051-dac2-477e-b382-158644859551" />

(TO DO: path to the cad file.)



  ## Electrode

The electrode selected for this project were the [2 mg/cm² Platinum Black - Carbon Cloth Electrode (W1S1011)](https://www.fuelcellstore.com/carbon-cloth-2-ptb-gas-diffusion-electrode-w1s1011?search=11060067) from the [Fuel Cell store](www.fuelcellstore.com). They were cut in 30mm X 30mm using a utility knife.

**Note and recommandation:** A high platinum loading of 2 mg/cm² was selected aiming for high performances. This choice inflates the cost of the stack by a lot and a lower platinum loading (0.5 mg/cm² for example) could be used to reduce the testing and developpemement cost. Also note that the carbon clothe electrode, which was selected for being easier to work with compared to carbon paper electrode, are better suited at high humidity level [(Wang, 2007)](https://doi.org/10.1016/j.electacta.2006.11.012).

  ## Hot press
To make each MEA, the precut membrane is hot pressed between to precut electrode. The heated press used in this project is a *5 Ton Portable Hydraulic Heat Press Machine 2.3 x 4.7 Inch*.

<img width="156" alt="image" src="https://github.com/user-attachments/assets/18015150-ff39-41fa-bc1a-4f7113b10202" />

For each MEA, a printed template and some tape were used to aligned the electrode to the membrane. The membrane was left on its plastic protective film during the pressing but the bottom electrode was inserted between the membrane and the film by lifting the corner with some tweezers (beware not to scratch the membrane). Note that the platinum coating of the electrodes must face the membrane. 

Each MEA was hot pressed at 66 kg/cm², 97°C for 3.56 minutes to optimize the stack's performances [(Okur, 2013)](https://doi.org/https://doi.org/10.1016/j.energy.2013.05.001). The pressure was set suspending a weight on the press lever (acounting for the hydraulic mecanical advantage) and considering the area of the electrodes only (9 cm²).

  ## CAD file
(???)


# Graphite flow plates
The flow plates (bipolar plates), were made of 0.125" thick [Fully Resin Impregnated Graphite Plates](https://www.fuelcellstore.com/impervious-bipolar-graphite-plates). 
  ## Machining
  Each Plate were manufacture using a small benchtop CNC router (_Genmitsu CNC 3018-PRO_) with a 1/32" endmill.

**Note:** 
* Machining graphite produces a very fine dust. This should be done in a well ventilated area with appropriate respirators. A shop-vac was used to further control the produced dust.
* Machining parameter: (TO DO)
  ## Flow field design and geometry
    Multiple flow fields geometry were tried and the ones producing the most power were selected. However, it should be noted that their was a high degree of uncertainty on the results so this process should be done again in the future.
    ### Hydrogen side (anode)
  Among others, the following flow fields were tried on the anode side:

![IMG_5936 (1)](https://github.com/user-attachments/assets/88fe3a32-2230-47bb-8c2d-f624937bab28)


  The simple serpentine flow field was selected.
<img width="788" height="594" alt="{30DB0875-6CFB-4B4F-8EC1-B9351816C968}" src="https://github.com/user-attachments/assets/16e817ca-90a8-40be-8056-ff77a9f65600" />

### Air side (cathode)

  All cathode flow fields that were tried followed the same idea of straight channels. The selection process was done before the optimisation of the gasket system. Indeed, nickel strips were added as back support for the gasket. The initial design was thus on that allowed the first PTFE gasket to self support and wasn't necessarely the most efficient one.

  <img width="775" height="489" alt="{ACC28917-BCA8-4B8C-A650-7DEC884F8421}" src="https://github.com/user-attachments/assets/692d02ef-7ed7-42c2-9434-545a9bc5e5ca" />

  **Note:** 
  * The cathode design should be a balance between the conductivity (more graphite in contact with the electrode) and air availability (less graphite in contact with the electrode)
  * The depth of the channels also affects the strength of the plates. This should also be considered as cracked plated cause leakage.
### Other features
  #### O-ring slots
  The first design of the sealing system included o-rings on both sides of the bipolar plates. These are no longer in the design as its sealing ability was highly sensitive to the o-ring grooves depth, causing reliability issue. The same plates were later retrofitted to work with flat gaskets. The cathode side o-ring grooves were filled using silicone and some custom 3D printed spacers. The cathod side o-ring grooves can thus be remove from later version without any trouble (probably...). The anode side groove is also not used anymore, further tests should be conductd before removing it from the design as the gasket system was designed to fit on plate with this feature. If removed, one possible risk chould be that the current EPDM gasket which had this space to be squished-in before (thus not geting out of the PTFE subgasket), could reach the membrane and damage it. New design still shoudn't include this feature, but carefull consideration must be taken if the gasket system remains unchanged.
  #### Holes
  Each flow plates has four holes: two port (inlet and outlet) and two other for the positioning rods.
  ### End flow plates
  The end flow plates must be different to allow contact with the current collectors without causing any leaks. For the cathode side of the stack, the last flow plate didn't have the inlet/outlet holes and the anode side of the plate was left uncarved. This allowed maximal contact with the current collector while elimating the need for a sealing system around the ports.

  For the anode side of the stack, where the inlet and outlet are, the o-ring grooves of the cathode side of the plate were not filled like the other plates. At least for this last plate, the o-ring grooves needs to stay in the design. Moreover, although it's not necessary, the cathode side flow fields can be removed to allow maximum contact with the current collector.
  ## CAD file
  (...)




# Sealing and gaskets 
Sealing the fuel cell turned out to be an unforseen major challenge of this project. During this process, multiple iterations of the gasketing system were tried and a procedure to test out the performance was developed. This section presents this procedure, along with the final design of this system.

(TO DO: sealing diagram)

## CAD file
(...)

## Testing procedure
Each new gasket system needed to pass 3 distinct test.
### Electrical contact
First the gasket shouldn't affect the electrical performance of the fuel cell. In other words, we had to ensure that the electrical resistance between the carbon clothe electrodes and the graphite bipolar plates didn't increase when the gasket was added. This meant that the gaskets, once compressed, shouldn't be thicker than the electrodes. To test this, we used a stack of two bipolar plate with the current collectors and sandwiched only one electrode, without the membrane and the gasket to measure the resistance. The voltage drop was measured with constant current power supply of 5A applied on the current collectors. This baseline resistance was on the order of 9mOhm. Then the same experiment was repeated with the gasket system (half of it if it was symetrical, else two stacked electrode are required). The resulting resistance had to be in the same range. This test was also used to determined the effect of different torque on the compression screws on the cell resistance.
### Membrane integrity
During the testing phase, we observed that some gasket systems would damage the proton exchange membrane. In other words, squishy materials, like EPDM rubber, would grip on the membrane and stretch it out, causing small tears which majorly compromised the sealing structure. This observation led to the introduction of a thin PTFE sub-gasket in the design. When we tested different system, instem of testing with a new MEA each time, we would try with a simple humidified membrane and then observe it directly (the membrane shouldn't be deformed or damage by compressing it in the fuel cell).
### Leak test
The final test for the fuel cell was a submerged leak test. For this test, some compressed air was used to see if the fuel cell would hold the design pressure (6-10 psi). Note that it was simpler and safer to use air from the workshop than to go in the lab to try this with hydrogen. Then, the fuel cell was submerged in distilled water in a transparent pot to identify the origin of the leaks (or to find smaller ons). Each new design was first tested with only one or two cells, and later retested with more and more cells to validate the sealing system.


## Main gasket
The last iteration of the main gasket was cut out of a 15 mil EPDM 50A rubber sheet. It was cut using the same procedure as the proton-exchange membrane, with double sided tape (from Dollarama) to hold it to the 3D printer bed. This procedure was far from perfect as the rubber tends to be dragged up by the cutting blade. Multiple slow passes were made to alleviate this issue, but the fail rate was still high. A real CNC drag knife with a longer cutting blade, or laser cutting might help.

For further iteration, harder rubber (EPDM 70A) should be tried as it would probably be easier to cut, and it might hold pressure better. 

The benefit of this material, over teflon, which is way easier to cut-out, is that it compresses well, allowing a good electrical contact and a good seal at a resonable compression (too much compression breaks the graphite). However, it also caused several issues. 

## Subgasket
First, because of its "squishyness" and good gripping properties, when compressed, the EPDM gasket  would grip on the proton exchange membrane (PEM) and tear it has the contact surface would expand under compression. To solve this, a 1 mil PTFE sub-gasket was added (this feature is known as edge protection [(Min Wang et al 2019)](https://iopscience.iop.org/article/10.1149/09208.0351ecst)). This created a sliperry protective layer between the PEM and the EPDM gasket, without compromising the seal. It was cut out using the same proceduree as the PEM and the EPDM gasket. For further improvements, 2 mil PTFE subgasket could be tried to improve the durability of this piece, as it tends to wear out after being compressed.

## Back support and margins
Next, because of its high compressibility, the EPDM gasket tended to squish in the hydrogen channels, cutting out the hydrogen flow entirely. Nickel back support were thus added where the gasket had to go over the flow channels. Also, appropriate margin between the gasket holes and any flow field feature (flow channels, port holes, etc.) were needed has the gasket expands under compression. To spot where to add more margin, we looked at the marks left of the rubber after the compression.

The nickel back support were made with 0.1mm x 4mm 99.6% pure nickel strip, which was cut to the desired length. Be sure to use pure nickel as nickel plated steel will rust.

These nickel strips were held in place using a small amount of silicone. For further improvements, some feature in the graphit flow plates should be added to accurately position the back support strips.


## Sealing interface with negative current collector
### Manufacturing process
(...)


## Issues and recomandations
(...)

# Current collectors
(...)
# End Plates
<img width="1053" height="756" alt="{9884F5E0-8846-489C-B124-512537534B9E}" src="https://github.com/user-attachments/assets/7ace09f3-c464-414d-b57c-0e6afd76973f" />

## Material
In order to have a reliable seal and a well distributed compression, the end plates needs to be very stiff. To achieve this while keeping a light weight, the selected material was a 3/8" thick [Flame-Retardant Garolite G-10/FR4 Sheet](https://www.mcmaster.com/85345K752/). Note that this material is very abrasive and might damage the tooling bits. 
## Ports
The selected connector were [Swagelok's #SS-400-1-0256](https://products.swagelok.com/en/c/straights/p/SS-400-1-0256). A 10-32 thread was tapped directly in the garolite sheets.

To keep the fitting tight over time, threadlockr was added and along with a 3D printd contraption that prevent the rotation of the two fitting like a lock wire.

## Compression
To compress the stack, eight M4 threaded rods were used to compress the two end plates together. A nut was also welded on one end of each rod to turn it into a long hex head bolt. Note that washers are needed to avoid damage on the end plates during compression.

# Stack assembly procedure
(...)
## Positioning rods
(...)

# Air blower
(...)
# Performances
## Testing
(...)

# Recommandations
(...)
# Acknowledgement
Huge thanks to all our sponsors and to all the experts who helped us along the way!

<img width="600" alt="github-1" src="https://github.com/user-attachments/assets/7965bfa0-8bd2-4d49-bacf-e9380af09838" />



