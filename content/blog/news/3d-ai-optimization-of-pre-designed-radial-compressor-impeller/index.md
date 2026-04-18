+++
title = "3D AI Optimization of Pre-designed Radial Compressor Impeller"
description = ""
is_news_page = true
type = "blog"
layout = "single-news"
date = 2026-04-09
source_url = "https://spinpous.com/Blog_post1.html"
url = "/blog/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/"
aliases = ["/news/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/", "/news/blog-post1/"]
+++

<h2>3D AI Optimization of a Pre-Designed Radial Compressor Impeller</h2>

<p>With TurboTides + OASIS, our customers are able to use their standard computing resources to drive automated design of turbomachinery. Using OASIS, the user can see improvement in their design in a short amount of time, even with a standard PC. Combined with the Turbotides software, this is the most powerful optimization engine for turbomachinery available. In this document, this optimizer is used to improve a well-designed impeller available in literature.</p>

<p>Most companies do not have access to a high-performance computing setup which allows for the fastest possible CFD computation. This combined with the limitations of other optimizers have limited the use of 3d optimization for most companies. However, by using a smarter optimizer, a designer can come to an improved design in a reasonable amount of time, even with a standard PC workstation. The optimization example presented in this document was completed in 30 hours.</p>

<p>This presents as a very valuable design tool which integrates well with our users current design resources - no additional investment in a HPC setup is necessary.</p>

<h3>3D CFD Impeller Optimization</h3>

<p>The Krain impeller is a previously designed impeller which is referenced in literature as a well-designed backswept Turbocompressor impeller. This geometry was recreated using the coordinate import tool in TurboTides geometry module. [1] First a CFD simulation was conducted in TurboTides at the design point to get the baseline performance characteristics before 3D AI optimization. A mesh sensitivity study was conducted to determine an acceptable mesh for accurate simulation.</p>

<figure class="news-figure news-figure-multi">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image01.jpg" alt="">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image02.gif" alt="">
  <figcaption>Figure 1. Krain impeller in TurboTides (left) and as manufactured (right)</figcaption>
</figure>

<p>For this optimization, 12 total variables were selected, which were the blade angle profile points for hub and shroud, the number of blades, and the tangential stacking at the leading edge.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image03.gif" alt="">
  <figcaption>Figure 2. Blade angle distribution of original Krain impeller</figcaption>
</figure>

<figure class="news-figure">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image04.gif" alt="">
</figure>

<p>The complete parameter list is shown below in Figure 3. A mesh sensitivity study was conducted to determine an acceptable mesh for accurate simulation.</p>

<p class="figure-caption">Figure 3. Complete list of optimization parameters</p>

<p>The objective of maximizing the total-total isentropic efficiency was selected. A constraint was placed on the pressure ratio and flow rate to ensure that the operating condition stays consistent. A constraint was also placed on the lean angle to ensure reasonable geometry. A penalty is applied to any iterations which result in a lean angle greater than 35 degrees or less than -35 degrees.</p>

<p>The CFD used the static pressure outlet boundary condition, with a total-static pressure ratio of 3.7 for both original and optimized impellers, at the design point RPM of 23363. Air was selected as the working fluid with atmospheric inlet conditions.</p>

<h3>Results</h3>

<p>The optimization was run for a total of 40 hours and ran for 291 iterations. the optimum design was reached at iteration 255. The optimizer produced a higher efficiency design as soon as iteration 13! The performance comparison is below:</p>

<p class="table-caption">Table 1. Summary of CFD results for original model compared to optimized model at design point</p>

<div class="news-table-wrap">
<table>
  <tr><th>Performance parameters</th><th>Original model</th><th>Optimized model</th></tr>
  <tr><td>Flow rate (kg/s)</td><td>4.71</td><td>4.76</td></tr>
  <tr><td>T-T Pressure ratio</td><td>4.75</td><td>4.75</td></tr>
  <tr><td>T-S Pressure ratio</td><td>3.7</td><td>3.7</td></tr>
  <tr><td>T-T Isentropic efficiency</td><td>87.14%</td><td>87.93%</td></tr>
</table>
</div>

<p>The blade angle and flow path curve distributions were modified during the optimization, these plots are shown below. The solid lines represent the optimized design, and the shaded lines represent the original design.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image05.gif" alt="">
  <figcaption>Figure 4. Blade angle plot for optimized and original impellers</figcaption>
</figure>

