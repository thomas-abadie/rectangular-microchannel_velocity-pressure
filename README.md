# Velocity field, wall shear stress (WSS) and pressure drop in a rectangular microchannel

This is a Jupyter notebook to calculate the velocity profile, wall shear stress and pressure drop in a rectangular microchannel using the analytical solution by [[1]](#1). 
The values used in the example are based on the experiments presented in [[2]](#2).

**Flow field in a rectangular channel**

Given a rectangular channel with a cross section $2W \times 2H = 1 \ {\rm mm} \times 0.1 \ {\rm mm}$, let us note the aspect ratio $\alpha = 2W / 2H$.
The velocity field can be written ([[1]](#1),[[3]](#3),[[4]](#4)): 

$$  u(x,y) = - \frac{16 c_1 W^2}{\pi^3} \displaystyle\sum_{n=0}^{\infty} \frac{\left(-1\right)^n}{(2n + 1)^3} \left( 1 - \frac{{\rm cosh} \left(\frac{\left(2n+1\right) \pi y}{2W} \right)}{{\rm cosh} \left(\frac{\left(2n+1\right) \pi H}{2W}  \right)}\right) cos \left(\frac{\left(2n + 1 \right) \pi x }{2W} \right) \ . $$

$c_1$ is written:

$$ c_1 = - 3 \frac{u_m}{W^2}  \frac{1}{1 - \frac{192}{\pi^5} \frac{W}{H}\displaystyle\sum_{n=0}^{\infty} \frac{1}{\left(2n + 1\right)^5} {\rm tanh} \left(\frac{\left(2n + 1\right) \pi H}{2 W} \right)}\ , $$

where $u_m$ is the average fluid velocity $u_m = Q/\left(2W \times 2H \right)$.


**Wall shear stress**

At the bottom wall of the channel, the wall shear stress (WSS) is written for y=-H:

$$
\mu \frac{\partial u(x,y)}{\partial y} = - \mu \frac{16 c_1 W^2}{\pi^3} \displaystyle\sum_{n=0}^{\infty} \frac{\left(-1\right)^n}{(2n + 1)^3} \left( \frac{\left(2n+1\right)}{2W} \frac{{\rm sinh} \left(\frac{\left(2n+1\right) \pi H}{2W} \right)}{{\rm cosh} \left(\frac{\left(2n+1\right) \pi H}{2W}  \right)}\right) cos \left(\frac{\left(2n + 1 \right) \pi x }{2W} \right) \ .
$$


**Pressure drop and pressure distribution**

The absolute pressure in the channel is of interest to exmine the pressure exerted on the cells in the microfluidic organ-on-chip platform used in [[2]](#2). 
The pressure at the outlet of the channel, assuming laminar flow and negligible fitting losses, can be written as the sum of atmospheric pressure, the hydrostatic pressure from the outlet tubing and the frition losses in the outlet tubing:

$$
P_{out} = P_{atm} + \rho g h + \frac{\mu L Q}{32 \pi D^4}
$$

where $P_{atm}$ is the atmospheric pressure, $\rho$ and $\mu$ are the density and dynamic viscosity of the fluid, $h$ is the height of the outlet tubing, $Q$ is the flow rate and $D$ is the diameter of the outlet tubing.

Given the very low flow rates, the friction pressure drop is negligible ($< 1 {\rm Pa}$) when compared to the atmospheric pressure (this might change with the very viscous fluids).

When the outlet tubing is raised 40 cm above the microfluidic channel, the outlet pressure is $P_{out} - P_{atm} = 3924 {\rm Pa}$.

The pressure drop along the channel can be expressed ([[1]](#1),[[4]](#4)):

$$
\frac{dp}{dz} = \frac{\lambda \rho u_m^2}{2 D_h}
$$

where $D_h$ is the hydraulic diameter and $\lambda$ depends on the aspect ratio of the channel:

$$
 \lambda = \frac{96}{Re} \left(1 - 1.3553 \alpha^{-1} + 1.9467 \alpha^{-2} - 1.7012 \alpha^{-3} + 0.9564 \alpha^{-4} - 0.2537 \alpha^{-5}  \right) \ .
$$

## References
<a id="1">[1]</a> 
Shah, R. K. and London. A. L. (1978).
Laminar Flow Forced Convection in Ducts: A Source Book for Compact Heat Exchanger Analytical Data.
Academic Press.

<a id="2">[2]</a> 
Bathrinarayanan, P. V., Abadie, T., Perez Esteban, P., Vigolo, D., Simmons, M. J. H. and Grover, L. M. (2025). 
Elevated hydrostatic pressure acts via piezo-1 to destabilise VE-cadherin junctions: an endothelium-on-chip study.
bioRxiv, doi: [10.1101/2025.03.27.645710](http://biorxiv.org/content/early/2025/04/01/2025.03.27.645710.abstract)

<a id="3">[3]</a> 
Abadie, T., Xuereb, C., Legendre, D. and Aubin, J. (2013).
Mixing and recirculation characteristics of gas–liquid Taylor flow in microreactors.
Chemical Engineering Research and Design, 91, 2225-2234, doi: [10.1016/j.cherd.2013.03.003](https://doi.org/10.1016/j.cherd.2013.03.003)

<a id="4">[4]</a> 
Abadie, T. (2013).
Hydrodynamics of gas-liquid Taylor flow in microchannels.
PhD thesis, Institut National Polytechnique de Toulouse, [link](https://theses.hal.science/tel-04298642v1/file/abadie.pdf)
