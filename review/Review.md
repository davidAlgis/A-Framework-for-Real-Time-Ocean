# Summary

Decision: Accept

The idea of publishing a paper that aids in the implementation of a system, more than focusing just on novelty, seems in the spirit of JCGT and it is to me welcome.

The reviewers also noted positively this fact, and through that lens mostly ask (review 1 and 2 especially) if some of the verbosity can be shortened in favor of perhaps adding more implementation details (pseudo-code, data structure layouts where relevant, etc.).

I mostly agree that these would be welcome improvements, considering the nature of the paper it is important to read if from the perspective of someone who is more implementation-minded.

That said - I don't think these improvements are strictly necessary for publication, if the errors and typos noted by the reviewers are addressed - to me they are good suggestions for the authors on how to improve the presentation of the paper, but ultimately, it's in the author's hands to decide what's the best angle - in ours it's only the evaluation of whether or not the paper is interesting enough for our venue (and I think it is) and of course, correct errors.

Lastly, I also would not emphasize the suggestion of adding more test scenarios and evaluations of the novel parts of the paper, as researchers we always want to see more comparatives - and it's obviously a good thing if these can be produced, but I find that's a suggestion that is almost universally valid but also rarely a critical thing to address.

Note from EiC: it is probably worth noting the work https://dl.acm.org/doi/10.1145/3675388 in a revision, which in fact was published after submission of this work.


# Review 1

                  Journal of Computer Graphics Techniques Review Form

Reviewer Instructions: Complete this form and return it to
editor-in-chief@jcgt.org as an e-mail or e-mail attachment in plain
text form. Please do not convert it to PDF.

Please phrase your comments to preserve your anonymity.

We invite you to diverge from the format here if there is a better way
to organize your feedback on this paper.

A member of the editorial board will read this form and then either
shepherd the paper through publication (possibly with another round of
review), or reject the paper (with later resubmission allowed).



A JCGT paper should provide a concrete technique with sufficient
information to allow the reader to:

* Understand how it differs from alternatives
* Know the advantages AND limitations that will likely be encountered
  in practice
* Immediately integrate it into a production workflow

While not every acceptable paper must have this form, a great example
of a JCGT paper would be a technique that addresses a common graphics
problem, has been used in production, can be well-summarized in a few
pages with a complete implementation in a popular language and full
performance or accuracy evaluation.

As an example, SIGGRAPH paper on a new stable physics algorithm would
have a philosophical introduction, extensive related work, a
derivation section, and attractive result images for some common
benchmark scenes. A JCGT physics paper might instead begin by
sketching available physics libraries, have a minimal related work
section on current research, give a derivation augmented with complete
source code (maybe as supplemental files), and replace the results
section with timing on various architectures, extensive discussion of
stability and limitations, and a table of results on real-world test
cases.


_____________________________________________________________________________
Paper Title: Arc Blanc: a real time ocean simulation framework
Paper Authors: David Algis, Berenger Bramas, Emmanuelle Darles, Lilian Aveneau


> *  What kind of paper is this?
>       Novel Research/Algorithm/System
>       Survey
>       Experience/Advice/Case Study
>       Production/Implementation Notes
>       Tutorial
>       Data Set

Novel Research/Algorithm/System



> *  Is this a paper that others should read?
>
>    If this paper answered a question that you have, made more clear
>    how to implement something, changed the way that you think about
>    a problem, enabled further work, or worked out the details of
>    something that you've thought of before, then it probably is
>    interesting to JCGT, regardless of the magnitude of the
>    contribution. If it re-covers old ground or doesn't distinguish
>    itself along at least one axis like clarity, reliability, or
>    quality, then this may not be the right venue.

Yes. The paper combines methods developed for ocean simulation and solid-fluid coupling over the past few decades into a complete system with a good discussion of the choices made and their limitations. I believe this is a helpful source for anyone who would like to implement such an ocean simulation system in a video game.



> *  What is the concrete contribution ("technique") of this paper? 
>
>    This should be an algorithm, piece of code, workflow pattern,
>    data set, proof, equation, circuit, system, or survey that the
>    readers can directly apply to their own work.

