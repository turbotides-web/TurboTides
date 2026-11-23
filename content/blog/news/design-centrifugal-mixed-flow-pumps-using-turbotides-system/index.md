+++
title = "Design Centrifugal /Mixed Flow Pumps Using TurboTides System"
description = ""
is_news_page = true
type = "blog"
layout = "single-news"
date = 2026-04-10
source_url = "https://spinpous.com/Blog_post2.html"
url = "/blog/design-centrifugal-mixed-flow-pumps-using-turbotides-system/"
aliases = ["/news/design-centrifugal-mixed-flow-pumps-using-turbotides-system/", "/news/blog-post2/"]
+++

<h3>Objective / Background</h3>

<p>The objective of this study is to demonstrate the TurboTides software capability to create a new radial pump design, predict performance map, generate the 3D geometry, and predict hydrodynamics and mechanical performance using built-in 3D CFD and FEA modules.</p>

<p>TurboTides is an integrated design system that allows designers to conduct turbomachinery design on a single platform. The system supports design and analysis of axial, radial and mixed compressors, turbines, pumps, and fans. This powerful program distinguishes itself from its peers with unique features such as calibrated 1D models through data reduction, easy CAD import and parameterization, optimization engine that can invoke any solvers in TurboTides, and embedded database that facilitates smooth interaction and design data storage in the integrated design process.</p>

<p>Switching to TurboTides can greatly reduce the time of turbomachinery development cycle, improve the quality of the end product, and save the future project development time by organizing existing design/experience in the TT software efficiently.</p>

<p>In this case study, we created the preliminary design using the design wizard in 1D meanline module at first, and generated the full 3D flow path and impeller in the geometry module. The pump performance was predicted in both 1D meanline level and full 3D CFD level. Mechanical /structure performance were analyzed using FEA modules. After comparisons of the two designs completed by using different design options in TurboTides. To demonstrate the powerfulness of TurboTides' data reduction function, we used the CFD results from one design to calibrate the 1D meanline model and then use it to predict the performance of the other design. The small difference between the full CFD simulation of this design and the 1D prediction from calibrated model demonstrated the value of this function to help designer to quickly evaluate the performance of modified design without using time consuming CFD simulations. The calibrated model was also used to provide a useful prediction at operating conditions outside the CFD map.</p>

<h3>1D Meanline Design</h3>

<p>Users may start a new design using 1D design wizard in TurboTides. After inputs of the fluid definition, operating condition, and stage layout, TurboTides runs 1D solver to define a preliminary design. A preliminary design with the below operating conditions was generated with impeller, vaneless diffuser, and volute.</p>

<p>Operating conditions: Mass flow rate: 50 kg/s</p>

<p>Inlet Temp: 288K</p>

<p>Inlet Pressure: 101 kPa</p>

<p>RPM: 2900</p>

<p>T-T isentropic head: 100 m</p>

<p>The 1D pump design wizard in TurboTides has two modes described below.</p>

<h3>Conventional Design Mode</h3>

<p>Based on the user inputs of operating conditions and design targets (flow rate, head and cavitation requirement), preliminary sizing are performed to determine the key geometric parameters of the impeller and other components. The performance of the pump is predicted by using physics based meanline/1D models (deviation model, loss model, etc.). Those geometric parameters are adjusted and iterated until all design targets achieved with the best performance possible.</p>

<p>In this standard design mode, the solver uses well-tested and accredited correlations in the industry to predict the loss coefficient, deviation, and blockage at the operating conditions. Users can choose different correlation/model options and rules for sizing provided in TurboTides as shown in Figure 1 below. These models can be easily customized by users too. The parasitic losses can be modeled by adding a front or rear leakage path to the model.</p>

<p>After the preliminary sizing, users can apply desired geometric parameters manually or modify the design rule options from default value or impose constraints if necessary. This includes setting the inlet or outlet radius or width to a specific value, setting the LE or TE blade thickness, number of blades etc. After these are applied, users may create revised designs.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image01.gif" alt="">
  <figcaption>Figure 1. Impeller configuration window for standard design mode</figcaption>
</figure>

<h3>Fast Design Mode</h3>

<p>In the fast design mode, the relevant efficiency of the pump is directly input by users to size the machine without involving the calculation of the deviation model and loss model. In this mode, although the user inputs the efficiency, a preliminary prediction is provided based on proven empirical correlations with specific speed. These correlations predict the hydraulic, volumetric, mechanical, parasitic loss, and motor efficiency based on the specific speed of the machine calculated from the users' operating conditions. For engineers who prefer similar design approaches, TurboTides offered this option.</p>

<h3>Comparing Designs Generated Using Conventional and Fast Design Modes</h3>

<p>Two designs were created for the given operating condition using both the conventional and fast design modes. Figure 2 below shows some comparison of the geometry.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image02.gif" alt="">
  <figcaption>Figure 2. Impeller meridional view for fast design mode (solid line) and standard design mode (shaded line)</figcaption>
</figure>

<p>Overall, the two design modes provide a similar geometry for this set of operating conditions. Table 1 below shows a comparison of the predicted performance for both designs generated in fast design mode and standard design mode. There are differences in the geometry and predicted performance, due to the different calculation methods.</p>

