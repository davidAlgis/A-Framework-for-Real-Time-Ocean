# Review 1

## Concrete Remarks

- [x] The normalization factor Q is missing in Equation 13. ✅ 2025-02-04
	🔼 The normalization factor is missing on purposed, indeed the normalization factor needs to only to be applied on the full spectrum in equation 15. Moreover, we applied it on equation 8, because as mention under equation 17 "normalization problem will occur if the full-spectrum normalization factor is simply approximated before its application, because for small values of $r_{\omega}$, $Q_{DB\xi}(\omega)$ will be very low and therefore numerically challenging to normalize.".
	
- [x] Figure 3 caption mentions the dispersion parameter, but the figure is actually about another parameter \delta. ✅ 2025-01-10
	🔼 Thanks, we have corrected and clarify the caption of figure 3

- [x] I am confused about the parameters of the listed cascades in Section 2.3. First of all, the ranges listed seem wrong: 12/16 is clearly greater than 12/256. I presume this is a typo. Also, shouldn't L be larger for smaller k? ✅ 2025-01-30
	🔼 Indeed, we mixed ourself between the length of the cascades and their cutoff. We have fixed this.

- [x] Figure 9 caption says that F_a is "applied to the center of the submerged part." It should be the "unsubmerged part" instead. ✅ 2025-01-10
	🔼 We have corrected this typo.

- [x] It is unclear what Figure 11 c shows. ✅ 2025-01-10
	🔼 We have clarified the caption of each caption to make them more clear 

- [x] h* in Equations 48, 50, and 59 should be negative (following Equation 46). The same goes for unlabeled equations above Equation 53. ✅ 2025-01-10
	🔼 We have corrected this sign error. 

- [x] In the Equation above Equation 56, "sinh(kY)" should be "sinh(ky)." ✅ 2025-01-10
	🔼 We have corrected this case mistake

- [x] The parameters y, t, and k in Equations 59, 60, 61, and 62 are written in an inconsistent order. They should all use the same order. ✅ 2025-01-10
	🔼 We have corrected the order of all parameters in the whole article to make it more consistent.

- [x] This sentence in Appendix A is unclear and needs more explanation: "Note that while the third equation of system 1 is not used here, it can help to deduce the dispersion relation." ✅ 2025-01-10
	🔼 We have removed this sentence and replace it by the whole calculation of dispersion relation to make it more clear. 

- [x] In Equation 71 v_y should be v_z. ✅ 2025-01-10
	🔼 We have corrected this typo.

- [x] In Equation 73, there appears to be an extra term: h(x,t)/dt ✅ 2025-01-10
	🔼 We have removed the excess term.


Other minor issues:

- [x] The abstract ends with the term "fluid to solid algorithm." I would replace it with "fluid to solid coupling algorithm." ✅ 2025-01-10
	🔼 Indeed we added coupling to make the term more coherent with literature.

- [x] The introduction begins with mentioning "scientific computing," but the paper is not about scientific computing at all. I would replace it with "computer graphics." ✅ 2025-01-10
	🔼 We used "computer graphics" which is more appropriate with our article and JCGT.

- [x] I would recommend removing the subsection title 1.1 and converting Section 1.2 (related work)  to Section 2. ✅ 2025-01-10
	🔼 Indeed, putting related work in a dedicated section is more coherent with literature.

- [x] On page 5, "standard gravity" should be "gravitational acceleration." ✅ 2025-01-10
    🔼 We changed "gravitational acceleration" instead of "standard gravity".

- [x] In Section 3.2.3 the description of \rho_a is repeated. ✅ 2025-01-10
	🔼 We have removed the doublon.
	
- [x] In Section 4.4.2, "M has is bow" should be "M has a bow" ✅ 2025-01-10
	🔼 We fixed the typo.
	
- [x] On page 27, "fluid to solid coupling FDM" should be "solid to fluid coupling FDM." ✅ 2025-01-10
	🔼 We fixed the typo.
# Review 2

## General Remarks

