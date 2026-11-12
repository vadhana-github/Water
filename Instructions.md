Model Inputs:

Navigate to https://github.com/gromacs/gromacs/blob/main/share/top. Download the gro files spc216.gro; tip4p.gro; tip5p.gro.
Navigate to https://github.com/gromacs/gromacs/blob/main/share/top/oplsaa.ff. Download the tip4p.itp. spc.itp, spce.itp, tip5p.itp
Create topology files for each of the itp files and the corresponding gro files.
Run energy minimisation using the .itp .gro files (tip4p.itp for tip4p.gro; tip5p.itp for tip5p.gro; spc.itp for spc216.gro and spce.itp for spc216.gro) with the following molecular dynamics parameters: steepest descent algorithm (integrator = steep) with a maximum force threshold (emtol = 1000.0 kJ/mol/nm), a step size (emstep = 0.01 nm), and up to 50,000 steps. It employs a Verlet cut-off scheme (cutoff-scheme = Verlet, nstlist = 1), Particle-Mesh Ewald long-range electrostatics (coulombtype = PME), 1.0 nm cut-offs (rcoulomb, rvdw, rlist), and 3D periodic boundary conditions (pbc = xyz).
Run NVT with the minimised structure as input and using Berendsen thermostat for 50 ps at 298.15 K (use coupling constant as 100 times the time step). Run another NVT simulation using the output structure from previous simulation as input and using Nose-Hoover thermostat for 50 ps at 298.15 K (coupling constant is 1 or 2 ps)
Run NPT with Nose-Hoover thermostat (coupling constant is 2 ps) and Parrinello Rahman barostat for 5 ns at 1 bar and 298.15 K (coupling constant is 5 ps). Dump positions, velocities, forces and pressure every 200 steps. This constitutes the production run.
Repeat NVT and NPT simulations using the above protocol for a wide range of temperatures from 15 degrees C to 100 deg C and at 1 bar.
Estimate properties from molecular trajectories in the production runs over the last 3 ns out of the 5 ns total run. Estimate radial distribution function between Oxygen pairs, bulk density, Self diffusion coefficient from mean squared displacement, bulk viscosity using the Green Kubo relations from the off-diagonal elements of the pressure tensor and surface tension from the time-averaged diagonal components of the pressure tensor.
Plot volume, bulk density of liquid water, surface tension, viscosity and self diffusion coefficient at various temperatures and at 1 bar.
Compare with experimental data reported