<p class="table-caption">Table 1. Predicted parameters at design point operating condition</p>

<div class="news-table-wrap">
<table>
  <tr><td></td><td>Standard design mode</td><td>Fast design mode</td></tr>
  <tr><td>Specific speed (non-dimensional)</td><td>0.38</td><td>0.38</td></tr>
  <tr><td>Specific diameter</td><td>7.02</td><td>7.19</td></tr>
  <tr><td>NPSHr</td><td>6.43</td><td>8.48</td></tr>
  <tr><td>NPSHa</td><td>10.33</td><td>10.33</td></tr>
  <tr><td>T-T efficiency</td><td>82.50%</td><td>79.50%</td></tr>
  <tr><td>T-S efficiency</td><td>80.20%</td><td>77.10%</td></tr>
  <tr><td>Parasitic power loss</td><td>4683
  W</td><td>4049
  W</td></tr>
  <tr><td>Power input</td><td>59883
  W</td><td>61668
  W</td></tr>
</table>
</div>

<p>The lower efficiency of the design from fast design mode is because the mechanical loss and losses in the motor have been included in the overall efficiency calculation from the correlations used. In contrast, the standard design mode calculation does not include these losses in by default, user has to add these losses manually.</p>

<h3>TurboTides 1D Analysis Mode</h3>

<p>The TurboTides 1D Analysis mode was then used to predict the pump performance at different operation conditions In the analysis mode, users can choose most sophisticated meanline models for pumps available. They are customizable, and may include axial thrust modeling, interstage modeling, cavitation modeling and structural modeling. The analysis mode allows the user to change geometry parameters and see their effect on the performance prediction. Custom parameters and functions can be defined and graphed by the user. The analysis mode includes a multi-point analysis tool that allows for performance maps generation based on RPM, inlet pressure, or IGV angle. The performance map for this design is shown in Figure 3. Figure 4 shows the prediction of axial thrust of these designs.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image03.gif" alt="">
  <figcaption>Figure 3. Performance maps produced in TurboTides 1D Analysis Mode (for the fast-mode design).</figcaption>
</figure>

<figure class="news-figure">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image04.gif" alt="">
  <figcaption>Figure 4: Axial thrust prediction from TurboTides 1D Analysis mode.</figcaption>
</figure>

<h3>Blade Generation and 3D Geometry Modeling</h3>

<figure class="news-figure news-figure-multi">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image05.gif" alt="">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image06.gif" alt="">
  <figcaption>Figure 5: Flow path curves and 3D model in TurboTides Geometry Module</figcaption>
</figure>

<p>The 3D model is created automatically based on the key geometry determined in 1D module and following certain rules (user controllable) when transferring the design to the geometry module. TurboTides uses a fast and robust geometry engine for easy, fast modification of geometry. The geometry module can create about any turbomachinery components engineers typically use, including impellers, diffusers, volutes, continuous crossovers, return channels, guide vanes, inlet chambers, pipe diffusers, and others.</p>

<p>The geometry module provides a rich set of real-time geometry editing features for almost every type of turbomachinery component. These include a wide range of volute editing capabilities, customizable exit pipe, cross-sections, tongue fillets, etc.. The module supports different diffuser airfoil profiles which can be selected and customized by the user. Like the rest of the tools in TurboTides, this module is seamlessly integrated with the 1D, 3D CFD, FEA, or Cycle modeling modules, and external CFD/FEA tools for instant geometry transfer. For this case study, the model was not modified before moving to CFD, to demonstrate the accuracy of the 1d design mode.</p>

<h3>CFD Simulations</h3>

<p>A performance map for the above design was constructed using the TurboTides built-in CFD module. These simulations are conducted to predict how the pump would operate at different flow rates and speeds. Although TurboTides has a full-featured CFD tool with automatic meshing with secondary flow paths, parallel processing, robust features and post-processing, we have options for interfacing with external CFD tools like CFX/Fluent, Star CCM, FineTurbo, etc.. For this example, the fast design mode case was run in CFD. The below Figures 6 and 7 show the CFD predictions of performance of the fast design mode design (represented by a solid red line) next to the predictions from the 1D Analysis mode (dashed red lines). The CFD was conducted using water as the working fluid, atmospheric inlet conditions, with the SST turbulence model, while modeling cavitation using the integrated Rayleigh-Plesset model. As the 1D model included the predictions of motor, parasitic, and mechanical losses, these loss sources were removed from the 1D prediction to give a more accurate comparison.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image07.gif" alt="">
  <figcaption>Figure 6. Mass flow rate vs. T-T isen. head performance map (solid red represents CFD, dotted red line represents 1D)</figcaption>
</figure>

<figure class="news-figure">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image08.gif" alt="">
  <figcaption>Figure 7. Mass flow rate vs. T-T isen. efficiency performance map(solid red represents CFD, dotted red line represents 1D)</figcaption>
</figure>

<p>The performance map plots in Figures 6 and 7 show the 1D prediction from TurboTides analysis mode matches closely with the 3D CFD prediction of performance.</p>