- [x] The bibliography is OK, though I am a bit confused as to why Yuksel's PhD thesis is referenced, instead of the related paper: ✅ 2025-01-10

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
	🔼 We used this references instead of the thesis when talking about the wave particles.

- [x] I enjoyed reading this paper. I would have liked it a lot more if it included more detailed descriptions of the algorithms and/or source code. ✅ 2025-02-04
	🔼 We tried to add more algorithm to simplify the implementation for readers.

- [ ] give more detail on the actual implementation: memory layout on the GPU, implementation of the kernels etc. This is especially relevant since performance timing is given in Sec 5 of the paper, but the rest of the paper gives us little idea as to why these number are such as they are. For example, the bottleneck in Fig 14 seems to be geometry and force computation (intersection geometry computation). Why should this be so slow?
	🔼 TODO.

- [x] No quite. As mentioned above, the paper should provide more implementation details, specifically with regard to the GPU computation and data layout, specifically to explain the timing numbers in Fig 14, and why some of them seem a bit heavy (e.g. like geometry processing). the paper also mentions that no serious CPU-side computation is used - it would be interesting to know why (e.g. could the geometry processing (intersection curve), which seems to be a bottleneck according to Fig 14, be offloaded to CPU?) ✅ 2025-02-04
	🔼 The decision to keep all heavy computations on the GPU, including geometry processing, is motivated by minimizing data transfers between CPU and GPU, which can introduce significant latency. While offloading intersection curve computations to the CPU could theoretically balance the workload, it would require frequent memory exchanges, likely negating any performance gain. In addition, we added a comment in section 6 to enforce the fact that this choice of "no serious CPU-side computation" was made to ensure that CPU remains available for other standard tasks.
## Concrete Remarks

Sec 1
=====

1.1
---
- [x] 1st bullet point, (Tex error) here and elsewhere Tessendorf is quoted as ✅ 2025-01-10
"Tessendorf (2004) [Tessendorf 1999]" (i.e. reference link and text do not match)
	🔼 We changed references to make them coherent between text and citation.
Sec 2
=====

- [x] Sec 2.1 - 2.5 are very heavy on hydrodynamics. ✅ 2025-01-31
For example, starting with eq (5) on p6 all bullet points below on JONSWAP spectrum are straight from page 33 of Horvath (there it is eq 28). There is probably no need to copy this here verbatim, rather than giving a cursory explanation of what the terms of (5) are, a derivation into a more computationally ready form would be better.
The same goes for the details of the usual Donelan-Banner spectrum, specifically eqns (7) - (12), could just refer to Sections 6.0.9 - 6.1 of Horvath. The focus instead could be on approximation in eq (17), which is original, and the conclusion eq (18).
	🔼 Thank you for the insightful comment. We agree that the derivations are detailed; however, we believe these sections help simplify the reader's understanding of the underlying hydrodynamic principles and provide clarity for implementation. Moreover, it makes the paper a bit more self-contained.
2.2
---

- [x] Isn't $k$ locally constant (wrt x,z)? Then could just write ✅ 2025-01-29
$$\frac{\partial D_x}{\partial x} = i k_x D_x$$
for the first equation, and similar for the other 4 derivatives. Makes it easier to read and is explicit about computation needed.
	🔼 $k$ is indeed locally constant relative to $x$ and $z$, however, the equation $\frac{\partial D_x}{\partial x} = i k_x D_x$ isn't true, because $k_x$ cannot be factorize from the sum, as it's the index on which the sum is apply. Nonetheless, this suggestion is true when considering individually each terms of the sum. Therefore, we have rewrite this paragraph to show these equality in a more "Fourier-fashion", which is more close of the implementation.
	  

2.5
---
- [x] Second paragraph p 12. It would be helpful to have some details on memory organization for the NxN tiles, computation efficiency on the GPU, etc - especially since quoting performance numbers in Sec 5, Figure 14. ✅ 2025-01-31
	Thank you for the valuable suggestion; however, we believe the current level of detail sufficiently balances technical depth and readability

2.6
---

