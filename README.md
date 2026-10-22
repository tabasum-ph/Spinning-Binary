# Conservative binary motion with misaligned spins

An interactive illustration of eccentric binary motion, separating Newtonian motion, post-Newtonian (PN) orbital corrections, spin–orbit coupling, and spin–spin interactions through conservative 2PN order.

The purpose is to understand what each Hamiltonian contribution changes: periastron advance, orbital-plane precession, spin precession, and conserved quantities. This is an illustration of established dynamics, not a new analytical solution.

## Open the animation

[Open the interactive animation](./index.html)

For the shared repository, upload `binary-contributions.html` as `index.html` beside this README. The link runs the animation when viewed on the published website; on GitHub's repository page it opens the file view. Use the repository's published website address to share the running animation.

Alternatively, download `index.html` and open it in a modern browser. No Python, LaTeX, or numerical data download is required: the motion data and simulation code are embedded in the page.

## Controls

- Select a **Hamiltonian case** and press **Play**.
- Drag the picture to rotate it, or choose the top or edge camera view.
- Move the time slider to inspect a particular state.
- Choose **one, five, or ten radial cycles**.
- Select the **canonical** or **position–velocity** shaded plane.
- Read the live diagnostics below the picture and the detailed setup panel.

One radial cycle means a periastron-to-periastron interval: from one minimum of separation to the next. It does not mean that the full spatial orbit or spin configuration returns to its initial state. Ten cycles make accumulated precession easier to see; nonplanarity does not require waiting ten cycles.

## Seven cases

| Case | Hamiltonian contributions |
| --- | --- |
| 1 | Newtonian orbital motion |
| 2 | Newtonian + 1PN orbital correction |
| 3 | Orbital terms through 2PN |
| 4 | Newtonian + 1PN orbital + leading 1.5PN spin–orbit coupling |
| 5 | Case 4 + 2PN orbital correction |
| 6 | Case 5 + leading mutual spin–spin interaction |
| 7 | Full conservative 2PN: case 6 + both black-hole spin-induced quadrupole terms |

Cases 1–3 have all spin couplings disabled. Their spin arrows are passive, fixed reference vectors, and their orbital motion remains planar. Cases 4–7 evolve the spins with the selected interactions. Case 6 deliberately omits self-spin terms to isolate their contribution; it is not the full 2PN black-hole model.

All cases have the same initial canonical positions, momenta, and spins. They do not have identical initial velocities, energies, or relativistic eccentricities. Switching cases preserves fractional progress through the selected cycle count, not the same elapsed physical time.

## Initial conditions and spin misalignment

Let **J₀ = r₀ × p₀** be the initial canonical orbital angular momentum. The initial x–y plane is perpendicular to J₀, and +z points along J₀. Tilt θ is measured from +z; azimuth φ is measured from +x toward +y.

| Parameter | Body 1 | Body 2 |
| --- | --- | --- |
| Mass mₐ/M | 0.6 | 0.4 |
| Dimensionless spin χₐ | 0.8 | 0.7 |
| Spin magnitude in units GM²/c | 0.288 | 0.112 |
| Initial tilt θₐ | 60° | 110° |
| Initial azimuth φₐ | 30° | 135° |

Here M = m₁ + m₂ and χₐ = c|Sₐ|/(Gmₐ²).

The misalignment criterion is

**cos θₐ = (Sₐ · J₀)/(|Sₐ| |J₀|), with 0° < θₐ < 180°.**

Equivalently, Sₐ × J₀ ≠ 0. Both spins satisfy this condition. The initial vectors also satisfy **J₀ · (S₁ × S₂) ≠ 0**, so they are noncoplanar. Noncoplanarity is an additional property of this setup, not a requirement for misalignment.

In units G = c = M = 1, the Newtonian reference parameters are a = 40 and e = 0.35, with

- r₀ = (26, 0, 0);
- p₀ = (0, 0.24√(1.35/26), 0).

The orbit is **eccentric**, not quasi-circular. The value e = 0.35 specifies the Newtonian initial-condition prescription; it is not a common relativistic eccentricity for every case. There is no radiation reaction or inspiral driven by energy loss.

## Geometry and conserved quantities

The orbital angular momentum is **J = r × p**, and the total angular momentum is **J_tot = J + S₁ + S₂**. Spin–orbit coupling generally makes momentum p and velocity ṙ nonparallel. Consequently, the plane normal to r × p differs from the plane normal to r × ṙ. The plane selector distinguishes them; the displayed orbital tilt always refers to the canonical vector J.

Energy, J_tot, and both spin lengths are conserved in every selected model. For cases 4 and 5, J² and C = J · S_eff are also conserved, where

**S_eff = (2 + 3m₂/(2m₁))S₁ + (2 + 3m₁/(2m₂))S₂ = 3S₁ + 4.25S₂.**

They are constant in the decoupled cases 1–3 as well. In cases 6–7, changes in J² and C can be physical. The integrability of the truncated 1.5PN model and perturbative integrability through full 2PN are different statements; a nonclosing or nonplanar orbit alone is not evidence of chaos.

## Numerical checks and display limitations

The motion follows Hamilton's equations with canonical spin brackets. Stored trajectories were calculated using fourth-order Runge–Kutta integration and checked by halving the time step. Displayed states are reconstructed by short integrations from nearby checkpoints, rather than linear interpolation of phase-space coordinates.

Checks of 700 intermediate frames in each case found relative energy errors below 10⁻⁸. The live diagnostics evaluate the displayed state; the total-angular-momentum arrow is computed from that state, not held fixed by construction. These are numerical checks for this setup, not a measure of the accuracy of the PN approximation to general relativity.

Further limitations:

- The selected truncated Hamiltonian is evolved numerically without re-expanding its solution at every step.
- Individual body locations use the leading centre-of-mass split x₁ = 0.4r and x₂ = −0.6r. Higher-PN centre-of-mass corrections are not reconstructed.
- Body sizes are enlarged. Each arrow has its own fixed display scale, so lengths of different arrows should not be compared directly.
- Precession angles and departures from the initial plane are not exaggerated.
- Trajectory trails are smooth visual guides; they are not additional integrated dynamical states.
- The animation does not calculate gravitational waveforms or a one-cycle Magnusian.

## References

- **Tanay, Stein and Gálvez Ghersi**, *Integrability of eccentric, spinning black hole binaries up to second post-Newtonian order*. Sections II–IV give the Hamiltonian, Poisson structure, and integrability discussion. Their effective-spin convention is half the one used here. [arXiv:2012.06586](https://arxiv.org/html/2012.06586)
- **Cho and Lee**, *Analytic Keplerian-type parametrization for general spinning compact binaries with the leading order spin-orbit interaction*. An analytical treatment of precessing eccentric motion; their displayed Hamiltonian deliberately omits the 1PN orbital correction. [arXiv:1908.02927](https://arxiv.org/abs/1908.02927)
- **Hartl and Buonanno**, *The dynamics of precessing binary black holes using the post-Newtonian approximation*. Numerical conservative dynamics including spin–orbit, spin–spin, and spin-induced quadrupole interactions. [arXiv:gr-qc/0407091](https://arxiv.org/abs/gr-qc/0407091)
