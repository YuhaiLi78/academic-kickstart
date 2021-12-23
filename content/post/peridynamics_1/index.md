---
title: Peridynamics Study Notes 1
summary: Peridynamics basics
date: "2021-12-22T00:00:00Z"

reading_time: false  # Show estimated reading time?
share: false  # Show social sharing links?
profile: false  # Show author profile?
comments: false  # Show comments?

# Optional header image (relative to `static/img/` folder).
header:
  caption: ""
  image: "Peridynamics.jpg"
---

# Basic
The classical molecular dynamics depends on the locality of material points. In peridynamics theory, each material points is identified by is coordinates <b><i>x<sub>k</sub></i></b> and is associated with its incremental volume <i>V<sub>k</sub></i> and the mass density &rho;(<b><i>x<sub>k</sub></i></b>). Each material point may also be subjected to load, displacement, and velocity which lead to motion and deformation. In a deformaed state, a material point, <b><i>x<sub>k</sub></i></b>, experiences a displacement, <b><i>u<sub>k</sub></i></b>, and its location is described by its position vector, <b><i>y<sub>k</sub></i></b>. The displacement and body load vector are represented as <b><i>u<sub>k</sub><i></b>(<b><i>x<sub>k</sub></i></b>, t) and <b><i>b<sub>k</sub></i></b>(<b><i>x<sub>k</sub></i></b>, t).    
     
In the peridynamics theory, the interactions of the material point <b><i>x<sub>k</sub></i></b> with the others is assumed to vanish beyond a local range, &delta;, called horizon. The material points within the distance &delta; is called the family of <b><i>x<sub>k</sub></i></b>, denoted as H<sub><b><i>x<sub>k</sub></i></b></sub>. In the other word, it is assumed that a material point only interacts with it own family. The interactions between material points are prescribed as the micropotential that depends on the deformation and the constitutive properties of the material.    
    
# Deformation
The deformation of a material point, <b><i>x</i></b><sub>k</sub> is influenced by the collective deformations of the other points. In a deformed state, the relative position vector, (<b><i>x</i></b><sub>k</sub> - <b><i>x</i></b><sub>j</sub>) prior to deformation became (<b><i>y</i></b><sub>k</sub> - <b><i>y</i></b><sub>j</sub>) after deformation. The stretch between two points <b><i>x</i></b><sub>k</sub> and <b><i>x</i></b><sub>j</sub> is defined as:    
<math>
s<sub>(k)(j)</sub> = (|<b>y</b><sub>(j)</sub> - <b>y</b><sub>(k)</sub>| - |<b>x</b><sub>(j)</sub> - <b>x</b><sub>(k)</sub>|)<over>(|<b>x</b><sub>(j)</sub> - <b>x</b><sub>(k)</sub>|)
</math>

The displacement vectors of a material point <b>x</b><sub>(k)</sub> can be stored in a vector:    
<u>Y</u>(<b>x</b><sub>(k)</sub>, t) = 
<math>
    <mrow>
    <mo> { </mo>
    <mtable>
        <mtr> <mn><b>y</b><sub>(1)</sub> - <mn><b>y</b><sub>(k)</sub></mn> </mtr>
        <mtr> <mn><b>y</b><sub>(2)</sub> - <mn><b>y</b><sub>(k)</sub></mn> </mtr>
        <mtr> <mn>...</mn> </mtr>
        <mtr> <mn><b>y</b><sub>(n)</sub> - <mn><b>y</b><sub>(k)</sub></mn> </mtr>
    </mtable>
   <mo> } </mo>
</mrow>
</math>