The main contribution of this paper is the system, explaining which techniques are helpful in practice, and providing sufficient details to describe them without getting too much into their derivations. The paper also includes novel components but I would consider them minor.



> *  How does this technique improve on the existing literature for the
>    topic?
>
>    For example, it may offer better performance, fewer limitations,
>    make the implementation clearer, provide better evaluation, etc.
>    An idea need not be novel, but it must offer improvement.
>    Likewise, a technique need not be better in all dimensions--a
>    slower method that saves space or is easier to implement may be
>    of value. Sometimes there is significant related work that the
>    author may be unaware of that alters the value of the
>    contribution. If that is the case, please give a citation and
>    explain the significance.

The improvements on the existing literature are minor. Their practical implications are also not clearly presented, such as what happens if one were to use a simpler method for estimating the fluid velocity away from the surface? On the other hand, the paper describes how to combine methods developed for different components of an ocean simulation system into a single framework, which seems valuable.



> *  Is this paper topical? 
>
>    If this is something that you want to try, tell your colleagues
>    about, or wish you had known earlier, it is sufficiently topical.
>    Do you want to see a paper on this topic or technique published?

Yes.



> *  Does the paper provide sufficient information for you to deploy
>    the technique?
>
>    It should prevent you from going down false paths, avoid having
>    the implementer reconstruct tedious details, generally speed
>    integration, and indicate strategies for verifying correctness.
>
>    List any additional elements required to deploy it that are not
>    provided. 

The mathematical descriptions are sufficient, though there are some errors (see below). Algorithmic descriptions could be improved. I am not sure if the paper includes sufficient information for aiding an implementation-oriented reader. There are no source codes included and no pseudocodes in the paper.



> *  How has the technique been proven or battle-tested? 
>
>    Some ways to demonstrate this include: use in production, formal
>    mathematical proof, and extensive accuracy and performance tests
>    on real-world data. "Production" need not be commercial, e.g.,
>    widely-adopted open source applications and libraries, and
>    teaching and research infrastructure used for several years
>    contain techniques that are useful, well-understood by their
>    authors, and reliable. (An idea may be worthy as research, but
>    not mature enough to be considered a graphics technique.)
>
>    List additional information, tests, data, or experiments required
>    to achieve this threshold.

The paper provides some limited evaluation using only 2 scenes with a single hardware configuration. Therefore, I would not consider that the system described in the paper is battle-tested. That said, it includes a sufficient evaluation to indicate that the system works and delivers good performance on a hardware with reasonable specs.

The novel components are not properly tested. The paper includes some numerical evaluation, but I would have also liked to see qualitative comparisons to see how they impact the results.



> *  Evaluate the title and abstract.  How can they be improved to better 
>    explain the take-home contribution of the paper?

The title and the abstract are OK. I would emphasize the novel components a bit less, since their magnitude is limited and the paper lacks qualitative evaluation.



> *  Rate the quality and level of detail of the exposition as a whole.
>
>    A JCGT paper need not have explicit "related work", "results",
>    and "conclusions" sections. It should offer extensive
>    verification. The text should be to the point, limit itself to a
>    single topic, and be supported by lists, equations, tables, and
>    figures as needed.
>
>    Note typos, confusing sections, figures, or ambiguous text. Also
>    note exemplary text and diagrams. Suggest material that could be
>    cut to tighten the focus on the core contribution of the paper.

The paper is easy to read. It is a bit verbose and could be shortened, but I think it is acceptable.



> *  List objective factual errors or overstatements in the technical
>    content of the paper. Please suggest corrections where possible.

The paper includes numerous errors/typos:

- The normalization factor Q is missing in Equation 13.

- Figure 3 caption mentions the dispersion parameter, but the figure is actually about another parameter \delta.

- I am confused about the parameters of the listed cascades in Section 2.3. First of all, the ranges listed seem wrong: 12/16 is clearly greater than 12/256. I presume this is a typo. Also, shouldn't L be larger for smaller k?

- Figure 9 caption says that F_a is "applied to the center of the submerged part." It should be the "unsubmerged part" instead.

- It is unclear what Figure 11 c shows.