- [x] Paragraph 1, p 13, awkward phrasing "...tied to the wave vector, preventing from any simplifications to reduce the needed calculations." ✅ 2025-01-10
Maybe ".., preventing any simplifications that could reduce the required calculations."
	🔼 We rephrased this sentence with your suggestions.

- [x] Para 2, p 14 "First, while the velocity decays exponentially, it relies on a logarithmic similar to..." should probably be "..., it relies on a logarithmic function similar to..." ✅ 2025-01-10
	🔼 We added the missing word.

- [x] Same paragraph, "this function decreases slowly (actually with ln(250 + 1) = 5.5)," ✅ 2025-01-10
What is the significance of "250 + 1" here?!
	🔼 The "250 + 1" was to keep the same "form" as the function, but we removed it to avoid confusion 

- [ ] Figure 6, vertical scale should probably be logarithmic to make these graphs more informative. As it is now, three of four graphs are scrunched on top of each other.

- [x] Not sure why the bracket "{" in eq. (28). Also it does not look like eq (28) is quoted in the rest of the paper, so $\alpha$ and $\beta$ could just be given inline. ✅ 2025-01-17
	🔼 We inline the coefficients choice.

Sec 3
=====

3.1
---

3.2.1

- [x] p 17. "The Arc Blanc framework uses the prism approximation proposed by Bajo et al." How? In Bajo et al. paper, the geometry (position & area vector, is stored in texels of the surface textures of the model.) The prisms used there are per texel, so for example the prism height is determined by (average) water height above the projected texel center. How is this done here? ✅ 2025-01-29

Specifically, "The principles of their method are as follows: from each submerged triangle $T^s_i$ of the body, a prism is build up to the water surface; hence, each prism volume can be calculated, and so the full submerged volume vw by adding all of them." This is not exactly correct - their computation is at surface texel granularity level - it is not immediately obvious how this is to be done on triangle basis (e.g. uniform tessellation?)
	🔼 Thank you for your insightful comment. We revised the paragraph to clarify and justify that we use an approximation similar to Bajo et al., but at the triangle level rather than the texel granularity. We add some "formal" details about the calculation.
3.2
---

- [x] Sections 3.2.2 and 3.2.3 details are redundant: the only true geometric difference between the two is that in one case we are considering velocity of water while in the other velocity of air (density and drag coefficient being that of the medium under consideration can be understood from context) ✅ 2025-01-15
	🔼 We have merge the two sections to remove redundancy.

- [x] Also, p19 Paragraph 2 has a typo: the 3rd and 4th bullets are identical ✅ 2025-01-20
	🔼 We have removed the doublon.

3.3
---

- [x] As above, item 3, it is not clear how to do the volume computation. The paper claims it is triangle based, while the quoted source (Bajo et al) uses surface texel based computation. Does the author imply that some sort of uniform triangulation scheme is to be used? If so, then there is also the matter of closing and triangulating the polygons given by the (approximate) cutting of triangles against the waterline described in paragraph 2 of 3.1 on p 17 by referring to Kerner's paper. 
	🔼 As mentioned above, we have made the paragraph on the volume computation more clear. Moreover, we clarified the hypothesis that we have made on the meshes. 


- [x] Figure 9, p 20 mentioning c_i, COG, center of submerged part etc, but these are not labeled in the diagram, which produces unnecessary cognitive load when reading the diagram. Also, can spread the vectors a bit to declutter (dont need to have them bunched up so realistically), likewise v_a and v_w are not collinear in general. Larger arrow tips would help. ✅ 2025-01-31
	🔼 We tried to clarify the caption while keeping information about where to apply the forces. Moreover we change the figure based on your comment to make it more clear.

Sec 4.
=====

4.1
---

