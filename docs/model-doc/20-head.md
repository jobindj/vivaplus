---
bibliography: [../../viva-refs.bib]
---
# Head

!!! warning "This section of the documentation is under development"
    
    This section is being updated

## Bones

The skull, mandible and teeth were modelled as 1 mm shells, with material model `MAT_RIGID` and properties according to data for cortical bone [@Reilly1975], density 2.e-6, Young's modulus 17.1 GPa, and poisson ratio 0.3.

## Soft tissues

### Skin

The head skin is modelled using 1mm membrane elements (`ELFORM=9`), with material model `MAT_FARBRIC` with stress-strain curves based on [@Manschot1986] (across the tibial direction). Further, Young's modulus for the skin was set to 1 MPa (roughly the slope of the initial part of the non-linear curve) for both material directions and poisson's ratio to 0.49 (assumed close to incompressible). Shear modulus was set to 0.33MPa (based on isotropic assumption). Compressive stresses were eliminated `CSE=1`. The stiffness of the "liner" were set to 1E-6 GPa (to not contribute to the overall stiffness). A rayleigh damping coefficient of 0.05 (recommended according to the LS-DYNA manual) was used. For the density a value of 1E-6 was assumed for the skin.

The eyelids were modelled using 1 mm thick, fully integrated shells, using material model MAT_ELASTIC with parameters; density 1e-6, Young's modulus 2MPa and poisson ratio 0.3.

### Scalp

The scalp was modelled using solid elements with material model `MAT_OGDEN_RUBBER` using material properties based on [@Trotta2019]. For the current implementation the ogden parameters corresponding to the highest strain rate (15-100) was used with ogden material parameters according to; μ=1.48 MPa and α=8.1. A poisson's ratio of 0.4999 was used and density was taken from [@Trotta2020]

### Oral cavity

The oral cavity was modelled using solid elements with material model `MAT_OGDEN_RUBBER`, with material parameters according to [@Engelbrektsson2011]
## Adjustment of mass and inertia

Six discrete mass elements, alinged along the principal axes (crossing at the head CoG), were used to adjust the total mass and principal inertias of the head. Using the sex parameter different masses were assigned for 50F and 50M. The mass and inertia properties were taken from [@Yoganandan2009], with original data from [@Plaga2005].

|  Sex   | Mass [kg] | Ixx [kgmm$^2$] | Iyy [kgmm$^2$] | Izz [kgmm$^2$] | CGx<sup>*</sup> [mm] | CGz<sup>*</sup> [mm] |
|:------:|-----------|--------------|--------------|--------------|-----------|-----------|
| Female | 3.82      | 16955        | 18392        | 12226        | 0.2       | 29.1      |
|  Male  | 4.42      | 21491        | 23323        | 15489        | 1.3       | 26.4      |

<sup>*</sup> Relative to tragion



## References

\bibliography