- h* in Equations 48, 50, and 59 should be negative (following Equation 46). The same goes for unlabeled equations above Equation 53.

- In the Equation above Equation 56, "sinh(kY)" should be "sinh(ky)."

- The parameters y, t, and k in Equations 59, 60, 61, and 62 are written in an inconsistent order. They should all use the same order.

- This sentence in Appendix A is unclear and needs more explanation: "Note that while the third equation of system 1 is not used here, it can help to deduce the dispersion relation."

- In Equation 71 v_y should be v_z.

- In Equation 73, there appears to be an extra term: h(x,t)/dt


Other minor issues:

- The abstract ends with the term "fluid to solid algorithm." I would replace it with "fluid to solid coupling algorithm."

- The introduction begins with mentioning "scientific computing," but the paper is not about scientific computing at all. I would replace it with "computer graphics."

- I would recommend removing the subsection title 1.1 and converting Section 1.2 (related work)  to Section 2.

- On page 5, "standard gravity" should be "gravitational acceleration."

- In Section 3.2.3 the description of \rho_a is repeated.

- In Section 4.4.2, "M has is bow" should be "M has a bow"

- On page 27, "fluid to solid coupling FDM" should be "solid to fluid coupling FDM."



> *  Is the bibliography adequate (not too little or too much)?  
>
>    JCGT papers should only cite directly relevant work that is
>    discussed in the text, and should not cite early papers on topics
>    that are so commonly known as to appear in textbooks. Often three
>    citations are sufficient. Primary, archival, and peer-reviewed
>    sources are strongly preferred because they stand the test of
>    time. Please suggest specific references that might be
>    eliminated, for example, ones that nod to previous work but which
>    you don't realistically see a reader seeking out in response to
>    this paper.

The bibliography is OK, though I am a bit confused as to why Yuksel's PhD thesis is referenced, instead of the related paper:

@article{Yuksel2007,
   author       = {Cem Yuksel and Donald H. House and John Keyser},
   title        = {Wave Particles},
   journal      = {ACM Transactions on Graphics (Proceedings of SIGGRAPH 2007)},
   year         = {2007},
   volume       = {26},
   number       = {3},
   articleno    = {99},
   location     = {San Diego, California},
   url          = {http://doi.acm.org/10.1145/1276377.1276501},
   doi          = {10.1145/1276377.1276501},
   acmid        = {1276501},
   publisher    = {ACM Press},
   address      = {New York, NY, USA},
}


> *  Is the paper ready for shepherding by an editor to incorporate
>    changes requested in this review?
>
>    Could it be made ready for publication with one or more rounds 
>    of improvement guided by an associate editor, but without any 
>    additional external reviews?

Yes.



> *  Additional comments are welcome here.

I enjoyed reading this paper. I would have liked it a lot more if it included more detailed descriptions of the algorithms and/or source code.


# Review 2

_____________________________________________________________________________
Paper Title: Arc Blanc: a real time ocean simulation framework
Paper Authors: David Algis, Berenger Bramas, Emmanuelle Darles


> *  What kind of paper is this?
>       Survey
>       Experience/Advice/Case Study

The paper's stated aim is to gather in one place building blocks of ocean simulation theory found in literature, and to describe how they interconnect.


> *  Is this a paper that others should read?

Yes.
For example, this paper would be a good starting place for somebody who is new to ocean simulation but wishes to implement a functioning system.
If this is paper's aim, there are two places where it could do better:
a) The paper should be a bit less heavy on hydrodynamic theory details: several equation sequences involving JONSWAP and Donelan-Banner spectra are taken verbatim from quoted references (e.g. Horvath) and are not really used much beyond the page they are on. It does not feel like the minute details of the spectrum derivation and empirical coefficients involved contributes much to understanding of the general theory (at least not from the jcgt perspective, but I might be wrong?)
b) give more detail on the actual implementation: memory layout on the GPU, implementation of the kernels etc. This is especially relevant since performance timing is given in Sec 5 of the paper, but the rest of the paper gives us little idea as to why these number are such as they are. For example, the bottleneck in Fig 14 seems to be geometry and force computation (intersection geometry computation). Why should this be so slow?

More details are mentioned below.

1. 

