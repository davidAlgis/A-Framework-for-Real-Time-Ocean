# Review 1

## General Remarks

- [ ] The improvements on the existing literature are minor. Their practical implications are also not clearly presented, such as what happens if one were to use a simpler method for estimating the fluid velocity away from the surface? On the other hand, the paper describes how to combine methods developed for different components of an ocean simulation system into a single framework, which seems valuable.
- [ ] The mathematical descriptions are sufficient, though there are some errors (see below). Algorithmic descriptions could be improved. I am not sure if the paper includes sufficient information for aiding an implementation-oriented reader. There are no source codes included and no pseudocodes in the paper.
- [ ] The paper provides some limited evaluation using only 2 scenes with a single hardware configuration. Therefore, I would not consider that the system described in the paper is battle-tested. That said, it includes a sufficient evaluation to indicate that the system works and delivers good performance on a hardware with reasonable specs. The novel components are not properly tested. The paper includes some numerical evaluation, but I would have also liked to see qualitative comparisons to see how they impact the results.
- [ ] The title and the abstract are OK. I would emphasize the novel components a bit less, since their magnitude is limited and the paper lacks qualitative evaluation.

The paper includes numerous errors/typos:

## Concrete Remarks

- [ ] The normalization factor Q is missing in Equation 13.

- [x] Figure 3 caption mentions the dispersion parameter, but the figure is actually about another parameter \delta. ✅ 2025-01-10

- [ ] I am confused about the parameters of the listed cascades in Section 2.3. First of all, the ranges listed seem wrong: 12/16 is clearly greater than 12/256. I presume this is a typo. Also, shouldn't L be larger for smaller k?

- [x] Figure 9 caption says that F_a is "applied to the center of the submerged part." It should be the "unsubmerged part" instead. ✅ 2025-01-10

- [x] It is unclear what Figure 11 c shows. ✅ 2025-01-10

- [x] h* in Equations 48, 50, and 59 should be negative (following Equation 46). The same goes for unlabeled equations above Equation 53. ✅ 2025-01-10

- [x] In the Equation above Equation 56, "sinh(kY)" should be "sinh(ky)." ✅ 2025-01-10

- [x] The parameters y, t, and k in Equations 59, 60, 61, and 62 are written in an inconsistent order. They should all use the same order. ✅ 2025-01-10

- [x] This sentence in Appendix A is unclear and needs more explanation: "Note that while the third equation of system 1 is not used here, it can help to deduce the dispersion relation." ✅ 2025-01-10

- [ ] In Equation 71 v_y should be v_z.

- [ ] In Equation 73, there appears to be an extra term: h(x,t)/dt


Other minor issues:

- [ ] The abstract ends with the term "fluid to solid algorithm." I would replace it with "fluid to solid coupling algorithm."

- [ ] The introduction begins with mentioning "scientific computing," but the paper is not about scientific computing at all. I would replace it with "computer graphics."

- [ ] I would recommend removing the subsection title 1.1 and converting Section 1.2 (related work)  to Section 2.

- [ ] On page 5, "standard gravity" should be "gravitational acceleration."

- [ ] In Section 3.2.3 the description of \rho_a is repeated.

- [ ] In Section 4.4.2, "M has is bow" should be "M has a bow"

- [ ] On page 27, "fluid to solid coupling FDM" should be "solid to fluid coupling FDM."

# Review 2

## General Remarks

- [ ] The bibliography is OK, though I am a bit confused as to why Yuksel's PhD thesis is referenced, instead of the related paper:

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

- [ ] I enjoyed reading this paper. I would have liked it a lot more if it included more detailed descriptions of the algorithms and/or source code.


- [ ]  it could do better:
a) The paper should be a bit less heavy on hydrodynamic theory details: several equation sequences involving JONSWAP and Donelan-Banner spectra are taken verbatim from quoted references (e.g. Horvath) and are not really used much beyond the page they are on. It does not feel like the minute details of the spectrum derivation and empirical coefficients involved contributes much to understanding of the general theory (at least not from the jcgt perspective, but I might be wrong?)
b) give more detail on the actual implementation: memory layout on the GPU, implementation of the kernels etc. This is especially relevant since performance timing is given in Sec 5 of the paper, but the rest of the paper gives us little idea as to why these number are such as they are. For example, the bottleneck in Fig 14 seems to be geometry and force computation (intersection geometry computation). Why should this be so slow?

- [ ] No quite. As mentioned above, the paper should provide more implementation details, specifically with regard to the GPU computation and data layout, specifically to explain the timing numbers in Fig 14, and why some of them seem a bit heavy (e.g. like geometry processing). the paper also mentions that no serious CPU-side computation is used - it would be interesting to know why (e.g. could the geometry processing (intersection curve), which seems to be a bottleneck according to Fig 14, be offloaded to CPU?)

