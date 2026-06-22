# Source: https://coursify.hasanraiyan.me/research/introduction-to-superconductivity

Introduction to Superconductivity

# 

Introduction to Superconductivity

Verified Sources

Jun 17, 2026

## AI Summary

Superconductivity is one of the most remarkable phenomena in condensed matter physics. Discovered in 1911 by Dutch physicist Heike Kamerlingh Onnes, it refers to the complete disappearance of electrical resistance in certain materials when cooled below a characteristic critical temperature. Beyond zero resistance, superconductors exhibit perfect diamagnetism — a property fundamentally distinct from merely being a "perfect conductor."

These two defining properties — **zero resistance** and the **Meissner effect** — cannot be explained by classical or single-electron quantum theory. Instead, they arise from a collective quantum state in which electrons form Cooper pairs, condensing into a coherent macroscopic quantum wavefunction. This intersection of quantum mechanics and many-body physics makes superconductivity one of the deepest and most technologically significant areas of modern physics.

The implications are far-reaching: from the MRI machines used in hospitals to the quantum computers being developed in research labs, from lossless power transmission to magnetic levitation trains — superconductivity sits at the heart of current and future technology.

## Footnotes

1. [Introductory Chapter: Fundamentals of Superconductivity | IntechOpen](https://www.intechopen.com/chapters/1214245) - Overview of BCS theory, Cooper pair formation, London penetration depth, and phenomenological descriptions of superconductivity. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 

#### The Map of Superconductivity

### 

Key Milestones in Superconductivity

#### Discovery of Superconductivity

1911

Heike Kamerlingh Onnes discovers zero resistance in mercury at 4.2 K, marking the birth of superconductivity research."

#### Meissner Effect Discovered

1933

Walther Meissner and Robert Ochsenfeld discover perfect diamagnetism — magnetic flux expulsion is an independent property, not just a consequence of zero resistance."

#### London Equations

1935

Fritz and Heinz London develop the phenomenological London equations, describing the electrodynamic response of superconductors and introducing the London penetration depth."

#### Ginzburg-Landau Theory

1950

Vitalii Ginzburg and Lev Landau publish their phenomenological theory using a complex order parameter, later enabling the distinction between Type I and Type II superconductors."

#### BCS Theory

1957

John Bardeen, Leon Cooper, and Robert Schrieffer develop the microscopic theory of superconductivity, explaining Cooper pair formation and the energy gap. They win the 1972 Nobel Prize."

#### Josephson Effect

1962

Brian Josephson predicts that Cooper pairs can tunnel through a thin insulating barrier — the Josephson effect — foundational for SQUIDs and superconducting qubits."

#### High-Tc Cuprates Discovered

1986

J. Georg Bednorz and K. Alex Müller discover superconductivity in lanthanum barium copper oxide at 35 K, launching the era of high-temperature superconductivity. Nobel Prize in 1987."

#### MgB₂ Discovered

2001

Akimitsu's group discovers superconductivity in magnesium diboride at 39 K — the highest Tc for a conventional (phonon-mediated) superconductor at ambient pressure."

#### Iron-Based Superconductors

2008

Hosono's group discovers superconductivity in LaFeAsO at 26 K, opening a new class of unconventional superconductors with Tc values reaching 56 K."

#### Hydride Breakthroughs

2025

Pressure-quench techniques push Hg-1223 cuprate superconductor behavior to 151 K at ambient pressure — the highest confirmed Tc at atmospheric pressure."

### The Two Defining Properties

A material is classified as a superconductor if and only if it exhibits both of the following properties below its TcT\_cTc​:

**1\. Zero Electrical Resistance:** Below TcT\_cTc​, the DC resistivity drops to exactly zero — not merely a very small value, but identically zero. A current established in a superconducting loop will persist indefinitely without decay, as confirmed by experiments running for years with no measurable attenuation.

**2\. The Meissner Effect:** When a superconductor is cooled below TcT\_cTc​ in the presence of a weak magnetic field, it expels all magnetic flux from its interior. This is **perfect diamagnetism**: B⃗\=0\\vec{B} = 0B\=0 inside the bulk. The magnetic susceptibility is χ\=−1/(4π)\\chi = -1/(4\\pi)χ\=−1/(4π) (in CGS), the maximum possible diamagnetic response.

The Meissner effect is **not** a consequence of zero resistance. In an ideal (zero-resistance) conductor, Faraday's law would freeze whatever magnetic flux was present when the resistance vanished. A superconductor, by contrast, actively expels flux regardless of the cooling path. This distinction is fundamental: the Meissner effect reflects the **thermodynamic** nature of the superconducting state, not a mere kinetic property.

The external magnetic field does not cease abruptly at the surface. It penetrates a thin surface layer of characteristic thickness λL\\lambda\_LλL​ (the London penetration depth), decaying as:

B(x)\=B0 e−x/λLB(x) = B\_0 \\, e^{-x/\\lambda\_L}B(x)\=B0​e−x/λL​

where λL\\lambda\_LλL​ is given by:

λL\=mμ0nse2\\lambda\_L = \\sqrt{\\frac{m}{\\mu\_0 n\_s e^2}}λL​\=μ0​ns​e2m​​

with nsn\_sns​ the density of superconducting electrons, mmm the electron mass, and eee the electron charge.

## Footnotes

1. [Introductory Chapter: Fundamentals of Superconductivity | IntechOpen](https://www.intechopen.com/chapters/1214245) - Overview of BCS theory, Cooper pair formation, London penetration depth, and phenomenological descriptions of superconductivity. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [Superconductivity and BCS Theory - Rutgers University](https://www.physics.rutgers.edu/grad/621/lectures/L19_SC.pdf) - Lecture notes covering London equations, Meissner effect derivation, and the exponential decay of magnetic fields inside superconductors. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-2-2)
 
3. [Introduction to Superconductivity - Cambridge University Press](https://assets.cambridge.org/97810092/18597/excerpt/9781009218597_excerpt.pdf) - Excerpt explaining the fundamental distinction between the Meissner effect and perfect conductivity, and the independence of these two defining properties. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 

#### Zero Resistance ≠ Superconductor

An ideal conductor and a superconductor behave differently in a magnetic field. An ideal conductor **traps** whatever flux was present when resistance vanished (Faraday's law). A superconductor **expels** flux (Meissner effect). The Meissner effect is an independent, thermodynamic property — proving that superconductivity is a true phase transition, not just a limiting case of perfect conductivity.

more...

### The BCS Theory: Microscopic Understanding

For 46 years after the discovery of superconductivity, the microscopic mechanism remained elusive — Einstein, Bohr, Heisenberg, and Feynman all attempted and failed to develop a complete theory. The breakthrough came in 1957 with the Bardeen–Cooper–Schrieffer (BCS) theory, which earned its authors the 1972 Nobel Prize in Physics.

The BCS mechanism proceeds in three conceptual steps:

**Step 1 — Phonon-Mediated Attraction:** In a normal metal, electrons repel each other via the Coulomb interaction. However, an electron moving through the crystal lattice distorts the nearby ion cores, creating a region of enhanced positive charge. This phonon-mediated polarization attracts a second electron. The net result: an effective **attractive** interaction between two electrons, mediated by virtual phonons.

**Step 2 — Cooper Pair Formation:** Leon Cooper showed in 1956 that any arbitrarily weak attractive interaction between electrons near the Fermi surface leads to a bound state. Two electrons with opposite momenta (k⃗\\vec{k}k and −k⃗\-\\vec{k}−k) and opposite spins (↑\\uparrow↑ and ↓\\downarrow↓) form a Cooper pair with total momentum zero. This pair behaves as a composite boson, since it has spin 0 or 1, and is not subject to the Pauli exclusion principle for fermions.

**Step 3 — Condensation:** All Cooper pairs condense into a single, coherent macroscopic quantum state described by a single wavefunction:

Ψ(r⃗)\=∣Ψ0∣ eiϕ(r⃗)\\Psi(\\vec{r}) = |\\Psi\_0| \\, e^{i\\phi(\\vec{r})}Ψ(r)\=∣Ψ0​∣eiϕ(r)

The energy cost of scattering a Cooper pair requires breaking it apart, which needs an energy ≥2Δ\\geq 2\\Delta≥2Δ (the superconducting energy gap). At temperatures well below TcT\_cTc​, thermal energy kBT≪2Δk\_B T \\ll 2\\DeltakB​T≪2Δ, making scattering extremely unlikely — hence **zero resistance**.

The BCS theory also predicts:

- An energy gap that varies with temperature as Δ(T)≈Δ0(1−(T/Tc)2)1/2\\Delta(T) \\approx \\Delta\_0 \\left(1 - (T/T\_c)^2\\right)^{1/2}Δ(T)≈Δ0​(1−(T/Tc​)2)1/2 near TcT\_cTc​
- A critical temperature: kBTc≈1.13 ℏωD e−1/N(0)Vk\_B T\_c \\approx 1.13 \\, \\hbar\\omega\_D \\, e^{-1/N(0)V}kB​Tc​≈1.13ℏωD​e−1/N(0)V
- The isotope effect, confirming phonon mediation: Tc∝M−1/2T\_c \\propto M^{-1/2}Tc​∝M−1/2

## Footnotes

1. [Introductory Chapter: Fundamentals of Superconductivity | IntechOpen](https://www.intechopen.com/chapters/1214245) - Overview of BCS theory, Cooper pair formation, London penetration depth, and phenomenological descriptions of superconductivity. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-1-2)
 
2. [Cooper pair - Wikipedia](https://en.wikipedia.org/wiki/Cooper_pair) - Description of Cooper pair formation, phonon-mediated attraction, and the role of Bardeen-Pines interaction in conventional superconductivity. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
3. [What Are Cooper Pairs? - AZoQuantum](https://www.azoquantum.com/Article.aspx?ArticleID=664) - Detailed explanation of phonon-mediated pairing, the isotope effect, and unconventional pairing mechanisms in cuprates and iron-based superconductors. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

### How Cooper Pairs Form and Enable Superconductivity

1. 1
 
 Step 1
 
 Electron Traverses the Lattice
 
 A conduction electron (e⁻₁) moving through the crystal lattice polarizes nearby positive ions, displacing them slightly toward its path. This creates a localized region of enhanced positive charge density — a virtual phonon.
 
2. 2
 
 Step 2
 
 Second Electron is Attracted
 
 A second electron (e⁻₂) is attracted to the region of enhanced positive charge left in the wake of e⁻₁. This indirect, phonon-mediated attraction overcomes the direct Coulomb repulsion at low energies, creating an effective attractive interaction between the two electrons." content: "\`\`\`mermaid graph LR A\["e⁻₁ passes through"\] --> B\["Lattice ions displaced"\] B --> C\["Region of + charge created"\] C --> D\["e⁻₂ attracted"\] D --> E\["Cooper Pair formed"\]
    
3.  3
    
    Step 3
    
    Cooper Pair Formation
    
    The two electrons form a Cooper pair with total momentum zero (k↑ and −k↓) and total spin zero (singlet state). The binding energy is approximately 2Δ≈3.5 kBTc2\\Delta \\approx 3.5 \\, k\_B T\_c2Δ≈3.5kB​Tc​. Despite the weak attraction, Cooper proved _any_ attractive interaction leads to a bound state near the Fermi surface.
    
4.  4
    
    Step 4
    
    Cooperative Condensation
    
    Not just one pair, but _all_ pairs of electrons within an energy shell of width ℏωD\\hbar\\omega\_DℏωD​ around the Fermi energy participate. They condense into a single coherent quantum ground state — a macroscopic wavefunction Ψ\=∣Ψ0∣eiϕ\\Psi = |\\Psi\_0| e^{i\\phi}Ψ\=∣Ψ0​∣eiϕ — with a well-defined phase across the entire superconductor.
    
5.  5
    
    Step 5
    
    Energy Gap Protects the State
    
    The condensate opens an energy gap 2Δ2\\Delta2Δ in the excitation spectrum. To scatter an electron out of the condensate, one must supply at least 2Δ2\\Delta2Δ of energy per pair. At low temperatures (kBT≪2Δk\_B T \\ll 2\\DeltakB​T≪2Δ), thermal fluctuations cannot provide this energy — scattering is suppressed and resistance vanishes entirely.
    

### Type I vs. Type II Superconductors

Superconductors are classified by their magnetic response into two principal types, determined largely by the ratio of the London penetration depth λL\\lambda\_LλL​ to the coherence length ξ\\xiξ:

κ\=λLξ\\kappa = \\frac{\\lambda\_L}{\\xi}κ\=ξλL​​

| Property | Type I | Type II |
| --- | --- | --- |
| **κ\\kappaκ value** | κ<1/2\\kappa < 1/\\sqrt{2}κ<1/2​ | κ\>1/2\\kappa > 1/\\sqrt{2}κ\>1/2​ |
| **Critical fields** | Single: HcH\_cHc​ | Two: Hc1H\_{c1}Hc1​ and Hc2H\_{c2}Hc2​ |
| **Magnetic behavior** | Complete Meissner effect up to HcH\_cHc​ | Meissner state → Mixed (vortex) state → Normal state |
| **Transition** | Abrupt at HcH\_cHc​ | Gradual from Hc1H\_{c1}Hc1​ to Hc2H\_{c2}Hc2​ |
| **Materials** | Pure metals (Hg, Pb, Al, Sn) | Alloys and compounds (NbTi, Nb₃Sn, cuprates) |
| **Typical TcT\_cTc​** | Low (< 10 K) | Higher (up to 134 K at ambient pressure) |
| **Practical use** | Limited (low HcH\_cHc​) | Extensive (MRI, accelerator magnets) |

In Type II superconductors, between Hc1H\_{c1}Hc1​ and Hc2H\_{c2}Hc2​, magnetic flux penetrates as **quantized vortices** (each carrying a flux quantum Φ0\=h/2e≈2.07×10−15\\Phi\_0 = h/2e \\approx 2.07 \\times 10^{-15}Φ0​\=h/2e≈2.07×10−15 Wb), forming the Abrikosov vortex lattice. This mixed state allows Type II materials to carry much higher currents and withstand much higher fields than Type I — making them the backbone of all practical superconducting applications.

## Footnotes

1.  [Basic Principles and Type I vs Type II Superconductors - WJARR](https://wjarr.com/sites/default/files/fulltext_pdf/WJARR-2022-0050.pdf) - Comprehensive comparison of Type I and Type II superconductors including magnetic behavior, critical fields, material properties, and applications. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-6) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-6-2)
    

#### Why Gold, Silver, and Copper Never Superconduct

The best room-temperature conductors — gold, silver, and copper — do not become superconducting at any temperature (at ambient pressure). Why? They have the smallest lattice vibrations (stiff lattices), which means very weak electron-phonon coupling. Since Cooper pairs in conventional superconductors require phonon-mediated attraction, these materials cannot form the needed bound state. This is fully consistent with BCS theory: weak phonon coupling ⟹ no pairing ⟹ no superconductivity.

more...

### 

Critical Temperatures of Selected Superconductors

Comparison of Tc values for important superconducting materials (at ambient or specified pressure)

### High-Temperature Superconductors

The discovery of high-temperature superconductors (HTS) in 1986 by Bednorz and Müller was a transformative moment. Their observation of superconductivity at 35 K in LaBaCuO shattered the perceived BCS limit and opened an entirely new research frontier. Within a year, YBCO pushed TcT\_cTc​ to 92 K — above the boiling point of liquid nitrogen (77 K) — enabling practical cooling without liquid helium.

Key HTS material families include:

-   **Cuprates** (copper-oxide-based): YBCO (Tc\=92T\_c = 92Tc​\=92 K), BSCCO (Tc\=110T\_c = 110Tc​\=110 K), Hg-1223 (Tc\=134T\_c = 134Tc​\=134 K at ambient pressure — the current record at atmospheric pressure)
-   **Iron-based superconductors** (discovered 2008): TcT\_cTc​ up to 55 K in SmFeAsO, with different pairing symmetry from cuprates

Crucially, the pairing mechanism in HTS materials is **not** fully understood. Unlike conventional superconductors where phonon mediation is established, HTS likely involves spin fluctuations or other strongly correlated electronic effects. This remains one of the greatest unsolved problems in condensed matter physics.

## Footnotes

1.  [Intro to High-Temperature Superconductors - National MagLab](https://nationalmaglab.org/magnet-academy/read-science-stories/science-simplified/high-temperature-superconductors) - Primer on cuprate, BSCCO, REBCO/YBCO, and MgB₂ high-temperature superconducting materials and their development. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-7-2)
    
2.  [A New Road Map to Room Temperature Superconductors - UC Davis](https://www.ucdavis.edu/egghead/blog/new-road-map-room-temperature-superconductors) - Discussion of the 133 K ambient-pressure record for Hg-1223, pressure quenching techniques, and computational approaches to discovering new superconductors. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-8)
    

MRI / Medical Imaging

Quantum ComputingPower TransmissionMaglev TransportationParticle Accelerators

Superconducting magnets (typically NbTi at 4.2 K) generate the strong, stable magnetic fields (1.5–7 T) required for MRI. Superconducting MRI offers higher field strengths, improved signal-to-noise ratio, faster scan times, and better diagnostic accuracy compared to resistive magnets. YBCO-based HTS magnets are being developed for next-generation, lower-cost systems.

### Current Frontiers and the Quest for Room-Temperature Superconductivity

The holy grail of superconductivity research is a material that exhibits zero resistance at or near room temperature and ambient pressure. While no such material has been conclusively demonstrated, the pursuit has accelerated with several notable developments:

-   **Hydride superconductors:** Under extreme pressures (millions of atmospheres), hydrogen-rich compounds like H₃S and LaH₁₀ have shown superconductivity at temperatures up to ~250 K. However, the required pressures make them impractical.
-   **Pressure quenching:** In 2025, researchers at the University of Houston and Argonne National Laboratory demonstrated that Hg-1223 cuprate, compressed at ~300,000 atmospheres and then rapidly depressurized, retained superconducting signatures up to 151 K at ambient pressure — an 18-degree improvement sustained for up to two weeks.
-   **Computational discovery:** Researchers advocate for using machine learning and _ab initio_ modeling to systematically search for stable, high-TcT\_cTc​ materials — moving beyond the Edisonian trial-and-error approach.

There are **no known physical laws** that forbid room-temperature superconductivity. The challenge is finding the right combination of material properties: high-frequency lattice modes, strong electron-phonon coupling, and high density of states at the Fermi level.

## Footnotes

1.  [A New Road Map to Room Temperature Superconductors - UC Davis](https://www.ucdavis.edu/egghead/blog/new-road-map-room-temperature-superconductors) - Discussion of the 133 K ambient-pressure record for Hg-1223, pressure quenching techniques, and computational approaches to discovering new superconductors. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-8)
    
2.  [Physicists break longstanding high-temperature superconductivity record - Phys.org](https://phys.org/news/2026-03-ceramic-shatters-longstanding-high-temperature.html) - Report on pressure-quench experiments raising Hg-1223 superconducting behavior to 151 K at ambient pressure. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-9) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-9-2)
    

#### The LK-99 Controversy

In July 2023, a Korean team claimed the discovery of LK-99, a purported room-temperature, ambient-pressure superconductor. The claim went viral but was rapidly debunked by multiple independent groups, who showed the observed levitation was due to ferromagnetic impurities (Cu₂S), not the Meissner effect. This episode highlights the importance of rigorous peer review and reproducibility in superconductivity claims.

more...

### Frequently Asked Questions

Why is the Meissner effect not just a consequence of zero resistance?

What is flux quantization and why does it matter?

Can the BCS theory explain high-temperature superconductors?

What makes NbTi so widely used in practical superconducting magnets?

### Knowledge Check

Question 1 of 5

Q1Single choice

What are the two defining properties of a superconductor that distinguish it from an ideal (infinite-conductivity) conductor?

Zero resistance and negative magnetoresistance

Zero resistance and the Meissner effect (perfect diamagnetism)

The Meissner effect and high thermal conductivity

Zero resistance and the isotope effect

BackNext

## Explore Related Topics

[1\\ \\ NumPy for Beginners: A Comprehensive Introduction\\ \\ NumPy supplies fast, multi‑dimensional arrays and tools for creation, indexing, broadcasting, and linear algebra.\\ \\ -   An `ndarray` holds homogeneous data; key attributes are `ndim`, `shape`, `size` (∏shapei\\prod\\text{shape}\_i∏shapei​) and `dtype`. -   `np.array`, `np.zeros`, `np.arange`, `np.linspace`, and random functions create arrays, optionally specifying `dtype`. -   Basic slicing returns a view, while boolean or fancy indexing returns a copy; use `.copy()` when needed. -   Broadcasting stretches dimensions of size 1: `Result shape_i = max(A_i,B_i)`, allowing element‑wise ops without data duplication. -   NumPy’s ufuncs, aggregation (`sum`, `mean`) and `np.linalg` (dot, inverse, eig) run on optimized BLAS/LAPACK.](https://coursify.hasanraiyan.me/research/numpy-for-beginners-a-comprehensive-introduction) [2\\ \\ Understanding Belady's Anomaly in Operating Systems\\ \\ Belady's Anomaly shows that, for some page‑replacement policies, adding more physical frames can **increase** the number of page faults.\\ \\ - FIFO (a non‑stack algorithm) does not satisfy the inclusion property and can exhibit the anomaly. - On the reference string 1,2,3,4,1,2,5,1,2,3,4,51,2,3,4,1,2,5,1,2,3,4,51,2,3,4,1,2,5,1,2,3,4,5, FIFO yields 999 faults with 333 frames but 101010 faults with 444 frames. - Stack algorithms such as LRU or Optimal obey M(N,t)⊆M(N+1,t)M(N,t)\\subseteq M(N+1,t)M(N,t)⊆M(N+1,t), guaranteeing that more frames never raise fault counts. - Designing a virtual‑memory system with stack‑based replacement eliminates Belady's Anomaly.](https://coursify.hasanraiyan.me/research/understanding-beladys-anomaly-in-operating-systems)

[![Coursify logo](https://coursify.hasanraiyan.me/_next/image?url=%2Fimages%2Fapps%2Fcoursify.png&w=48&q=75)Browse all research articles](https://coursify.hasanraiyan.me/research)