> *  What is the concrete contribution ("technique") of this paper? 

1. gathering in one place a streamlined details of how to build an ocean simulation system
2. fluid velocity computation optimization: in general, this would involve calculating IFFT at each 3D point of simulation. The paper describes how to save computation by utilizing discretization of depth and interpolation. These velocities are used to calculate fluid and air drag forces for the fluid-solid coupling
3. Lagrange poly approximation to Donelan-Banner spectra normalization factor (eq (17))


> *  How does this technique improve on the existing literature for the
>    topic?

Fluid velocity computation in the Arc Blanc framework is an original optimization - specifically the interpolation method using logarithmic distribution. Also the analysis of interpolation degree using multi-objective optimization to balance fast computation time with accuracy.


> *  Is this paper topical? 
>
Yes, it would be interesting to implement an ocean system using this paper.


> *  Does the paper provide sufficient information for you to deploy
>    the technique?
>
No quite. As mentioned above, the paper should provide more implementation details, specifically with regard to the GPU computation and data layout, specifically to explain the timing numbers in Fig 14, and why some of them seem a bit heavy (e.g. like geometry processing). the paper also mentions that no serious CPU-side computation is used - it would be interesting to know why (e.g. could the geometry processing (intersection curve), which seems to be a bottleneck according to Fig 14, be offloaded to CPU?)


> *  How has the technique been proven or battle-tested? 
>
There are not code repos attached to this paper. But there are a number of animations given which (probably) demonstrate that this system has been implemented?


> *  Evaluate the title and abstract.  How can they be improved to better 
>    explain the take-home contribution of the paper?

Both are fine and to the point.

> *  Rate the quality and level of detail of the exposition as a whole.
>
Mod few typos/grammatical errors, the exposition is clear. 
As I've noted, it would be helpful to tone down some hydrodynamic details (e.g. details on spectra) in favor of more exposition on practical implementation details.

>    Note typos, confusing sections, figures, or ambiguous text. Also
>    note exemplary text and diagrams. Suggest material that could be
>    cut to tighten the focus on the core contribution of the paper.

Sec 1
=====

1.1
---
1st bullet point, (Tex error) here and elsewhere Tessendorf is quoted as 
"Tessendorf (2004) [Tessendorf 1999]" (i.e. reference link and text do not match)

Sec 2
=====

Sec 2.1 - 2.5 are very heavy on hydrodynamics.

For example, starting with eq (5) on p6 all bullet points below on JONSWAP spectrum are straight from page 33 of Horvath (there it is eq 28). There is probably no need to copy this here verbatim, rather than giving a cursory explanation of what the terms of (5) are, a derivation into a more computationally ready form would be better.

The same goes for the details of the usual Donelan-Banner spectrum, specifically eqns (7) - (12), could just refer to Sections 6.0.9 - 6.1 of Horvath. The focus instead could be on approximation in eq (17), which is original, and the conclusion eq (18).

2.2
---

Isn't $k$ locally constant (wrt x,z)? Then could just write 
$$\frac{\partial D_x}{\partial x} = i k_x D_x$$
for the first equation, and similar for the other 4 derivatives. Makes it easier to read and is explicit about computation needed.

2.5
---
Second paragraph p 12. It would be helpful to have some details on memory organization for the NxN tiles, computation efficiency on the GPU, etc - especially since quoting performance numbers in Sec 5, Figure 14.

2.6
---

Paragraph 1, p 13, awkward phrasing "...tied to the wave vector, preventing from any simplifications to reduce the needed calculations."
Maybe ".., preventing any simplifications that could reduce the required calculations."

Para 2, p 14 "First, while the velocity decays exponentially, it relies on a logarithmic similar to..."
should probably be "..., it relies on a logarithmic function similar to..."

Same paragraph, "this function decreases slowly (actually with ln(250 + 1) = 5.5),"
What is the significance of "250 + 1" here?!

Figure 6, vertical scale should probably be logarithmic to make these graphs more informative. As it is now, three of four graphs are scrunched on top of each other.

Not sure why the bracket "{" in eq. (28). Also it does not look like eq (28) is quoted in the rest of the paper, so $\alpha$ and $\beta$ could just be given inline.


