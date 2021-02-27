# Week 3

**Textbook Sections:** 2.8-2.10 (through page 58), 2.11, 2.12

### 2.9 Intercellular Communication and Signal Transduction (51-53)

##### Communication between cells
1. Gap junctions 
2. Surface identifying markers (glycoproteins and glycolipids) permit transient link-up communication (ie. avoiding unintentional phagocytosis)
3. Extracellular chemical messengers
	1. **Paracrines**: local chemical messengers restricted to short distance signalling. Ex. histamine. These must be distiguished from chemicals being released during regular cellular activity like CO2. 
	2. **Neurotransmitters**: the means by which neurons communicate with one another and the cells that they innervate. 
	3. **Hormones**: long range chemical messengers in the blood. 
	4. **Neurohormones**: hormones secreted into the blood by **neurosecretory neurons** such as the adrenal medual (modified sympathetic ganglion that secretes NE and E into the blood). 

**Signal transduction** (the process of incoming signals being conveyed to the interior) happens in two ways:
1. opening or closing channels (**chemically gated channels**)
2. second-messenger systems 

### 2.10 Membrane Potential (53-59)

**Membrane potential**  measures the potential of the ICF with respect to the ECF (usually in mV). $RMP = V_{inside} - V_{outside}$

The **resting membrane potential** for excitable human cells is usually around $-70 \; mV$. This means the inner leaflet is more negative than the outer leaflet. RMP varies between cell types:

![[Pasted image 20210227075414.png]]

Each ion tends to drive membrane potential towards it's equillibrium potential, determined the by the **Nernst Equation:**
$$E = \frac{RT}{zF}\ln{\frac{C_{out}}{C_{in}}} = (61\;mV)\log{\frac{C_{out}}{C_{in}}} $$

where $R = 8.314 \; Jmol^{-1}K^{-1}$, $F = 96485.33212 \; Cmol^{-1}$, $T$ is the temperature in K, and $z$ is the valance of the ion. The second equation is for room temperature ions with +1 charge. 

The degree to which the total membrane potential tends towards each individal ion's equillibrium potential depends on the permeability of the membrane to that ion. 

|Ion|$C_{out}$|$C_{In}$|Relative Permeability At Rest| $E \; (mV)$
|---|---|---|---|--|
|Na+| 150 | 15 | 1|61|
|K+| 5 | 150| 50-75|-90|
|A- (generic anions)|0 | 65 | 0|
|Cl-||||-70

##### Potassium:
- has a concentration gradient from ICT->ECF
- will move out of leak channels and leave anions behind, generating electrial gradient from ECF -> ICF (net negative on the inside)
- This will occur unti the two gradients balance
- increased extracellular potassium would decrease the concentration gradient and decrease the magnitude of the equillibrium potential
- increased intracellular potassion would do the reverse. 

##### Sodium
- has a concentration gradient from ECF->ICF
- will move into cell through channels leaving A- behind, generating electrial gradient from ICF->ECF (net negative on the inside)
- This will occur unti the two gradients balance

##### Chloride
- $E = RMP$ because the membrane is highly permeable to Cl-. 

**Depolarization:** MP becomes less negative.
**Hyperpolarization:** MP becomes more negative than RMP
**Repolarization**: MP becomes more negative, moving towards RMP. 

**Types of gated channels**
1. mechanicaly
2. voltage (VG)
3. chemically
4. thermally

### 2.11 Graded Potentials (59-61)

**Triggering events:** usually chemically gated opening of ion channels. Opening Na+ gates will be excitatory. Opening general cation gates will be excitatory because the electrochemical gradient for Na+ is more strong than it is for K+ at RMP. **The magnitude of the triggering event** affects the number of channels that open and thus the magnitude of the graded potential. 

**Inflow of Na+** causes a local current flow. The positive charges will flow from the active area to inactive areas along the membrane on the ICF side. On the ECF side, positive charges will flow into the the recently vacated areas. Depolarization spreads from the active area along the membrane in a **decremental** fashion. 

**Current loss** occurs due to lack of insulation (ion leak channels) and resistance, resulting in **decremental conduction** of graded potentials. 

### 2.12 Action Potentials (61-71)

**VG Na+ Channels:** consist of 2 gates: activation and inactivation gate (ball and chain). Can be in one of three states:
1. closed and ready to open
2. closed and unable to open (inactivation gate is closed)
3. Open

**VG K+ Channels:** have similar states to VG Na+ channels but consist of four protein subunits instead of the activation and inactivation gates. 

##### Steps of an action potential

