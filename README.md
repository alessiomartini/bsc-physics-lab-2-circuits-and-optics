# Physics Laboratory II — Lab Reports (UniMiB)

The six lab reports of *Laboratorio di Fisica II*, BSc in Physics, Università
degli Studi di Milano-Bicocca — **Alessio Martini, Matthew Maisano and Niccolò
Mantovani**.

Three experiments on **electrical circuits** and three on **waves and optics**.
Each report is a complete, self-contained LaTeX document (15–30 pages) with the
same structure throughout:

> **Introduzione** (aim + theory) → **Esperienza in breve** (what was actually
> done) → **Strumentazione** (the instruments and their sensitivities) →
> **Dati** (every measurement, with its uncertainty) → **Analisi dei dati**
> (fits, χ², p-values, propagated errors) → **Conclusioni** →
> **Riflessioni**

The **Riflessioni** section at the end of each report is the distinctive one:
rather than closing on the result, it takes up whatever did not fit the model
during the experiment and works out why. Several of the most interesting
results in this repository are in those sections.

Reports are written in Italian.

## Part one — electrical circuits

### `Circuiti_1.pdf` — Ohmic and non-ohmic materials *(22 pp.)*

Starts by characterising the instruments before trusting them: the internal
resistance of the voltmeter is extracted from an equivalent-resistance
measurement ($R_\text{eq} = 900 \pm 3\ \text{k}\Omega \Rightarrow R_\text{int}
\approx 9\ \text{M}\Omega$), and the same is done for the ammeter. That result
then justifies the rest: **Ohm's law** is verified in two circuit
configurations, and the report explains *why* each configuration demands
resistances of a particular order of magnitude — large for (I), small for (II) —
so that the instrument's own resistance drops out of the measurement.

Then a **resistive voltage divider**, and finally a **diode**, where the linear
model stops working and the **Shockley equation** takes over — the "non-ohmic"
half of the title. The diode analysis is cross-checked against another group's
independent reduction of the same data.

### `Circuiti_2.pdf` — Pulsed-current response *(26 pp.)*

Transient response measured on an oscilloscope, driving the circuits with a
square wave plus a DC offset from a bench generator to simulate a pulsed
current.

**RC**, **RL** and **RLC** circuits, with the RLC studied in all three regimes —
under-damped, critically damped and over-damped — plus an RL circuit treated with
a *real* (non-ideal) inductance.

The conclusions are candid: every model was confirmed **except the under-damped
RLC**, and rather than explain the discrepancy away, the report says plainly
that no convincing cause was found and lists the possibilities (a disconnected
component, an instrument fault, human error). Compatibility of the fitted
parameters holds at the 1% significance threshold but not always at 5%.

*Riflessioni*: rectified current through a **Graetz bridge** — four diodes that
flip the negative half of a sinusoid, doubling the frequency and producing a
non-zero mean voltage.

### `Circuiti_3.pdf` — Resonance phenomena *(30 pp.)*

The frequency-domain counterpart of `Circuiti_2`. Characteristic impedances and
**transfer functions** — modulus and phase — measured across RC, RL and RLC
circuits, with the transfer function taken separately across each component
(generator and resistor, then capacitor; then inductor). Every fit is validated
with a **p-value test**, and $C$ and $L$ are recovered from the fit parameters
and compared between independent determinations.

Conclusion: the forced–damped oscillator equation
$\ddot{x} + \gamma\dot{x} + \omega_0^2 x = f(t)$ describes the RLC circuit to
excellent accuracy — all p-values clear the 5% threshold.

*Riflessioni*: the best moment in the set. At 15 MHz the measured $|H_R|$ in the
**RC** circuit departed from its expected asymptote of 1. Rather than discard the
point, the group hypothesised that the circuit's own **self-inductance** was no
longer negligible, refitted with an RLC model, and then estimated the
inductance of a square loop analytically,

$$L_\text{square} \approx \frac{2\mu_0 l}{\pi}\left[\ln\frac{l}{a} - 0.774\right]$$

getting $L \approx 946\ \text{nH}$ against the $921\ \text{nH}$ returned by the
fit. A stray parasitic turned into a quantitative prediction that checks out.

