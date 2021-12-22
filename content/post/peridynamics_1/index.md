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
The classical molecular dynamics depends on the locality of material points. In peridynamics theory, each material points is identified by is coordinates <b>_x<sub>k</sub>_</b> and is associated with its incremental volume _V<sub>k</sub>_ and the mass density $\rho$(<b>_x<sub>k</sub>_</b>). Each material point may also be subjected to load, displacement, and velocity which lead to motion and deformation. In a deformaed state, a material point, <b>_x<sub>k</sub>_</b>, experiences a displacement, <b>_u<sub>k</sub>_</b>, and its location is described by its position vector, <b>_y<sub>k</sub>_</b>. The displacement and body load vector are represented as <b>_u<sub>k</sub>_</b>(<b>_x<sub>k</sub>_</b>, t) and <b>_b<sub>k</sub>_</b>(<b>_x<sub>k</sub>_</b>, t).     
In the peridynamics theory, the interactions of the material point <b>_x<sub>k</sub>_</b> with the others is assumed to vanish beyond a local range, $\delta$, called horizon. The material points within the distance $\delta$ is called the family of <b>_x<sub>k</sub>_</b>, denoted as H<sub><b>_x<sub>k</sub>_</b></sub>. In the other word, it is assumed that a material point only interacts with it own family. The interactions between material points are prescribed as the micropotential that depends on the deformation and the constitutive properties of the material. 