Sec 3
=====

3.1
---

3.2.1

p 17. "The Arc Blanc framework uses the prism approximation proposed by Bajo et al."

How? In Bajo et al. paper, the geometry (position & area vector, is stored in texels of the surface textures of the model.) The prisms used there are per texel, so for example the prism height is determined by (average) water height above the projected texel center. How is this done here?

Specifically,

"The principles of their method are as follows: from each submerged triangle $T^s_i$ of the body, a prism is build up to the water surface; hence, each prism volume can be calculated, and so the full submerged volume vw by adding all of them."

This is not exactly correct - their computation is at surface texel granularity level - it is not immediately obvious how this is to be done on triangle basis (e.g. uniform tessellation?)

3.2
---

Sections 3.2.2 and 3.2.3 details are redundant: the only true geometric difference between the two is that in one case we are considering velocity of water while in the other velocity of air (density and drag coefficient being that of the medium under consideration can be understood from context)

Also, p19 Paragraph 2 has a typo: the 3rd and 4th bullets are identical

3.3
---

As above, item 3, it is not clear how to do the volume computation. The paper claims it is triangle based, while the quoted source (Bajo et al) uses surface texel based computation. Does the author imply that some sort of uniform triangulation scheme is to be used? If so, then there is also the matter of closing and triangulating the polygons given by the (approximate) cutting of triangles against the waterline described in paragraph 2 of 3.1 on p 17 by referring to Kerner's paper.

Figure 9, p 20 mentioning c_i, COG, center of submerged part etc, but these are not labeled in the diagram, which produces unnecessary cognitive load when reading the diagram. Also, can spread the vectors a bit to declutter (dont need to have them bunched up so realistically), likewise v_a and v_w are not collinear in general. Larger arrow tips would help.


Sec 4.
=====

4.1
---

Paragraph 1, suggesting change of notation, e.g. $\delta$ instead of $dx$ for the discretization step. This would make (35) (38) (40) (42) less confusing when first seen (e.g. it's not a differential), or $\Delta{x}, \Delta{y}, \Delta{t}$, but that might be a bit too detailed, e.g. since the grid is regular.


Eq (36)  probably it is easier to read something like

$u = clamp_hi(|v|/v_max, 1)$ and $d(t) = lerp(d0, d_max, u)$

than the given piecewise definition.

Numeric values like the ones in eq 37, which affect stability, might be meaningless if some implementation details of the framework are not been specified (e.g. floats, doubles etc)?

4.2
---

A simple diagram showing the relationship between (i,j), (k,l), and (o,p) would make (39) easier to read (e.g. could extend Fig 10 to show this).

4.3 
---

"The value of c is deduced from dx and dt to validate the CFL as follows"

Deduced how? \sqrt(0.49) seems close to \sqrt(0.5) which you would get from Eq (40)?

4.4
---

Last paragraph on p 23, typo: "corresponding to the vertices of Z contained into one intersected polygons." should be "...in one of the intersection polygons"

4.4.1
-----

Paragraph 1, typo: "contained into one intersection polygon" should be "contained in one of the intersection polygons"

The reference to (what I assume is) CLRS listed in the References section is incorrectly written. Also CLRS is too general so probably not needed here. Stabbing ray approach described might have robustness issues - are those significant enough to cause some form of instability in the simulation?

Last sentence of the last paragraph of 4.4.1, typo: "technic"

Also, not explicitly mentioned, but I am guessing that the intersection polygons from sec 3.1 are projected onto xz plane in order to do z-ray stabbing in sec 4.4.1. Could some such projected intersection polygons then be generate (e.g. self intersecting when projected onto zx plane, or inverted - e.g. for turbulent water height and finely tessellated body M)

Also, doing ray stabbing on multiple components probably increases chances of bad classification of a point. Could do closed component count (provided the model M is a closed orientable surface to start with, so the intersection polygons have well-defined interior) to speed up the test.

4.4.2
-----

Sentence 2, paragraph 1, typo: "By construction of the grid Z, M has is bow oriented on the positive side of the z axis and its starboard on the positive side of the x axis."

Should be "..has *its* bow.."?

Also, for landlubbers among us, please clarify "starboard" as "right-hand side when facing the bow" :)