## Concrete Remarks

Sec 1
=====

1.1
---
- [ ] 1st bullet point, (Tex error) here and elsewhere Tessendorf is quoted as 
"Tessendorf (2004) [Tessendorf 1999]" (i.e. reference link and text do not match)

Sec 2
=====

- [ ] Sec 2.1 - 2.5 are very heavy on hydrodynamics.

- [ ] For example, starting with eq (5) on p6 all bullet points below on JONSWAP spectrum are straight from page 33 of Horvath (there it is eq 28). There is probably no need to copy this here verbatim, rather than giving a cursory explanation of what the terms of (5) are, a derivation into a more computationally ready form would be better.

- [ ] The same goes for the details of the usual Donelan-Banner spectrum, specifically eqns (7) - (12), could just refer to Sections 6.0.9 - 6.1 of Horvath. The focus instead could be on approximation in eq (17), which is original, and the conclusion eq (18).

2.2
---

- [ ] Isn't $k$ locally constant (wrt x,z)? Then could just write 
$$\frac{\partial D_x}{\partial x} = i k_x D_x$$
for the first equation, and similar for the other 4 derivatives. Makes it easier to read and is explicit about computation needed.

2.5
---
- [ ] Second paragraph p 12. It would be helpful to have some details on memory organization for the NxN tiles, computation efficiency on the GPU, etc - especially since quoting performance numbers in Sec 5, Figure 14.

2.6
---

- [ ] Paragraph 1, p 13, awkward phrasing "...tied to the wave vector, preventing from any simplifications to reduce the needed calculations."
Maybe ".., preventing any simplifications that could reduce the required calculations."

- [ ] Para 2, p 14 "First, while the velocity decays exponentially, it relies on a logarithmic similar to..."
should probably be "..., it relies on a logarithmic function similar to..."

- [ ] Same paragraph, "this function decreases slowly (actually with ln(250 + 1) = 5.5),"
What is the significance of "250 + 1" here?!

- [ ] Figure 6, vertical scale should probably be logarithmic to make these graphs more informative. As it is now, three of four graphs are scrunched on top of each other.

- [ ] Not sure why the bracket "{" in eq. (28). Also it does not look like eq (28) is quoted in the rest of the paper, so $\alpha$ and $\beta$ could just be given inline.


Sec 3
=====

3.1
---

3.2.1

- [ ] p 17. "The Arc Blanc framework uses the prism approximation proposed by Bajo et al."

- [ ] How? In Bajo et al. paper, the geometry (position & area vector, is stored in texels of the surface textures of the model.) The prisms used there are per texel, so for example the prism height is determined by (average) water height above the projected texel center. How is this done here?

Specifically,

- [ ] "The principles of their method are as follows: from each submerged triangle $T^s_i$ of the body, a prism is build up to the water surface; hence, each prism volume can be calculated, and so the full submerged volume vw by adding all of them."

- [ ] This is not exactly correct - their computation is at surface texel granularity level - it is not immediately obvious how this is to be done on triangle basis (e.g. uniform tessellation?)

3.2
---

- [ ] Sections 3.2.2 and 3.2.3 details are redundant: the only true geometric difference between the two is that in one case we are considering velocity of water while in the other velocity of air (density and drag coefficient being that of the medium under consideration can be understood from context)

- [ ] Also, p19 Paragraph 2 has a typo: the 3rd and 4th bullets are identical

3.3
---

- [ ] As above, item 3, it is not clear how to do the volume computation. The paper claims it is triangle based, while the quoted source (Bajo et al) uses surface texel based computation. Does the author imply that some sort of uniform triangulation scheme is to be used? If so, then there is also the matter of closing and triangulating the polygons given by the (approximate) cutting of triangles against the waterline described in paragraph 2 of 3.1 on p 17 by referring to Kerner's paper.

- [ ] Figure 9, p 20 mentioning c_i, COG, center of submerged part etc, but these are not labeled in the diagram, which produces unnecessary cognitive load when reading the diagram. Also, can spread the vectors a bit to declutter (dont need to have them bunched up so realistically), likewise v_a and v_w are not collinear in general. Larger arrow tips would help.


Sec 4.
=====

4.1
---

