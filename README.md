# Ultrafast Electron Transfer — Interactive Physics + Sonification Lab

A single-file, dependency-free web app that simulates and **sonifies** the
ultrafast dynamics of a donor excitation injected into an acceptor aggregate
held in the Coulomb potential of the hole left behind — inspired by
Somoza *et al.*, *Nature Communications Physics.* (2023),
[s42005-023-01179-z](https://www.nature.com/articles/s42005-023-01179-z).

Built as a didactic tool (high-school to early-undergraduate level) to
develop intuition for delocalization, quantum interference, resonant
transfer, Bloch oscillations, disorder-induced localization and
ballistic vs. diffusive transport in simple model Hamiltonians.

## Launch the app

- **GitHub Pages (recommended):**
  `https://cacosomoza.github.io/QuantumSynthesizer/`
  *(enable once: repo Settings → Pages → Deploy from branch → `main` / root)*
- **Instant preview (no setup):**
  [Launch via htmlpreview](https://htmlpreview.github.io/?https://github.com/cacosomoza/QuantumSynthesizer/blob/main/index.html)
- **Offline:** just open `index.html` in any modern browser — no server,
  no build step, no dependencies.

The interface is bilingual: use the 🌐 button (top right) to switch between
English and 中文. You can also force a language with `?lang=en` / `?lang=zh`.

## The physical model

Single-excitation manifold, closed-system Schrödinger dynamics:

H = Σₙ Ωₙ |n⟩⟨n| + J Σₙ (|n⟩⟨n+1| + h.c.)

- **Donor** (site 0): Ω₀ = Δ − V, coupled to the chain with strength J_donor.
- **Acceptors**: Ωₙ = −V/n (frozen-hole Coulomb potential; trap at n = 1).
- **Geometries**: 1D chain (2–500 sites) or 2D square lattice (up to 30×30
  acceptors + central donor, 901 levels).
- Optional constant electric field F (Wannier–Stark ladder / Bloch
  oscillations) and static Gaussian disorder on the acceptor onsites.
- Initial state |ψ(0)⟩ = |donor⟩; exact propagation in the eigenbasis,
  ψ(n,t) = Σₖ cₖ φₖ(n) e^(−iEₖt/ħ).

Reference parameters (P3HT:PCBM-like, from the paper): J = 500 cm⁻¹,
V = 2420 cm⁻¹.

## What you can see

| Panel | Content |
|---|---|
| **Physical model** | Live schematic: donor "plugged" into the chain (1D) or hovering over a metallic surface (2D). Sites glow with \|ψₙ(t)\|² in real time; **click any site (or the donor) to hear its pitch**. |
| **Eigenbasis** | Instantaneous signed contributions Re[cₖ φₖ(n) e^(−iEₖt/ħ)] per eigenstate, phase dials, injection bands. Hover a level (2D) to inspect its eigenstate on the lattice. |
| **Site basis** | Onsite energies Ωₙ + live populations Pₙ(t). Vertically **drag the energy scale to sculpt** the onsite landscape (Gaussian brush = emphasis slider). |
| **Populations vs. time** | P₀ (donor), P₁ (trap), Σ Pₙ≥₂ (separated). Draggable in time. |
| **P_transfer(Δ), γ(Δ), ⟨n⟩max(Δ)** | Sweeps vs. donor detuning: resonant transfer peaks, transport exponent (subdiffusive → diffusive → ballistic → superballistic), maximum wavepacket reach. Click to set Δ. |
| **Kubo transport** | Velocity autocorrelation, D(t), and Re σ(ν) (THz conductivity) for the injection quench vs. thermal Kubo–Greenwood at a chosen temperature. |

## What you can hear

Every dynamical degree of freedom is mapped to sound (WebAudio):

- **Engines**: additive (one voice per ladder region), wavetable, granular.
- **Modes**: *musical* (pitches quantized to a scale; in 2D, pitch follows
  distance rings around the central trap — first neighbors one scale degree
  up, etc.) or *scientific* (frequency linear in onsite energy, Hz/eV).
- **Scales**: 7 diatonic modes, major/minor pentatonic, chromatic,
  **phrygian dominant**, **hirajoshi**.
- **Harmony engine**: `fixed`, `stochastic walk` (biased random walk along the
  mode-brightness axis), or `progression` — tonal moves only: relative modes
  sharing the same pitch collection (mixolydian ↔ dorian …), circle-of-fifths
  tonic shifts (one accidental at a time), pentatonic breaths. Transitions are
  triggered by wavepacket activity, boosted at boundary reflections; the
  photocurrent sign steers brighter/darker.
- **Rhythm**: gating driven by D(t), d⟨n⟩/dt, separated population, or
  threshold site-events; coherence Cₙ drives FM/AM modulation.
- **Output monitor**: oscilloscope + Lissajous phase scope of the
  post-compressor master mix.

## Controls & tips

- **Presets**: tight-binding, Bloch–Zener (field), paper parameters,
  dissociation.
- URL parameters for deep-linking a configuration:
  `?n=50&j=500&v=2420&delta=0.3&jd=500&f=0&dim=2&play=1&theme=crt&lang=zh`
- **Themes**: dark / light / CRT (1970s phosphor terminal).
- **Magnifier** 🔍: hover any plot to zoom.
- Time resolution slider = samples per shortest oscillation period
  (right = finer timestep).

## Files

```
index.html   — the entire app (HTML + CSS + JS, zero dependencies)
README.md    — this file
```

## Citation

If you use this app in teaching or talks, please credit the underlying
physics to Gajewski *et al.*, *Nat. Commun.* (2026),
[doi:10.1038/s41467-026-73700-1](https://www.nature.com/articles/s41467-026-73700-1).