End of the same paragraph:

"Hence, h is made such that from the vertex at position x, the front of the mask is above the free surface and the back below, in a way that is proportional to the speed of M. Moreover, the boat forms a V shape, with its center a bit below the extremity of the side."

I can not visualize this. For example, 

- what is meant here by "front of the mask is above the free surface and the back below"?
- "..the boat forms a V shape.." - does V here mean that the boat is in the shape of the letter "V", or does V denote the shape (object) in question? For example, the sentence before eq (43) says "The function f models the side effect using a shape in V", which suggest the latter, but the next sentence says "The V-shape is obtained from the absolute value of the abscissa" (note the hyphen) which suggest the former.

Can we please have a diagram that shows and explains this geometry configuration clearly - in addition to Fig 11?

Sec 5
=====

Figure 14. XP2 geometry, section 3.1. 4.6 msec for 4153 triangles vertex classification and splitting seems a bit excessive. Same goes for forces computation. This, for example, is why it would be nice to see more implementation details.

Also, an idea: maybe assuming that the intersection shape is more or less the same between two consecutive frames, for low Beaufort state at least, (and for some k steps, where k is small), then recompute the buoyancy/volume based on the previous volume of the submerged shape, correcting for the height difference of the water between the two frames, then on k-th step doing the correct computation?


> *  List objective factual errors or overstatements in the technical
>    content of the paper. Please suggest corrections where possible.

See notes for Sec 3.2.1 and 3.3 above. Also above is a note on potential stability issues for Sec 4.4.1, and a note in Sec 5.


> *  Is the bibliography adequate (not too little or too much)?  
>
More than adequate.


> *  Is the paper ready for shepherding by an editor to incorporate
>    changes requested in this review?
>
Yes, provided some of the changes are done - specifically reducing some of the hydrodynamic spectra material and adding more on implementation details.

>    Could it be made ready for publication with one or more rounds 
>    of improvement guided by an associate editor, but without any 
>    additional external reviews?

Yes.



# Review 3 

                  Journal of Computer Graphics Techniques Review Form

Reviewer Instructions: Complete this form and return it to
editor-in-chief@jcgt.org as an e-mail or e-mail attachment in plain
text form. Please do not convert it to PDF.

Please phrase your comments to preserve your anonymity.

We invite you to diverge from the format here if there is a better way
to organize your feedback on this paper.

A member of the editorial board will read this form and then either
shepherd the paper through publication (possibly with another round of
review), or reject the paper (with later resubmission allowed).



A JCGT paper should provide a concrete technique with sufficient
information to allow the reader to:

* Understand how it differs from alternatives
* Know the advantages AND limitations that will likely be encountered
  in practice
* Immediately integrate it into a production workflow

While not every acceptable paper must have this form, a great example
of a JCGT paper would be a technique that addresses a common graphics
problem, has been used in production, can be well-summarized in a few
pages with a complete implementation in a popular language and full
performance or accuracy evaluation.

As an example, SIGGRAPH paper on a new stable physics algorithm would
have a philosophical introduction, extensive related work, a
derivation section, and attractive result images for some common
benchmark scenes. A JCGT physics paper might instead begin by
sketching available physics libraries, have a minimal related work
section on current research, give a derivation augmented with complete
source code (maybe as supplemental files), and replace the results
section with timing on various architectures, extensive discussion of
stability and limitations, and a table of results on real-world test
cases.


_____________________________________________________________________________
Paper Title: Arc Blanc: a real time ocean simulation framework
Paper Authors:
David Algis, Universit´e de Poitiers
Berenger Bramas,INRIA Nancy
Lilian Aveneau, Universit´e de Poitiers
Emmanuelle Darles, Universit´e de Poitiers

> *  What kind of paper is this?
>       Novel Research/Algorithm/System
>       Experience/Advice/Case Study


> *  Is this a paper that others should read?
>
Yes, the first part of the paper that enables improved water->solid interaction definitely deserves attention.



> *  What is the concrete contribution ("technique") of this paper? 