<h3>1D Model Calibration and Data Reduction</h3>

<p>One of the most useful features is the advanced Data Reduction. The data reduction function calibrates the loss coefficient, deviation, and blockage coefficients in 1D, after being provided real test data or CFD results. The calibrated 1D meanline model then can be used to accurately predicts performance for additional operation conditions, with different fluids or even modified geometries during the design iterations. This feature will greatly shorten developing time and accelerate the design process. It may also help to lower the costs by reducing expensive tests or/and high fidelity CFD needed.</p>

<p>In this case study, after calibrating the 1D model using the CFD data, the 1D analysis mode can be used to make accurate predictions of this machine at conditions outside of the operating conditions in the original performance map, with a different working fluid, or with a modified geometry. The below figure shows the 1D model prediction of performance after calibrating the 1D model with the CFD results. The test data and calibrated analysis mode predictions are almost identical, indicating that the 1D model was then ready to use to accurately predict performance. After this, modifications can then be made to the operating conditions, working fluid, RPM, inlet conditions, and the performance prediction will remain accurate and useful.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image09.gif" alt="">
  <figcaption>Figure 8. 1D model prediction after Data Reduction using CFD data</figcaption>
</figure>

<p>To demonstrate the power of using a calibrated 1D model, the 1D analysis mode was then used to predict performance at RPMs above and below the design point RPM, this is shown below in Figure 9.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image10.gif" alt="">
  <figcaption>Figure 9. Calibrated model prediction at RPMs outside original CFD data</figcaption>
</figure>

<p>We also completed full 3D CFD simulation of the same speedlines and compared with predictions from calibrated 1D model in Figure 10. The difference between 1D and 3D CFD performance maps are very small, which means user can use calibrated meanline model to quickly generate full performance map without losing much accuracy.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image11.gif" alt="">
  <figcaption>Figure 10. Calibrated model prediciton vs. CFD results</figcaption>
</figure>

<p>Furthermore, the user can make changes to the model's geometry and the calibrated model will stay accurate, within certain bounds. This means the user can make use of the calibrated1D model to quickly and accurately assess the effect of proposed changes to the design on the performance map.</p>

<h3>Mechanical Performance Analysis Using FEA</h3>

<p>The FEA module within TurboTides functions similarly to the CFD module, with automatic meshing and simulation setup. The user can set up a static, thermal, or modal analysis within seconds. The materials, boundary conditions, loads, mechanical geometry are all editable. The fluid loads from FEA are automatically applied to the model. The FEA analyses can be done for a single blade segment or an entire impeller. The user can customize the materials, operating conditions, loads, initial conditions, and constraints. The full featured FEA module also includes random vibration analysis, transient heat transfer, hot-cold conversion, dynamic analysis (including transient structural, thermal, harmonic analyses), among other tools. After the simulation finishes, the user has post processing options to view contours and plots showing the displacement, mode shapes, stresses, temperatures, etc.. For this analysis, the modal and static structural analyses were conducted. The below figures show a contour of the total deformation and the von Mises stress contour for the impeller for the static analysis.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image12.gif" alt="">
  <figcaption>Figure 11. Total deformation contour for impeller (fast design mode design)</figcaption>
</figure>

<figure class="news-figure">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image13.gif" alt="">
  <figcaption>Figure 12. von Mises stress contour for impeller (fast design mode design)</figcaption>
</figure>

<p>The below figure shows the deformation of the first mode shape.</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image14.gif" alt="">
  <figcaption>Figure 13. First mode shape displacement contour (fast design mode design)</figcaption>
</figure>

<p>For the modal analysis, TurboTides outputs Campbell and interference diagrams, which can be used to find which modes are of highest concern during operation. For this case, the first natural frequency is at a frequency far above the possible excitation frequencies this machine could experience, so during normal operation there should be no resonance. This is shown below in the Campbell diagram for this case:</p>

<figure class="news-figure">
  <img src="/img/news/spinpo/design-centrifugal-mixed-flow-pumps-using-turbotides-system/image15.gif" alt="">
  <figcaption>Figure 14. Campbell diagram from modal analysis in TurboTides FEA module</figcaption>
</figure>

<h3>Conclusions</h3>

<p>Through this case study, we take a glance of the powerfulness of TurboTides as an efficient and effective pump design system covering workflow from system analysis to 1D preliminary design, 3D geometry generation, automatic meshing, 3D CFD and FEA structural analysis. Although this case study is only a demonstration of a new design from scratch, TurboTides also offers extensive functions and features for the reuse and redesign optimization of the existing designs. TurboTides accomplishes this through a unique combination of parametrized CAD import, Data Reduction, embedded database management, and multidisciplinary design optimization, all within a single, fully integrated package. This software provides an entire suite of tools engineers need to develop a turbomachine, from scratch to a completed 3D CAD model with dedicated flow and mechanical simulations/performance prediction.</p>

<p>We at Spinpo are eager to help you meet your design goals. Spinpo provides the best customer service in this industry - offering same day or real time technical support for all our customers.</p>

<p>Please <a href="/contact/">contact us</a> if you have any questions or would like to schedule a live demonstration.</p>
