# 18.369(J)/8.315(J): Mathematical Methods in Nanophotonics

This is the repository of course materials for the [18.369(J)/8.315(J)](http://student.mit.edu/catalog/m18a.html#18.369) course at MIT, taught by Prof. [Steven G. Johnson](http://math.mit.edu/~stevenj/), in Spring 2020.  (This course is offered once every two years.)

Syllabus
--------

> **Tired of doing electromagnetism like it's 1865?**
>
> _Find out what solid-state physics has brought to [8.02](https://ocw.mit.edu/courses/physics/8-02-physics-ii-electricity-and-magnetism-spring-2007/) in the last 20 years, in this new course surveying the physics and mathematics of nanophotonics—electromagnetic waves in **media structured on the scale of the wavelength**._
>
> _In this regime, which is the basis for everything from iridescent butterfly wings to distributed-feedback lasers and integrated optical devices to the next generation of optical fibers, the 140–year-old analytical techniques you learned in 8.02 aren't as useful. Instead, we will cover computational methods combined with high-level algebraic techniques borrowed from solid-state quantum mechanics: linear algebra and eigensystems, group theory, Bloch's theorem and conservation laws, perturbation methods, and coupled-mode theories, to understand surprising optical phenomena from band gaps to slow light to nonlinear filters._
>
> For beginning graduate students and advanced undergraduates.


**Lectures**: Tues-Thurs 11am–12:30pm (4-153). **Office Hours:** Tues. 4–5pm (2-345). TA/grader: [Chenyang Shao](http://math.mit.edu/directory/profile.php?pid=2035).   [Handwritten notes](https://www.dropbox.com/s/1c3l54mf3rh8qw3/18.369%20spring%202020.pdf?dl=0).

**Probable topics**: _Methods_: linear algebra & eigensystems for Maxwell's equations, symmetry groups and representation theory, Bloch's theorem, numerical eigensolver methods, time and frequency-domain computation, perturbation theory, coupled-mode theories, waveguide theory, adiabatic transitions. _Optical phenomena_: photonic crystals & band gaps, anomalous diffraction, mechanisms for optical confinement, optical fibers (new & old), nonlinearities, integrated optical devices.

**Grading**: 33% problem sets (weekly/biweekly). 33% take-home mid-term exam (Posted **April 20**, due **April 21**.). 34% final project (proposal due April 14, project due May 12).

* Psets will be [submitted electronically via Stellar](https://learning-modules.mit.edu/gradebook/index.html?uuid=/course/18/sp20/18.369).  Submit a good-quality PDF *scan* of any handwritten solutions (or a PDF printout of computer output).

**Collaboration policy**: Talk to anyone you want to and read anything you want to, with three exceptions: First, you **may not refer to homework solutions from the previous terms** in which I taught 18.369. Second, make a solid effort to solve a problem on your own before discussing it with classmates or googling. Third, no matter whom you talk to or what you read, write up the solution on your own, without having their answer in front of you.

**Books**: [Photonic Crystals: Molding the Flow of Light (Second Edition)](http://ab-initio.mit.edu/book) (**readable online**). (This book is at an undergraduate level and 18.369/8.315 is somewhat more advanced, but the book should provide a useful foundation.)

Useful (but not required) books (available in the library): [Group Theory and Its Applications in Physics](http://link.springer.com/book/10.1007/978-3-642-80021-4) by Inui et al. ([readable online](http://link.springer.com/book/10.1007/978-3-642-80021-4) via MIT), and _Group Theory and Quantum Mechanics_ by Michael Tinkham.

**Final projects:** A typical project will be to find some interesting nanophotonic structure/phenomenon in the literature (chapter 10 of the book may be a helpful guide to some possibilities), reproduce it (usually in 2d only, so that the simulations are quick), using (e.g.) the numerical software ([Meep](https://github.com/stevengj/meep) and/or [MPB](https://github.com/stevengj/mpb)) introduced in the course/psets (other useful free/open-source software: [SCUFF-EM](http://homerreid.dyndns.org/scuff-em/) and [S4](https://web.stanford.edu/group/fan/S4/)), and extend/analyze it in some further way (try some other variation on the geometry, etc.). Then write up the results in a 7-15 page report (in the format of a journal article, ideally [Phys. Rev. A](http://pra.aps.org) style, including figures, a comprehensive review of related work, etcetera)—reports should be written for a target audience of your classmates in 18.369/8.315, and should explain what you are doing at that level. Projects should _not_ be a rehash of work you've already done in previous terms for your research (but may be some extension/digression thereof).

**Prerequisites**: 18.303, 8.07, or permission of instructor. (Basically, some experience with partial differential equations and linear algebra. e.g. 8.05, 8.07, 6.013, 3.21, 2.062 are all good background.) This is a graduate-level course aimed at beginning graduate students and suitably advanced undergraduates.

Supplementary lecture notes will be made available as the term progresses.

Lecture Summaries and Handouts
------------------------------

### Lecture 1: 4 Feb 2020

**Handouts:** syllabus (this web page), [introductory slides](notes/18.369-intro.pdf), [pset 1](psets/pset1.pdf) (due Thur Feb 13).

Motivation and introduction: this class is about electromagnetism where the wavelength is neither very large (quasi-static) nor very small (ray optics), and the analytical and computational methods we can use to understand phenomena in materials that are structured on the wavelength scale. In that situation, there are very few cases that can be solved analytically, but lots of interesting phenomena that we can derive from the _structure_ of the equations.

We start by setting up the source-free Maxwell equations as a linear eigenproblem, which will allow us to bring all of the machinery of linear algebra and (eventually) group theory to bear on this problem without having to solve the PDE explicitly (which is usually impossible to do analytically).

Notational introductions: Hilbert spaces (vector space + inner product), notation for inner products and states (magnetic fields etc.). Defined the adjoint (denoted †) of linear operators and Hermitian operators (Â=Â†).

Showed that the Maxwell eigen-operator ∇×ε⁻¹∇× is Hermitian for real ε (by showing that ∇× is Hermitian). The Maxwell operator is also positive semidefinite for ε>0, and it follows that the eigenfrequencies are real.

**Further reading:** See chapter 2 of the _Photonic Crystals_ textbook for Maxwell's equations as an eigenproblem etc. For a more sophisticated treatment of Hilbert spaces, adjoints, and other topics in functional analysis, a good text is _Basic Classes of Linear Operators_ by Gohberg et al. The basics of electromagnetism in macroscopic media (ε and μ) are covered in any non-freshman electromagnetism textbook, e.g. _Classical Electrodynamics_ by Jackson or _Introduction to Electromagnetism_ by Griffiths.

### Lecture 2: 6 Feb

**Handouts:** [representation theory summary](notes/representation-theory.pdf)

Simple one-dimensional example of fields in metallic cavity, showed that consequences match predictions from linear algebra.

Discussed consequences of symmetry, and in particular showed that mirror symmetry implies even/odd solutions. Discussed subtleties of mirror symmetries for electromagnetism: although the E and H fields seem to have opposite symmetry, they don't, because H is a pseudovector. Defined general rotation operators _R̂_ for vector and pseudovector fields.

Gave a simple 2d example of fields in a 2d metal box, and showed that the symmetries are more complicated, and may include degeneracies. In order to understand this, we need to understand the relationship of different symmetry operations to one another — this relationship is expressed more precisely by the _group_ of symmetry operators, which we will get to next time.

**Further reading:** Chapter 3 of the photonic-crystals text. See the Inui textbook, or many similar sources, on group theory; the most helpful in this context are the many "group theory in physics" books.

### Lecture 3: 11 Feb

Defined groups, and group representations, irreducibility, and partner functions, conjugacy classes and most of the other things on the handout, with some examples (the square symmetry group and the mirror symmetry group). (Briefly covered everything on the handout _except_ Great Orthogonality Theorem, character tables, projection operators, and product representations.)

Proved that all eigenfunctions can be chosen to transform as partner functions of an irreducible representation of the symmetry group (also called a "basis" of the representation), with the dimension of the representation given by the degree of degeneracy of the eigenvalue. Proved that all representations derived from a given eigenvalue are equivalent. Noted that orthonormal eigenfunctions give a unitary representation (outlined proof but did not work it through).

If the representation is irreducible, then the degeneracy comes from the symmetry of the system. If the representation is reducible, then we call it an **accidental degeneracy** (not coming from symmetry). Accidental degeneracies rarely happen by accident—usually the degeneracy has somehow been forced—so generically we only expect degeneracies if there are >1 dimensional irreps.

Build the simple character table for the {E,σ} mirror-symmetry group, reprising the previous result that in mirror-symmetric systems we expect even/odd eigenfunctions, and we don't expect (non-accidental) degeneracies (unless there are additional symmetries).

**Further reading:** Chapter 3 of the text, but this doesn't get into representation theory. See e.g. _Group Theory and Its Applications in Physics_ by Inui et al. (especially sections 4.1, 6.1, and 6.2) or _Group Theory and Quantum Mechanics_ by Michael Tinkham (especially sections 3-1 and 3-6), or any book with a similar title.  Character tables for all of the common symmetry groups are tabulated in both textbooks and online, e.g. see this [page on the C4v group](http://symmetry.jacobs-university.de/cgi-bin/group.cgi?group=404&option=4). See Inui section 6.6 on projection operators.

### Lecture 4: 13 Feb

**Handout:** [notes on decomposition of functions into partner functions](notes/irrep-decompose.pdf);  [pset 1 solutions](psets/pset1sol.pdf); [pset 2](psets/pset2.pdf) (due Thurs Feb 27).

Using the rules from the representation theory handout, we build up the character table for the symmetry group of the square (called _C_4v). Then, look at the eigenfunction solutions that we previously had for this case, and show how we could classify them into the various irreducible representations.

Looked at the projection operator (see handout) in more detail and gave some graphical examples of how we can use it to decompose a function into partner functions.

Used the projection operator to classify the modes of the square cavity, and in particular found that some of the modes are accidental degeneracies. In this way, we are able to find representatives of all five irreps. Conversely, by looking at the irreps, we can guess some of the types of eigenfunctions that should appear, inferring the sign pattern from the character table.

Showed how we can apply the projection operator to "random" functions to find partners of different irreps, even without an eigenproblem, and to "sketch" the qualitative features that we expect to find in the eigenfunctions. And, once we have partner functions, we can obtain representation matrices for each irrep (useful for 2+ dimensional irreps). As an example, looked at ψ(x,y)=1, x, and x2; found in particular that the 2d irrep transforms like {x,y}, i.e. the ordinary 2d rotation matrices.

Next time, we will show the irreducible representation is conserved over time in a linear system, by showing that the projection operator commutes with the time-evolution operator.

**Further reading:** Character tables for all of the common symmetry groups are tabulated in both textbooks and online, e.g. see this [page on the C4v group](http://symmetry.jacobs-university.de/cgi-bin/group.cgi?group=404&option=4). See Inui section 6.6 on projection operators.

### No class: 18 Feb

This is an "MIT Monday" due to the holiday on the previous day.

### Lecture 5: 20 Feb

Guest lecture, [Prof. Marin Soljačić, MIT Physics](https://www.rle.mit.edu/marin/): Novel devices and applications in photonics.

### Lecture 6: 25 Feb

**Handout:** [notes on time evolution and conservation laws](notes/time-evolution.pdf)

The irreducible representation is "conserved" over time in a linear system, because the projection operator commutes with the time-evolution operator.

Defined the time-evolution operator explicitly via an exponentiated operator on the 6-component vector-field (**E**, **H**). Showed that the time-evolution operator is unitary in an appropriate inner product, for lossless materials, and that this leads to conservation of energy.

**Further reading:** See my [Notes on the algebraic structure of wave equations](notes/wave-equations.pdf) for a general discussion of many wave equations, showing that they share the common form dψ/dt D ψ where D is anti-Hermitian. For Poynting's theorem, see any graduate-level book on electromagnetism, e.g. Jackson's _Classical Electrodynamics_. The result is summarized in chapter 2 of the textbook. Beware that matters are more complicated for dispersive media (ones in which ε and μ depend on ω), as discussed briefly in Jackson. A much more complete review of passive dispersive media, including the consequences of passivity for causality etcetera, can be found in our 2014 paper [Speed-of-light limitations in passive linear media](http://math.mit.edu/~stevenj/papers/Welters14.pdf): see in particular the discussion of passivity in section II.B and of "dynamical" energy density in section V.A.

### Lecture 7: 27 Feb

* [pset 2 solutions](psets/pset2sol.pdf)
* [pset 3](psets/pset3.pdf) (due Thursday Mar 12).

Finished time-evolution notes from last lecture: dispersive media, passivity, and dissipation.

**Translational symmetry:** Showed that for continuous translational symmetry, the representations are exponential functions exp(ikx) for some real number k (for unitary representations).  In a uniform medium, this gives **planewave** solutions.

Explained how conservation of the exp(-ikx) representation, which gives conservation of k, means that planewaves are produced by a line-current source Jz(x,y)=δ(x) exp[-i(ky-ωt)] in 2d, assuming outgoing (radiation) boundary conditions.

Next time: Conservation of the exp(-ikx) representation, which gives conservation of k, leads immediately to Snell's law at a flat interface.

**Further reading:** Textbook, chapter 3 on continuous translational symmetry.

### Lecture 8: 3 Mar

Introduced **dielectric waveguides**, via the simple 2d example of a high-ε region surrounded by a low-ε region, invariant in the x direction.

A point source (delta-function current) in a dielectric waveguide will generally excite _both_ guided (below the light line) and radiating (above the light line) solutions, and you might be interested in [this animation](https://github.com/mitmath/18303/raw/fall16/waveguide-movies/index-0.5.mp4) of a point source in a dielectric waveguide (ε=4 surrounded by air) (see also the [larger version of the same animation](https://github.com/mitmath/18303/raw/fall16/waveguide-movies/index-0.5-long.mp4)).

Introduced the "reduced" eigenproblem Θ̂ₖ=exp(-ikx)Θ̂exp(ikx) for the modes of a particular wavevector **k**. This is also Hermitian, its solutions ω(k) yield the dispersion relation (or _band structure_) of the problem.   The rotational symmetries are now reduced for Θ̂ₖ to the "little group of *k*", the symmetries that preserve *k*.

Explained how mirror symmetry in _z_ means that _z_-invariant solutions in "2d" structures ε(x,y) can be segregated into two polarizations: even Hz-polarized (what the book calls "TE") and odd Ez-polarized (what the book calls "TM"). (Note that the literature is split on the terminology here: many authors call the former TM and the latter TE.)

By conjugating the eigenequation, for real ε, showed that ω(**k**)=ω(−**k**) in general, even for structures without mirror symmetry. Connected this to time-reversal symmetry: the conjugated mode corresponds to running time backwards, which still solves the same Maxwell's equation. One way to break time-reversal symmetry is by introducing absorption loss (complex ε, which time-reverses into gain). Alternatively, briefly mentioned magneto-optic materials (complex-Hermitian ε, neglecting absorption) and why a static magnetic field can (locally) break time-reversal symmetry, and of use for Faraday isolators.

Continued discussing **dielectric waveguides**, via the simple 2d example of a high-ε region surrounded by a low-ε region, invariant in the x direction. Explained that the solutions far from the waveguide lead to a continuous region, the _light cone_, and argued (proof to come later) that the higher-ε region pulls down localized guided modes below the light cone. Since they are localized, they form discrete bands in order to stay orthogonal.

**Further reading**: See the book, chapter 3, on index guiding and the variational principle. (See e.g. Jackson's _Classical Electrodynamics_ for a more traditional viewpoint on dielectric waveguides, focused on the two cases that can be solved analytically, and Marcuse's _Theory of Dielectric Optical Waveguides_ for an expanded version of this. See e.g. Ramaswami and Sivarajan, _Optical Networks_ for a nice practical overview of dielectric waveguiding in modern telecommunications.)

### Lecture 9: 5 Mar

Introduced the **min–max or "variational" theorem**, which arises for any Hermitian eigenproblem. Proved the variational theorem (with the simplifying assumption of a basis of eigenfunctions), and mentioned the derivation (in chapter 2 of the book) that all extrema of the Rayleigh quotient are eigenvalues. We will use this theorem to derive general conditions under which guided modes are guaranteed to arise in dielectric waveguides.

Used the min–max theorem to prove the existence of index-guided modes (in two dimensions, for the TE/Hz polarization), for any translation-invariant structure where ε is increased "on average" in a localized region, for an appropriate definition of "on average."

Considered related localization theorems in quantum mechanics: an arbitrary attractive potential will always localize a bound state in 1d or 2d, but not in 3d, and sketched a simple dimensional argument in 1d and 3d (but not 2d, which is a difficult borderline case); see also [these notes](https://github.com/mitmath/18303/blob/fall16/slow-waveguides.pdf). Discussed the related theorem for 3d waveguides (2d localization); see the Bamberget and Bonnet and Lee papers above.

**Further reading**: See the book, chapter 2, on the variational principle. See [these notes](https://github.com/mitmath/18303/blob/fall16/slow-waveguides.pdf) on localization in a different scalar-wave equation via the same variational method. [Bamberget and Bonnet (1990)](http://epubs.siam.org/doi/abs/10.1137/0521082) is a classic paper on the theory of dielectric waveguiding. [Lee (2008)](https://www.osapublishing.org/oe/abstract.cfm?uri=oe-16-13-9261) is an extension of the variational proof to Maxwell's equations in much more complex periodic waveguides and photonic-crystal fibers.

### Lecture 10: 10 Mar

**Discrete translational symmetry:**

Started by considering a periodic "waveguide" in two dimensions: a sequence of dielectric rods in air. By analogy with ray-optics and total-internal reflection, it seems that this could not support guided modes. However, it does (chapter 7 of the book), and to understand this we need to understand discrete translational symmetry.

Showed that the representations of the discrete translation group are again exponentials, and thereby proved **Bloch's theorem**: the eigenfunctions can be chosen in the form of a planewave multipled by a periodic function.

As a corollary, the Bloch wavevector **k** is conserved, and mentioned how this relates to a famous mystery from the 19th century: electrons in a pure conductor act almost like a dilute gas, because they scatter only from impurities/imperfections that break the periodicity.

Qualitative description of the resulting band diagrams in 1d-periodic systems.

Derived the periodicity of the Bloch wavevector **k** in one dimension. Adding 2π/a does not change the irrep, and is only a relabeling of the eigensolution. This means that we only need to look at the "unit cell" in k-space to get the band diagram. Talked about a few different ways to think about this: 2π/a gives the same irrep, it gives the same PDE for the Bloch modes, and the Bloch modes can be expanded as a Fourier series with components at k+2πm/a for all integers m.

Discussed the band diagram, light cone, and guided modes of a periodic dielectric waveguide.

As an application of conservation of k (up to addition of reciprocal lattice vectors) in periodic systems, discussed reflection (specular and diffractive) from a periodic surface, and minimum-frequency/maximum-wavelength cutoffs for various diffracted orders.

**Further reading**: Chapter 3 and appendix B of the textbook on 1d periodicity. Chapter 7 on periodic dielectric waveguides. Chapter 10 has a section on reflection/diffraction from a periodic surface.

### Lecture 11: 12 Mar

* [pset 3 solutions](psets/pset3sol.pdf)

Began new topic: **photonic crystals in one dimension**. Sketched the form of the dispersion relation (band structure) and explained several qualitative features we can predict without solving:

*   From symmetry and periodicity, ω(k)=ω(-k)=ω(k+2π/a), and consequently ω(π/a-k)=ω(π/a+k) (i.e., ω is symmetric around both k=0 and k=π/a)
*   Because ω(k) is smooth except at crossings, we expect the bands to have zero slope at k=0 and k=&pi/a (around which they are even-symmetric)
*   ωa<<1 corresponds to the long-wavelength limit, at which the waves don't "see" the periodic structure and instead see some "average" homogeneous ε (an "effective medium" or "metamaterial"; also called "homogenization theory"). Hence around (ω,k)=(0,0) the bands should approach straight lines (the solutions in a homogeneous medium).
*   Because the 1d Maxwell equations are a 2nd-order ODE, and the eigenproblem at a given ω is a 2-point boundary-value problem, there can be only two solutions at each ω. It follows that the bands ω(k) must be _monotonic_ in (0,π/a).
*   Because the symmetry group at each k has at most a mirror symmetry, which has no 2d irreps, we do not generically expect degeneracies. (By playing with the parameters, it turns out that you can force accidental degeneracies at k=0.)
*   The combination of the last two points mean that we generically expect _band gaps_ to arise: ranges of ω in which there are no solutions (at least, not at real values of k).
*   Although I haven't shown it yet, it turns out the bands have slopes that alternate in sign: the first band has positive slope in (0,π/a), the second band negative, the third positive, and so on.

We will use perturbation theory to derive the magnitude of the gap and other features by starting with a homogeneous medium and then adding a little bit of periodic ε contrast.

**Further reading:** Chapter 4 of the textbook.

### Lecture 12: 31 Mar (via Zoom videoconference)

* [pset 4](psets/pset4.pdf) and accompanying [Jupyter notebook](https://nbviewer.jupyter.org/github/mitmath/18369/blob/master/psets/pset4.ipynb) (due Thursday, April 16).
* [handwritten notes from lecture](https://www.dropbox.com/s/1c3l54mf3rh8qw3/18.369%20spring%202020.pdf?dl=0) — all subsequent notes will be at the same link.
* [video lecture recording](https://mit.zoom.us/rec/play/65Ysfrqg_DM3HN2S5gSDBqArW9S9equshycfrqIPmh3mViZVOwf3YLUVNuVqQxpPp4co2wGcmgv2FAzC?continueMode=true)

A quantitative estimate of the size of the band gap in 1d, via perturbation theory. In particular, derived first-order perturbation theory for the eigenvalue of any Hermitian operator with some small change, by expanding the eigenvalue and eigenfunction as power series in the change and solving order-by-order. We then write down this perturbative expression for the Maxwell operator, and see that the fractional change in frequency is just the fractional change in index multiplied by the fraction of electric-field energy in the changed material.

Discussed how perturbation theory can be used to derive the effect of absorption losses (to lowest order): adding a small imaginary part to ε yields a corresponding imaginary part in ω, giving loss or gain depending on the sign.

To apply perturbation to the opening of the gap, there is a slight complication because the cos(πx/a) and sin(πx/a) modes of the unperturbed (homogeneous) system are degenerate. This creates an ambiguity: to which linear combination of these eigenfunctions (i.e., what 0-th order solution) do we apply our perturbation analysis to? For a general perturbation with L-fold degeneracy, there is a technique called _degenerate perturbation theory_ that solves this problem by reducing it to an L×L eigenproblem. Here, however, we can solve the problem by symmetry: since the perturbed problem still has mirror symmetry around x=0, we know that the perturbed eigenfunctions must still be even/odd, so we must start with the cos/sin solutions.

Discussed reflection of light from a semi-infinite 1d crystal, at a frequency in the gap. We have no propagating solutions in the crystal, so by conservation of energy we must have 100% reflection. However, showed by analytical continuation of the band edge that we expect exponentially decaying "evanescent" solutions in the crystal, with a complex wavevector k ≈ sqrt(Δω/α) + π/a, where Δω is how far we are into the gap and α is the band-edge curvature.

**Further reading:** For the same derivation of perturbation theory, see "time-independent perturbation theory" in any quantum-mechanics text, e.g. Cohen-Tannoudji. See also the section on small perturbations in chapter 2 of the book. See chapter 4 of the book on the origin of the 1d gap, and on the special formulas for quarter-wave stacks in 1d (discussed in more detail in Yeh's _Optical Waves in Layered Media_). For evanescent waves and defect cavities, see chapter 4 of the textbook.

### Lecture 13: 2 April

* [Jupyter notebook](https://nbviewer.jupyter.org/github/mitmath/18369/blob/master/notes/MPB-demo.ipynb); see also [the MPB home page](https://github.com/NanoComp/mpb) and documentation

Gave demo of MPB eigensolver software for 2d dielectric waveguide (also available on Athena, e.g. in the clusters or via ssh to `athena.dialup.mit.edu`).  I recommend you try to install it via the [Anaconda Python packages](https://meep.readthedocs.io/en/latest/Installation/#conda-packages), and if you are on Windows [use the WSL method](https://meep.readthedocs.io/en/latest/Installation/#installation-on-windows).

In the handout, I used a Jupyter/IPython notebook, which is a nice way to do these calculations interactively.  The plotting here is done using the Python [matplotlib](http://matplotlib.org/) package. As explained in the [MPB tutorial](https://mpb.readthedocs.io/en/latest/Python_Tutorial/), you can also run simulations in a standalone Python (`.py`) file (or a [Scheme](https://mpb.readthedocs.io/en/latest/Scheme_User_Interface/) file if you prefer!), extract the data with `grep` and or HDF5 output, and plot results using whatever software you like.

**Further reading:** The [MPB manual page](http://mpb.readthedocs.io/en/latest/), and Appendix D of the textbook (on numerical methods).