The paper presents a novel and apparently quite efficient, accurate and convenient method 
of calculating velocities of water body at the surface and underneath, based on using inverse FFT over ocean spectrum
on the set of horizontal slices at the fixed water depth. 
Optimization technique, aimed at improving simulation precision at fixed cost by distributing slices 
logarithmically and using piecewise non-linear interpolation, is presented.
The paper shows the thought process and explanation to steps that led to derivation of the method.

The water->solid interaction simulation method used in this paper is not novel and is based on summing up forces acting on hull triangles submerged in water,
but coupled with simulation of water volume presented in the paper, it allows to achieve much higher accuracy for simulating movement of the solid objects in water.

The solid->water interaction simulation is rather primitive and does not deserve attention.


> *  How does this technique improve on the existing literature for the
>    topic?

The paper enables straightforward implementation of simulation of movement of solid bodies in water with high accuracy.


> *  Is this paper topical? 
>
Yes, I want to try to improve my simulation of solid objects based on simulation of waver volume presented in the paper.


> *  Does the paper provide sufficient information for you to deploy
>    the technique?

Yes. Water->solid action part of the paper is very solid.

Although, the solid->water action simulation is primitive and lacks explanations and obvious improvements:
1. The movement of the hulls and how the corresponding translations/rotations of hulls affect the solid->water interaction is not clearly described.
It appears that only the translation part is taken in account.
2. Finite difference method used to simulate interactive waves is extremely primitive and is able to simulate vertical displacement of interactive waves only. 
Tessendorf's eWave based on FFT+iFFT per simulation step is a bit more expensive but produces full 3D displacements of the interactive waves.
3. Injecting displacements into water caused by movement of solid objects, called wave generation in the paper, based on functions representing side and front/back effect, looks absolutely artificial. 
Instead, a per-gridpoint signed difference in volumes produced by intersections of hull volume and still water volume at current vs previous simulation step 
could be used to generate water displacements based on incompressibility pf water.
4. Mask movement and orientation used in paper, so that front of the mask is above water surface and back is below water surface, looks artificial and extremely simplified.
A propulsion force acting on hull and causing it to move, in conjunction with proper water->solid interaction from the 1st part of the paper, with its forces and moments, 
will naturally cause hull to raise its bow based on physically correct simulation instead of oversimplified approximation used in the paper.


> *  How has the technique been proven or battle-tested? 
>

Analysis of performance vs precision was done, analysis of the simulation stability for interactive waves was done.
Videos showing simulation in action were attached.


> *  Evaluate the title and abstract.  How can they be improved to better 
>    explain the take-home contribution of the paper?

Title and abstract look ok.


> *  Rate the quality and level of detail of the exposition as a whole.
>

Overall the paper allows to implement presented technique without much trouble for people that have experience with the topic of the paper, 
although better explanation of how the forces acting on solid object in water are summed up and used to evolve solid object dynamics would improve it a lot.
Is the sum of the forces applied to center of gravity of the object? Or there are rotational moments?
Are moments of inertia of the solid object taken in account? 
What about the moment of inertia of water body surrounding the object?
Without those explained, this part of the abstract looks like a bit of overstatement:

"this paper proposes to bring all these components together, detailing all their interactions, in a
comprehensive and fully described real-time framework that simulates the free ocean surface
and the coupling between solids and fluid."


> *  List objective factual errors or overstatements in the technical
>    content of the paper. Please suggest corrections where possible.

I didn't find factual errors.
One note: deciseconds? Please, use seconds or milliseconds.

> *  Is the bibliography adequate (not too little or too much)?  
>

The paper lists a ton of references that are not touched in the paper in the sense that the paper does not derive anything from those.
For instance, 
1. SPH papers are not related.
2. Wave particles are not related
3. Water wave packets are not related


> *  Is the paper ready for shepherding by an editor to incorporate
>    changes requested in this review?

I'm not sure. 

> *  Additional comments are welcome here.

In chapter 2.6 the "interpolation degree" term is unclear and a bit misleading, 
and since the interpolation is based on water body displacements calculated at "slices" with fixed depth, 
I'd suggest term "interpolation slice" and "number of interpolation slices", for instance on Figure 7.


