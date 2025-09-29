# ALÉR-ION open source hydrogen fuel cell
*Note: The full documentation for this project is in progress. Sections marked with "(...)" will be updated in a near future. Feel free to contact me at mederic.chalifour.1@ulaval.ca for any question.*

Alérion Supermilage is a student group at l'Université Laval who focusses on the developpement of high efficiency vehicles for various competitions. Up until 2024, the team always relied on an internal combustion engines. They then transitioned toward an electric-driven system with a battery.

In 2025, the project of a self-made hydrogen PEM fuel cell was born. With the spirit of sharing knowledge and helping others develop this technology, all the relevant design files are release as an open-source project.

This is a PEM open cathode fuel cell which turns pure (or prehumidified) hydrogen gas into electrical power.

**DISCLAIMER: At the moment of writing this, the prototype still has reliability issues. This stack is prone to leaking. Alérion Supermileage waives any responsability related to the usage of this fuel cell design. Note that hydrogen is a flammable gas. Use these files at your own risks.**

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

  (Image)

  The simple serpentine flow field was selected.

  (Image)
    ### Air side (cathode)
  All cathode flow fields that were tried followed the same idea of straight channels. The selection process was done before the optimisation of the gasket system. Indeed, nickel strips were added as back support for the gasket. The initial design was thus on that allowed the first PTFE gasket to self support and wasn't necessarely the most efficient one.

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
(...)
## Main gasket
### Manufacturing process
(...)
## Subgasket
### Manufacturing process
(...)
## Sealing interface with negative current collector
### Manufacturing process
(...)
## Testing procedure
(...)
### Electrical contact
(...)
### Leak test
(...)
### Membrane integrity
(...)

## Issues and recomandations
(...)

# Current collectors
(...)
# End Plates
## Material
(...)
## Ports
(...)
## Compression
(...)

# Stack assembly procedure
(...)
## Positioning rods
(...)

# Air blower
(...)
# Performances
(...)

# Recommandations
(...)
# Acknowledgement
Huge thanks to all sponsors and to all the expert help without whom this project wouldn't have been possible.