- [ ] Paragraph 1, suggesting change of notation, e.g. $\delta$ instead of $dx$ for the discretization step. This would make (35) (38) (40) (42) less confusing when first seen (e.g. it's not a differential), or $\Delta{x}, \Delta{y}, \Delta{t}$, but that might be a bit too detailed, e.g. since the grid is regular.


- [ ] Eq (36)  probably it is easier to read something like

$u = clamp_hi(|v|/v_max, 1)$ and $d(t) = lerp(d0, d_max, u)$

than the given piecewise definition.

- [ ] Numeric values like the ones in eq 37, which affect stability, might be meaningless if some implementation details of the framework are not been specified (e.g. floats, doubles etc)?

4.2
---

- [ ] A simple diagram showing the relationship between (i,j), (k,l), and (o,p) would make (39) easier to read (e.g. could extend Fig 10 to show this).

4.3 
---

- [ ] "The value of c is deduced from dx and dt to validate the CFL as follows"

Deduced how? \sqrt(0.49) seems close to \sqrt(0.5) which you would get from Eq (40)?

4.4
---

- [ ] Last paragraph on p 23, typo: "corresponding to the vertices of Z contained into one intersected polygons." should be "...in one of the intersection polygons"

4.4.1
-----

- [ ] Paragraph 1, typo: "contained into one intersection polygon" should be "contained in one of the intersection polygons"

- [ ] The reference to (what I assume is) CLRS listed in the References section is incorrectly written. Also CLRS is too general so probably not needed here. Stabbing ray approach described might have robustness issues - are those significant enough to cause some form of instability in the simulation?

- [ ] Last sentence of the last paragraph of 4.4.1, typo: "technic"

- [ ] Also, not explicitly mentioned, but I am guessing that the intersection polygons from sec 3.1 are projected onto xz plane in order to do z-ray stabbing in sec 4.4.1. Could some such projected intersection polygons then be generate (e.g. self intersecting when projected onto zx plane, or inverted - e.g. for turbulent water height and finely tessellated body M)

- [ ] Also, doing ray stabbing on multiple components probably increases chances of bad classification of a point. Could do closed component count (provided the model M is a closed orientable surface to start with, so the intersection polygons have well-defined interior) to speed up the test.

4.4.2
-----

- [ ] Sentence 2, paragraph 1, typo: "By construction of the grid Z, M has is bow oriented on the positive side of the z axis and its starboard on the positive side of the x axis."

- [ ] Should be "..has *its* bow.."?

- [ ] Also, for landlubbers among us, please clarify "starboard" as "right-hand side when facing the bow" :)

- [ ] End of the same paragraph:

- [ ] "Hence, h is made such that from the vertex at position x, the front of the mask is above the free surface and the back below, in a way that is proportional to the speed of M. Moreover, the boat forms a V shape, with its center a bit below the extremity of the side."

I can not visualize this. For example, 

- [ ] - what is meant here by "front of the mask is above the free surface and the back below"?
- [ ] - "..the boat forms a V shape.." - does V here mean that the boat is in the shape of the letter "V", or does V denote the shape (object) in question? For example, the sentence before eq (43) says "The function f models the side effect using a shape in V", which suggest the latter, but the next sentence says "The V-shape is obtained from the absolute value of the abscissa" (note the hyphen) which suggest the former.

- [ ] Can we please have a diagram that shows and explains this geometry configuration clearly - in addition to Fig 11?

Sec 5
=====

- [ ] Figure 14. XP2 geometry, section 3.1. 4.6 msec for 4153 triangles vertex classification and splitting seems a bit excessive. Same goes for forces computation. This, for example, is why it would be nice to see more implementation details.

- [ ] Also, an idea: maybe assuming that the intersection shape is more or less the same between two consecutive frames, for low Beaufort state at least, (and for some k steps, where k is small), then recompute the buoyancy/volume based on the previous volume of the submerged shape, correcting for the height difference of the water between the two frames, then on k-th step doing the correct computation?

# Review 3 

## General Remarks

- [ ] Although, the solid->water action simulation is primitive and lacks explanations and obvious improvements:
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

- [ ] Overall the paper allows to implement presented technique without much trouble for people that have experience with the topic of the paper, 
although better explanation of how the forces acting on solid object in water are summed up and used to evolve solid object dynamics would improve it a lot.
Is the sum of the forces applied to center of gravity of the object? Or there are rotational moments?
Are moments of inertia of the solid object taken in account? 
What about the moment of inertia of water body surrounding the object?
Without those explained, this part of the abstract looks like a bit of overstatement:

- [ ] One note: deciseconds? Please, use seconds or milliseconds.

- [ ] The paper lists a ton of references that are not touched in the paper in the sense that the paper does not derive anything from those.
For instance, 
1. SPH papers are not related.
2. Wave particles are not related
3. Water wave packets are not related

- [ ] In chapter 2.6 the "interpolation degree" term is unclear and a bit misleading, 
and since the interpolation is based on water body displacements calculated at "slices" with fixed depth, 
I'd suggest term "interpolation slice" and "number of interpolation slices", for instance on Figure 7.
## 