<p>The 3D geometry before and after optimization is shown below, where the original impeller is red, and the optimized impeller is grey.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image06.gif" alt="">
  <figcaption>Figure 5. 3D geometry of original Krain (red) and optimized impeller (grey)</figcaption>
</figure>

<p>The Krain impeller was already a well-designed impeller. However, the TurboTides-OASIS 3D optimization tool has increased efficiency by .8%, demonstrating the power of this tool.A complete performance map at the design point RPM was created using the TurboTides CFD module for both the original and optimized designs.</p>

<figure class="news-figure news-figure-multi">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image07.gif" alt="">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image08.gif" alt="">
  <figcaption>Figure 6. Original design performance map (solid line) vs optimized design performance map (dotted line)</figcaption>
</figure>

<p>The increase of T-T efficiency was accompanied by an increase in the choke point mass flow from 4.92 to 5.17 kg/s. The surge margin was also improved, the optimized design is able to reach a lower mass flow rate than the original design.</p>

<h3>FEA Analysis</h3>

<p>Static structural FEA simulations were carried out in the Turbotides integrated FEA module on both the original and optimized designs to observe how the change in geometry effected the max Von Mises stress. An improvement in efficiency is only useful if the impeller remains structurally sound. As shown below in Figures 7 and 8, the maximum von Mises stress for the original design is 2.19x10^9 Pa, for the optimized design, the max von Mises stress has been reduced to 2.06x10^9 Pa.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image09.gif" alt="">
  <figcaption>Figure 7. Von mises stress contour for original design</figcaption>
</figure>

<figure class="news-figure">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image10.gif" alt="">
  <figcaption>Figure 8. Von mises stress contour for original design</figcaption>
</figure>

<h3>Analysis</h3>

<p>The below figures (representing the static pressure on the blade) show that the original design has a larger region of reversed blade loading, especially near the shroud.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image11.gif" alt="">
  <figcaption>Figure 9. Blade loading plot at 90% span before optimization</figcaption>
</figure>

<figure class="news-figure">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image12.gif" alt="">
  <figcaption>Figure 10. Blade loading plot at 90% span after optimization</figcaption>
</figure>

<p>Relative velocity contours at the 90% span can be used to compare the flow characteristics near the LE. The below Figure 11 shows the relative velocity contour near the LE for the original design, the peak velocity is seen on the suction side of the blade, corresponding with negative incidence. Figure 12 shows the relative velocity contour for the optimized design, showing that the size of the region with high velocity on the pressure side of the blade has been reduced. The local acceleration and deceleration of the flow on the pressure side can cause flow separation downstream.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image13.gif" alt="">
  <figcaption>Figure 11. Relative velocity magnitude contours at 90% span before optimization</figcaption>
</figure>

<figure class="news-figure">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image14.gif" alt="">
  <figcaption>Figure 12. Relative velocity magnitude contours at 90% span after optimization</figcaption>
</figure>

<p>At the design point operating condition, relative meridonial velocity contours at the 90% span show the original design has lower throughflow velocity flow near the shroud, midway between the inlet and outlet. This blockage effect can be seen in the below figures.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image15.gif" alt="">
  <figcaption>Figure 13. Relative meridional velocity contours at 90% span before optimization</figcaption>
</figure>

<figure class="news-figure">
  <img src="/img/news/spinpo/3d-ai-optimization-of-pre-designed-radial-compressor-impeller/image16.gif" alt="">
  <figcaption>Figure 14. Relative meridional velocity contours at 90% span after optimization</figcaption>
</figure>

<h3>Conclusions</h3>

<p>The TurboTides - OASIS integration saves time in the design process by allowing engineers to automate the process of making iterative design adjustments. This allows engineers to use their time more efficiently. This robust 3D optimization engine only offered in the TurboTides software can maximize efficiency or any other objective, while accounting for critical metrics like operating conditions and convergence. The user can optimize on a full performance map or a single operating point.</p>

<p>For the design in this case study, the design point efficiency was improved by nearly .8%. The operating range of the machine was also expanded, improving both the choke and surge margins. . While making these improvements, the maximum von mises stress was reduced as well. Considering that this is an impeller from literature which was already well-designed, this is a significant improvement</p>

<p>Please <a href="/contact/">contact us</a> if you have any questions or would like to schedule a live demonstration.</p>

<p>[1] Preliminary impeller geometry from: Krain H, Hoffmann W . Verification of an Impeller Design by Laser Measurements and 3D-Viscous Flow Calculations. American Society of Mechanical Engineers, 1989.</p>