- [x] Paragraph 1, suggesting change of notation, e.g. $\delta$ instead of $dx$ for the discretization step. This would make (35) (38) (40) (42) less confusing when first seen (e.g. it's not a differential), or $\Delta{x}, \Delta{y}, \Delta{t}$, but that might be a bit too detailed, e.g. since the grid is regular. ✅ 2025-01-20
	🔼 As suggested, we renamed $dx$ in $\delta$ to make equation less confuse. 

- [x] Eq (36)  probably it is easier to read something like $u = clamp_hi(|v|/v_max, 1)$ and $d(t) = lerp(d0, d_max, u)$ than the given piecewise definition. ✅ 2025-01-20
	🔼 Indeed this formulation is more clear. We replace our piecewise definition with this one.

- [x] Numeric values like the ones in eq 37, which affect stability, might be meaningless if some implementation details of the framework are not been specified (e.g. floats, doubles etc)? ✅ 2025-01-29
	🔼 We have specified that we are using single precision float number.

4.2
---

- [x] A simple diagram showing the relationship between (i,j), (k,l), and (o,p) would make (39) easier to read (e.g. could extend Fig 10 to show this). ✅ 2025-01-20
	🔼 We have added a figure to illustrate the relationship between indices.

4.3 
---

- [x] "The value of c is deduced from dx and dt to validate the CFL as follows"Deduced how? \sqrt(0.49) seems close to \sqrt(0.5) which you would get from Eq (40)? ✅ 2025-01-28
	🔼 We have clarified this sentence to explain that this choice has been made to make sure the equation 40 is true.

4.4
---

- [x] Last paragraph on p 23, typo: "corresponding to the vertices of Z contained into one intersected polygons." should be "...in one of the intersection polygons" ✅ 2025-01-28
	🔼 We have fixed this typo.

4.4.1
-----

- [x] Paragraph 1, typo: "contained into one intersection polygon" should be "contained in one of the intersection polygons" ✅ 2025-01-20
	🔼 We have fixed this typo.

- [x] The reference to (what I assume is) CLRS listed in the References section is incorrectly written. Also CLRS is too general so probably not needed here. ✅ 2025-01-28
	🔼 We removed this ref which makes doublon with the more precise reference of E. Haines (1994) .

- [ ] Stabbing ray approach described might have robustness issues - are those significant enough to cause some form of instability in the simulation?
	🔼 TODO what robustness issues and instability ? 

- [x] Last sentence of the last paragraph of 4.4.1, typo: "technic" ✅ 2025-01-20
	🔼 We have fixed this typo.

- [ ] Also, not explicitly mentioned, but I am guessing that the intersection polygons from sec 3.1 are projected onto xz plane in order to do z-ray stabbing in sec 4.4.1. Could some such projected intersection polygons then be generate (e.g. self intersecting when projected onto zx plane, or inverted - e.g. for turbulent water height and finely tessellated body M)
	🔼 Thanks for your remarks that has given us plenty to think about. The question on the "stability" of the intersection between M and water height can be divide into two questions:
	
- First, does the intersection between M and the water height (the height map) always results in some loop (or empty/singleton set), but not in some open loop or more stranger subset of $\mathbb{R}^3$. This question is non trivial and can be sumarrize with this theorem:
Theorem: Let $M$ be a compact 2-manifold without any border (our mesh) and $H=\set{(x,y,z)\in\mathbb{R}^3| h(x,z)-y=0}$, then $M\cap H$ can only be:
- Empty
- $x\in \mathbb{R}^3$
- $\cup_i c_i$ where $c_i$ are homeomorphic set to the unit circle $S^1$

The proof of this theorem is a bit long and out of scope for this paper, as it required some skills in differential topology, but here is a sketch of a demonstration:
The idea of the proof is to characterize the dimension of the intersection and to prove that the intersection is always compact. As compact set of dimension one in $\mathbb{R}^3$ are homeomorphic to finite union of circle.

First, note that the compactness of the intersection is quite trivial, as by definition $M$ is compact and $H$ is by definition closed, therefore their intersection must be compact. 

Second, for the dimension it's a bit more complex. But we can profit of the [preimage theorem](https://en.wikipedia.org/wiki/Preimage_theorem) which under certain condition gives us a characterization of the dimension of a set. 
Consequently, our objective is to pose the problem in a way we can apply the preimage theorem. 
Let $f:M\rightarrow \mathbb{R}$, $f(x,z,y)\mapsto h(x,z)-y$
Note that $S\cap H$ is equal to $f^{-1}(0)$, moreover by definition of the $h$ and its linearity, $f$ is a smooth map. 
Now we need to prove that $0$ is a regular value of $f$, that is $\forall x\in f^{-1}(0)$, $df_x : T_x M\rightarrow T_0 \mathbb{R}\simeq \mathbb{R}$ is surjective. To throw out this case lets directly assume that $f^{-1}(0)\neq empty set$. Moreover, $df_x(v) = \nabla f \cdot v$
Note that, if $df_x$ is not a zero map, then $df_x$ is surjective (indeed if it's not a zero map $im(df_x)=\mathbb{R}$, because it cannot be the other vector subspace $\set{0}$). Therefore, there can is two cases:
1. $T_x M\subset T_x H$ and then $df_x$ is not the zero map, which corresponds to the intersection is given by a single point.
2. $T_x M$ is not a subset of $T_x H$ and therefore $df_x$ is not the zero map and then surjective.
We can apply the preimage theorem and we have:
$codim(f^{-1}(0)) = dim(\mathbb{\mathbb{R}}) = 1$ 
Moreover, as we are in finite dimension:
$codim(f^{-1}(0)) = dim(M)-dim(f^{-1}(0))$
which ends the demonstration by giving us:
$dim(S\cap H) = 1$
- Second as you mention, does the project on the zx plane cause the intersection polygons to be self intersected. For this lets us simply remarks that if the polygon is simple on the continuous height map, then the projection that alter only the vertical component should gives us also a simple polygon. It won't be the case is instead of an height map we were using more complex parametric surfaces, where two point of the surfaces could be projected of the same point of the xz plane. The keypoint here is the bijection between the xz plane and the height map. 

TODO dois-je ajouter des choses dans l'article ?

- [x] Also, doing ray stabbing on multiple components probably increases chances of bad classification of a point. Could do closed component count (provided the model M is a closed orientable surface to start with, so the intersection polygons have well-defined interior) to speed up the test. ✅ 2025-02-04
	🔼 We didn't face any bad classification at this point, but we might in the future considering using closed component count indeed, thanks for the suggestion.

4.4.2
-----

- [x] Sentence 2, paragraph 1, typo: "By construction of the grid Z, M has is bow oriented on the positive side of the z axis and its starboard on the positive side of the x axis." Should be "..has *its* bow.."? ✅ 2025-01-20
	🔼 We have fixed this typo.

- [x] Also, for landlubbers among us, please clarify "starboard" as "right-hand side when facing the bow" :) ✅ 2025-01-20
	🔼 We added the precision to make the term more clear.

- [x] End of the same paragraph: ✅ 2025-02-04
"Hence, h is made such that from the vertex at position x, the front of the mask is above the free surface and the back below, in a way that is proportional to the speed of M. Moreover, the boat forms a V shape, with its center a bit below the extremity of the side."
I can not visualize this. For example, 
- what is meant here by "front of the mask is above the free surface and the back below"?
- "..the boat forms a V shape.." - does V here mean that the boat is in the shape of the letter "V", or does V denote the shape (object) in question? For example, the sentence before eq (43) says "The function f models the side effect using a shape in V", which suggest the latter, but the next sentence says "The V-shape is obtained from the absolute value of the abscissa" (note the hyphen) which suggest the former.
Can we please have a diagram that shows and explains this geometry configuration clearly - in addition to Fig 11?
	🔼 We have added some explanation and three figures to make clarify the desired shape.
Sec 5
=====

- [ ] Figure 14. XP2 geometry, section 3.1. 4.6 msec for 4153 triangles vertex classification and splitting seems a bit excessive. Same goes for forces computation. This, for example, is why it would be nice to see more implementation details.
	🔼 TODO
	
- [x] Also, an idea: maybe assuming that the intersection shape is more or less the same between two consecutive frames, for low Beaufort state at least, (and for some k steps, where k is small), then recompute the buoyancy/volume based on the previous volume of the submerged shape, correcting for the height difference of the water between the two frames, then on k-th step doing the correct computation? ✅ 2025-02-04
	🔼 Thanks for your suggestion, the project for which this article was made require precise hydrodynamics data at each frame. Nonetheless, your approximation could be interesting with simulation that has low Beaufort state. But it might complexify the implementation on GPU for more polyvalent system.  
# Review 3 

## General Remarks

- [x] Although, the solid->water action simulation is primitive and lacks explanations and obvious improvements: ✅ 2025-02-04
1. The movement of the hulls and how the corresponding translations/rotations of hulls affect the solid->water interaction is not clearly described.
It appears that only the translation part is taken in account.
	🔼We have added some precision about how to handle the rotation of the body for mask calculation.


- [x] 2. Finite difference method used to simulate interactive waves is extremely primitive and is able to simulate vertical displacement of interactive waves only. ✅ 2025-02-04
Tessendorf's eWave based on FFT+iFFT per simulation step is a bit more expensive but produces full 3D displacements of the interactive waves.
	🔼 We appreciate your insightful comment. While we agree that the finite difference method is more primitive and limited to simulating vertical displacements, its simplicity allows for straightforward implementation and efficient parallelization across multiple bodies in the sea. Implementing eWave would indeed be a valuable enhancement to Arc Blanc, and we might consider it for future work.
	
- [x] Injecting displacements into water caused by movement of solid objects, called wave generation in the paper, based on functions representing side and front/back effect, looks absolutely artificial. ✅ 2025-02-04
Instead, a per-gridpoint signed difference in volumes produced by intersections of hull volume and still water volume at current vs previous simulation step 
could be used to generate water displacements based on incompressibility pf water.
	🔼Thank you for the thoughtful suggestion. Using per-gridpoint signed differences based on the incompressibility of water is indeed a more realistic approach and could significantly enhance the accuracy of wave generation. However, we chose our current approximation to prioritize simplicity and straightforward implementation, which aligns better with the real-time constraints and accessibility goals of Arc Blanc. We will certainly consider your suggestion for future enhancements.

- [x] 4. Mask movement and orientation used in paper, so that front of the mask is above water surface and back is below water surface, looks artificial and extremely simplified. ✅ 2025-02-04
A propulsion force acting on hull and causing it to move, in conjunction with proper water->solid interaction from the 1st part of the paper, with its forces and moments, 
will naturally cause hull to raise its bow based on physically correct simulation instead of oversimplified approximation used in the paper.
	🔼Thank you for your valuable proposition. It might be a nice refinement for Arc Blanc framework.


- [x] Overall the paper allows to implement presented technique without much trouble for people that have experience with the topic of the paper, ✅ 2025-02-04
although better explanation of how the forces acting on solid object in water are summed up and used to evolve solid object dynamics would improve it a lot.
Is the sum of the forces applied to center of gravity of the object? Or there are rotational moments?
Are moments of inertia of the solid object taken in account? 
What about the moment of inertia of water body surrounding the object?
Without those explained, this part of the abstract looks like a bit of overstatement:
	🔼We have added details about the way the sum is made and forces applied to a physics solver. 

- [x] One note: deciseconds? Please, use seconds or milliseconds. ✅ 2025-01-17
	🔼 We used seconds, which are more standard.

- [x] The paper lists a ton of references that are not touched in the paper in the sense that the paper does not derive anything from those. ✅ 2025-02-04
For instance, 
1. SPH papers are not related.
2. Wave particles are not related
3. Water wave packets are not related
	🔼 As one the goal of the paper is to describe a complete unified framework for ocean simulation in real time, we think that presenting alternative approach could only benefits to the reader. And it makes the article more self consistent on the subject of ocean simulation.


- [x] In chapter 2.6 the "interpolation degree" term is unclear and a bit misleading, ✅ 2025-02-04
and since the interpolation is based on water body displacements calculated at "slices" with fixed depth, 
I'd suggest term "interpolation slice" and "number of interpolation slices", for instance on Figure 7.
	🔼 Thank you for your suggestion. While we understand that the term "interpolation degree" may be misleading, we prefer to retain it as it aligns with common terminology used in interpolation methods, such as polynomial interpolation.