## Part two — waves and optics

### `Interferometro.pdf` — Interferometry *(15 pp.)*

A laser, beam splitters and movable mirrors on an interferometer bench, in three
configurations:

- **Fabry–Perot** — verification of the interference law, and an estimate of the
  mirror displacement $\Delta d$ from fringe counting;
- **Michelson** — the **refractive index of air** and **of glass**;
- **Ruler as a diffraction grating** — light at grazing incidence off a ruler,
  giving a pitch $d = (9.5 \pm 1.4)\times 10^{-4}\ \text{m}$ against the nominal
  1 mm, compatible at $\tau = 0.5\sigma$ (61.7% probability of a larger
  discrepancy).

The conclusions state a genuine limitation instead of glossing it: the measured
refractive indices **could not be checked against tabulated values**, because no
tabulation exists at the laser's wavelength.

*Riflessioni*: running Fabry–Perot backwards. With the wavelength known,
counting fringes measures an unknown displacement far more precisely than any
mechanical method — a fiftieth-scale vernier resolves 0.02 mm, the optical
method does much better.

### `Microonde.pdf` — Wave behaviour of the electromagnetic field *(21 pp.)*

Geometrical and physical optics done at microwave wavelengths, where the
wavelength is centimetric and every effect is directly measurable:

- **wavelength**, from the standing-wave pattern;
- **the law of reflection** (Cartesio/Snell), verified by sampling the received
  voltage around the expected angle at three different angles of incidence;
- **refractive index of styrene**;
- **polarisation**;
- **Brewster's angle**.

Conclusion: geometrical optics accounts for all of it.

*Riflessioni*: an attempt to confirm that the field falls off as $1/r$ far from
the source, sampling the receiver voltage from 53 cm to 112 cm and fitting
$A/r + B$. The trend follows, but the report is honest that the **χ² test does
not support the hypothesis** — the scatter around the fit is much larger than the
error bars derived from instrument sensitivity, which means the uncertainties
were underestimated rather than the physics being wrong.

### `Spettrometro.pdf` — Spectrometry with a prism and a diffraction grating *(18 pp.)*

Two instruments measuring the same thing, so they can be played off against each
other. Known sources (**mercury**, **sodium**) calibrate each instrument, then an
**unknown gas** is identified from its spectrum.

With the **prism**, the refractive index comes from the angle of minimum
deviation,

$$\eta(\delta_\text{min}) = \frac{\sin\frac{\delta_\text{min} + \alpha}{2}}{\sin\frac{\alpha}{2}}$$

and the Hg lines are used to fit **Cauchy's law**. With the **grating**, the
wavelengths follow from the diffraction orders directly.

The conclusion is the comparison itself: the prism is more precise at high
frequencies, the grating at low ones, and each behaves exactly as its
**resolving power** (prism) and **dispersive power** $D = n/(d\cos\theta)$
(grating) predict. The grating wins overall across the visible, because the
prism's wavelengths inherit the propagated error of the linear fit that produced
Cauchy's coefficients $A$ and $B$.

## The recurring method

Worth stating separately, because it is what the course was really teaching:

1. **Characterise the instrument before trusting the measurement** — the internal
   resistances in `Circuiti_1`, the sensitivity of every device listed in each
   *Strumentazione* section.
2. **Every number carries an uncertainty, and every uncertainty is propagated.**
3. **Agreement is tested, not asserted** — p-values, χ², and Student's t-test
   against tabulated values, with an explicit acceptance threshold.
4. **Report what disagrees.** The under-damped RLC, the failed χ² on the $1/r$
   law, the 3.7σ discrepancy in the companion Lab I course — all of them are
   stated rather than buried.

## A note on the dates

The date on every title page is the date the LaTeX was last compiled, not the
date the experiment was performed.

## Related repository

- [`physics-lab-1-mechanics-and-waves-unimib`](https://github.com/alessiomartini/physics-lab-1-mechanics-and-waves-unimib)
  — the first-year laboratory course: Cavendish and Coulomb balances, acoustic
  tube, pendulum, springs.