1. At RMP of $-70 \; mV$, the VG Na+ and VG K+ gates are both in the "closed but ready to open" position. Leak channels enforce the relative permeability of the membrane to the ions, and the Na-K pump establishes the concentrations gradients (3 Na out, 2 K in), resulting the the RMP. 
2. A graded potential brings the MP to the threshold value of around $-50 \; mV$$. The VG Na+ activation gates open quickly, and the inactivation gates begin their slow (delayed) closing process (which will close at the peak of the AP). A delayed voltage response to threshold is also initated in the VG K+ pump, which will start to slowly open at the peak of the AP. 
3. When threshold is reached, the permeabilty of the membrane to Na+ ($P_{Na+}$) skyrockets in a positive feedback loop (Na+ in raises voltage which causes more Na+ channels to open). $P_{Na+} \sim 600P_{K+}$. **Na+ influx**
4. This causes a reversal in membrane potential, and the AP peaks at +30 mV. At the peak, the slow closing inactivation gate on the VG Na+ channels closes, and slow opening VG K+ gates are now open. This causes $P_{K+} \sim 300 P_{Na+}$, **K+ efflux** and the membrane potential moves back towards the equillibrium potential for K+. 
5. As repolarization is occuring, the VG Na+ gates begin to return to their "closed but capable of opening" state. The VG K+ channels are slow to close, resulting in a period where MP < RMP known as **after hyperpolarization**. 
6. The Na-K ATPase pump will restore the concentration gradients of K+ and Na+ after an action potential (although a single AP transfers only a few ions). 

The **refractory period** prevents backwards conduction of the AP. 
1. the **absolute refractory period** occurs from **VG Na+ opening** until they restore their **closed but ready to open** position. This is roughly from when threshold is first reached to the start of after hyperpolarization. No matter the stimulus strength, another AP cannot be generated during this period
2. the **relative refractory period** occurs due to a **lingering inactivation of some VG Na+ gates** and the **slow closing of the VG K+ gates**. Fewer than normal VG Na+ gates are ready to initate a new AP, and a **larger stimulus is required** to reach threshold due to some continual K+ efflux causing hyperpolarization. If an AP is initiated, **it may have a lower peak due to less available VG Na+ gates**. 

APs are conducted in an **all or none, nondecremental** fashion. Morover, the **strength of a stimulus is encoded in the frequency of an action potential**. There are two main types of AP conduction: 

##### Types of conduction 

1. **Contiguous conduction**: the continual regeneration of AP along a neuronal membrane. The active area (depolarization) causes local current flow, and theshold to be reach in an adjacent inactive area, generating a new AP. APs don't travel, the initiate neighbouring APs. While the new neighbouring AP ir happening, the other portion of the membrane is in its refractory period, so backwards conduction cannot occur.  
2. **Saltatory conduction:** the axons of some neurons are myelinated (by glial cells: **oligodendrocytes in the CNS** and **schwann cells in the PNS**). **Myelin** is composed of lipids (80%) and proteins (20%), so it cannot be penetrated by water soluble ions like Na+ and K+. In between the sections of myelin lie the **nodes of ranvier**, where the axonal membrane is exposed to the ECF and which house many voltage gated channels. The distance between the nodes of ranvier ($\sim 1 \; mm$) is short enough that an action potential can be conduced by local current flow from one node to the next, without having to regenerate an action potential in a directly adjacent portion of the cell membrane. At each node, a new AP is generated. This is called **saltatory conduction** because the APs jump from one node to the next. 

**Saltatory conduction** is about 50 times faster than **contiguous conduction**. Some other factors that affect conduction speed are:
1. Axonal diameter (larger is faster)
2. membrane resistance (to ion leakage). High resisance to ion leakage => higher insulation => faster conduction.  
3. membrane capacitance 

##### Neuron Anatomy
1. **Dendrites:** input zone projections where graded potentials are generated.
2. **Cell body/soma**.
3. **Axon hillock:** trigger zone with high concentration of VG Na+ gates
4. **Axon:** conducting zone.
5. **Axon Terminals:** release a neurotransmitter to their target cell. 

Some other terminology:
- **Dendridic spines:** membrane protrusions from a dendrite.
- **Sprouting:** intial development of a new dendridic branch.
- **Arborization:** large proliferation of branches (**dendridic arborization** or **axonal arborization**).
- **Collateral branches:** axon branches -> more synapses. 
- **Synaptogensis:** creation of new synapses.
- **Neurotrophin:** nerve growth factor NGF, brain derivaed nerve neurotrophic factor BDNF and neurotropin 3 and neurotropin 4. 
- **Synaptic pruning:** only the synaptic connections that are used are maintained. **Synaptic formation** and **apoptosis** play a role in this. 

##### From week 3 case study:
- inhibited Na-K ATPase pump (digoxin toxin)-> higher extracellular K+ and higher intracellular Na+ -> less negative K+ equillibrium potential -> depolarized RMP -> closer to reaching threshold -> seizures 
- T3 hormons stimulates Na-K ATPase activity -> increases concentration gradient for K+ -> hyperpolarization of RMP -> harder to reach threshold -> paralysis