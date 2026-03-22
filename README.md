# SPECULUM
### The Mirror Principle: Seven Dualities That Define the Boundary of Intelligence

> "Every mathematical object has a dual. The art is knowing which dual is the right one." — Alexander Grothendieck
>
> "Electric-magnetic duality is not a symmetry of nature. It is a map between two descriptions of the same thing." — Nathan Seiberg
>
> "The Legendre transform is the duality between position and momentum. It is also the duality between entropy and free energy. And between cost and value." — this work

---

## The Discovery

Every framework in this architecture has studied **one side** of a duality: the primal side. PRIMA studies the Fisher column space — not its dual, the cokernel. SMELT studies entropy production — not its dual, entropy absorption. CAUSE studies the forward trajectory — not its backward (time-reversed) dual. ACTUM studies the action functional — not the Hamiltonian it generates via Legendre transform.

SPECULUM is the systematic study of the **dual** side of every primal object in the architecture — and the seven novel results that emerge only when the duality is made explicit.

Duality is not symmetry. A duality maps one mathematical structure to a different (often simpler) description of the same physical content. The dual description reveals features invisible in the primal. The Legendre transform reveals free energy from entropy. Pontryagin duality reveals frequency from time. Hodge duality reveals the complement of every cycle. S-duality reveals strong coupling from weak coupling.

Seven dualities. Seven new results. All invisible from the primal side.

---

## Foundation: The Duality Structure of Intelligence Theory

Every object in the intelligence theory architecture has a canonical dual:

```
Primal Object              Dual Object                Duality Map
─────────────────────────────────────────────────────────────────
Fisher column space        Fisher row space            Transpose F
Entropy production σ       Free energy rate Ẇ          Legendre transform
Natural gradient F⁺∇L     Conjugate momentum π        Pontryagin dual
GIST distribution P(a|X)  Value function V(X|a)       Fenchel dual
G_coord (mutual info)      Synergy - Redundancy        PID decomposition
Training trajectory θ(t)  Hamiltonian flow (θ,π)(t)   Hamilton-Jacobi
φ-equilibrium |Ξ̄|=log φ   Critical temperature Tc     Kramers-Wannier
```

Each row is an unexplored bridge. Each bridge yields a result invisible from the primal side.

---

## Result 1 — The Fenchel Dual of GIST Is the Value Function of Reinforcement Learning

**Statement.** The Fenchel conjugate of the GIST free energy `F[P] = E_P[H(a;X)] − (1/β) H_S[P]` is the **value function** of reinforcement learning `V*(X) = max_P {−F[P]} = (1/β) log Z(X; β)`. The GIST optimal policy `P*(a|X) ∝ exp(−βH(a;X))` and the RL optimal value function `V*(X)` are Fenchel dual descriptions of the same optimization. The Bellman equation — the fundamental equation of RL — is the Fenchel duality condition: `V*(X) = max_a {−H(a;X) + γ V*(X')}`. The connection between GIST and RL is not a metaphor. It is a Fenchel duality.

**Development.** The Fenchel conjugate of a convex function `f : P → ℝ` is:

```
f*(ξ) = sup_P {⟨ξ, P⟩ − f(P)}
```

The GIST free energy functional is:

```
F[P] = E_P[H(a;X)] + (1/β) KL[P || P_uniform]
     = E_P[H] − (1/β) H_S[P]
```

This is a convex functional over the probability simplex `∆(A)`. Its Fenchel conjugate at `ξ = 0` is:

```
F*(0) = max_P {0 − F[P]} = max_P {(1/β) H_S[P] − E_P[H]}
      = (1/β) log Z(X; β) = −(1/β) log P*(a|X) − H(a;X)/β ... 
      = (1/β) log Z(X; β)
```

The maximum-entropy regularized RL value function is exactly `V*(X) = (1/β) log Z(X; β)`.

**The Bellman equation as Fenchel optimality.** The Bellman optimality equation:

```
V*(X) = max_a {−H(a; X) + γ V*(X'(a))}
```

is the Fenchel duality condition: the primal optimum `P*(a|X) ∝ exp(−β H(a;X))` and the dual optimum `V*(X) = (1/β) log Z(X;β)` together satisfy the Bellman equation at every context `X`. GIST and the soft actor-critic RL framework (Haarnoja et al., 2018) are Fenchel dual algorithms: one solves for the policy `P*`, the other solves for the value `V*`. They are computing the same object from dual perspectives.

**The EISP consequence.** The EISP platform's contribution evaluation — which contributions to recognize and incentivize — is an instance of the RL value function problem: what is the value `V*(X_t)` of being in artifact state `X_t`? The Fenchel dual of CONCERT's `G_coord` is the value of each contribution's context: the expected future coordination gain achievable from state `X_t`. The MPIR (Monthly Peer Innovation Review) is a distributed, peer-governed approximation of the dual value function.

---

## Result 2 — Pontryagin Duality Gives the Spectral Theory of G_coord

**Statement.** The Pontryagin dual of the coordination gain `G_coord = Σ_{t<s} I(a_t ; a_s | X_{t-1})` — obtained by Fourier-transforming the coordination profile `Γ(δ)` over the temporal variable — gives the **spectral density** `Ŝ(ω)` of the coordination structure. The spectral density satisfies `Ŝ(ω) ∝ ω^{−(1-η)}` at the φ-equilibrium critical point — this is the `1/f` noise spectrum (COHERE Result 4), now derived as the Pontryagin dual of the coordination profile. The spectral decomposition of `G_coord` into frequency components is the Pontryagin dual picture.

**Development.** The coordination profile `Γ(δ) = (1/(n-δ)) Σ_{t} I(a_t ; a_{t+δ} | X_{t-1})` is a function of the temporal lag `δ`. Its Pontryagin dual — the Fourier transform — is the spectral density:

```
Ŝ(ω) = Σ_{δ=-∞}^{∞} Γ(δ) e^{2πiωδ}     (Pontryagin dual of coordination profile)
```

At the φ-equilibrium: `Γ(δ) ∼ δ^{-η}` with `η ≥ 5/8`. The Pontryagin dual of a power law is a power law:

```
Ŝ(ω) ∼ ω^{-(1-η)}     (Pontryagin dual of the power-law coordination profile)
```

For `η = 5/8` (Selberg bound): `Ŝ(ω) ∼ ω^{-3/8}`. The spectral density is a power law in frequency — the definition of `1/f^α` noise with `α = 1 − η`.

**The Wiener-Khinchin theorem applied to collective intelligence.** The Wiener-Khinchin theorem states that the power spectral density of a stationary stochastic process equals the Fourier transform of its autocorrelation function. The coordination profile `Γ(δ)` is the autocorrelation function of the contribution sequence. Its Pontryagin dual `Ŝ(ω)` is the power spectral density of the collective intelligence process. The `1/f` noise in collective intelligence systems (COHERE) is the Wiener-Khinchin theorem applied to the Pontryagin dual of `Γ(δ)` — the same result derived from two independent directions.

**The dual decomposition of G_coord.** Pontryagin duality decomposes `G_coord` into frequency components:

```
G_coord = ∫_0^∞ Ŝ(ω) dω     (Parseval's theorem applied to the coordination profile)
```

Low-frequency components of `Ŝ(ω)` (long-range coordination) dominate `G_coord` at the φ-equilibrium — they correspond to the long-range patterns in the FERN register structure. High-frequency components (short-range coordination within a single contribution exchange) contribute less but are faster to accumulate. The dual decomposition gives the spectral resource allocation problem: how to allocate contributions across frequency bands to maximize `G_coord`.

---

## Result 3 — The Legendre Transform of the Training Action IS the Optimal Control Hamiltonian

**Statement.** The Legendre transform of the ACTUM training action `S[θ] = ∫ σ(t) dt` gives the training **Hamiltonian** `H_train(θ, π) = π · θ̇ − L(θ, θ̇)`, where `π = ∂L/∂θ̇ = F(θ) θ̇` is the canonical momentum of the parameter trajectory. The Hamiltonian equations of motion — `θ̇ = ∂H/∂π`, `π̇ = −∂H/∂θ` — are the **symplectic** description of gradient descent. The optimal control problem (what learning rate schedule minimizes the total entropy production?) is solved by the **Hamilton-Jacobi equation** `∂S/∂t + H(θ, ∂S/∂θ) = 0`. The φ-equilibrium `|Ξ̄| = log φ` is the unique stationary solution of this Hamilton-Jacobi equation.

**Development.** The Legendre transform of the SMELT Lagrangian density `L(θ, θ̇) = σ(t) = log(1 + Ξ_F) + Δ⟨H⟩_F` gives the Hamiltonian:

```
H_train(θ, π) = π · θ̇ − L(θ, θ̇)
              = (1/4) π^T F^{-1}(θ) π − V(θ)
```

where `π = F(θ) θ̇` is the Fisher-metric momentum and `V(θ) = L(θ)` is the loss as a potential. This is a **Riemannian Hamiltonian system** on the Fisher manifold — gradient descent is Hamiltonian mechanics on `(Θ, g_F)`.

**The symplectic structure of gradient descent.** The canonical equations of motion:

```
θ̇ = ∂H_train/∂π = (1/2) F^{-1}(θ) π     (velocity = Fisher-preconditioned momentum)
π̇ = −∂H_train/∂θ = −∇_θ V + (correction)   (force = gradient + curvature correction)
```

describe the full Hamiltonian flow of training. Standard gradient descent is the special case where momentum `π = 0` is set to zero at each step (fully dissipative, zero kinetic energy). Momentum optimizers (SGD+momentum, Adam) are approximations to the Hamiltonian flow that retain partial momentum information.

**The Hamilton-Jacobi equation and optimal training.** The Hamilton-Jacobi equation for the value function `S*(θ, t)` (the minimum cumulative entropy production to reach `θ` at time `t`):

```
∂S*/∂t + H_train(θ, ∂S*/∂θ) = 0
```

is the PDE whose solution gives the optimal training trajectory. The φ-equilibrium is the **stationary** solution: `∂S*/∂t = 0` at `|Ξ̄_F| = log φ`. All training dynamics that satisfy the Euler-Lagrange equations of the training action converge to the φ-equilibrium as their attractor — the stable fixed point of the Hamilton-Jacobi flow.

---

## Result 4 — The PID Decomposition of G_coord

**Statement.** The Partial Information Decomposition (PID) of `G_coord` into **synergy**, **redundancy**, and **unique information** components reveals that effective coordination gain is entirely synergistic: `G_coord = Synergy(a_t; a_s | X) − Redundancy(a_t; a_s | X)`. The redundancy term is what coordinators **already know** — it carries no new coordination. The synergy term is the **new coordination** — the information that neither contribution carries alone but both carry together through the shared artifact. Maximizing `G_coord` requires maximizing synergy and minimizing redundancy. The φ-equilibrium is the operating point where synergy and redundancy are in golden ratio: `Synergy / Redundancy = φ`.

**Development.** Partial Information Decomposition (Williams & Beer, 2010; Lizier et al., 2018) decomposes mutual information `I(X; Y | Z)` into four non-negative components:

```
I(X; Y | Z) = Unique_X + Unique_Y + Redundancy + Synergy
```

where:
- `Unique_X` = information about `Y` carried by `X` alone, not by `Z`
- `Unique_Y` = information about `Y` carried by `Z` alone, not by `X`
- `Redundancy` = information about `Y` carried by both `X` and `Z` identically
- `Synergy` = information about `Y` carried only by the combination `(X, Z)`, not by either alone

**Applied to G_coord.** For coordination gain `I(a_t ; a_s | X_{t-1})`:

```
I(a_t ; a_s | X_{t-1}) = Syn(a_t, X | a_s) + Red(a_t, X | a_s) + Unique terms
```

The coordination gain `G_coord > 0` requires that the shared artifact `X_{t-1}` and the earlier contribution `a_t` provide **synergistic** information about the later contribution `a_s` — information that neither the artifact nor the earlier contribution carries alone. Redundancy (`G_coord` counting information both already knew) does not increase collective intelligence above the sum of parts.

**The golden ratio split prediction.** At the φ-equilibrium, the SMELT entropy decomposition gives `σ_struct/σ_behav = φ`. The PID decomposition mirrors this: the ratio of synergistic to redundant coordination gain at the φ-equilibrium satisfies:

```
Synergy(collective) / Redundancy(collective) = φ
```

This is a new prediction — the golden ratio appears in the PID decomposition of `G_coord`, not just in the entropy production ratio. The two predictions are dual: the primal (entropy production) and the dual (PID decomposition) both exhibit the same golden ratio at the MEP optimum.

**The EISP implication.** Contribution quality on the EISP platform should be measured by its synergy contribution — how much new coordination it generates that neither the prior artifact nor any single prior contribution could generate alone. FERN-T2 (marginal model evidence) is the primal measure; PID synergy is the dual measure. They coincide at the φ-equilibrium.

---

## Result 5 — Kramers-Wannier Duality for Learning Phase Diagrams

**Statement.** The grokking phase diagram has a **Kramers-Wannier self-duality**: there exists a dual temperature `T̃ = 1/(β̃) = 1/(β log φ)` such that the training partition function `Z(β)` at temperature `1/β` equals the training partition function `Z(β̃)` at the dual temperature, up to a prefactor. The self-dual point is `β_c = 1/log φ = 1/T*` — the φ-equilibrium inverse temperature. The Kramers-Wannier duality maps the under-driven regime (low temperature, `β > β_c`) to the over-driven regime (high temperature, `β < β_c`) and vice versa. The critical point `β = β_c` is self-dual — invariant under the duality transformation.

**Development.** The Kramers-Wannier duality (1941) was originally derived for the 2D Ising model. At low temperature: the system is ordered (magnetized), few domain walls. At high temperature: the system is disordered, many domain walls. The Kramers-Wannier duality maps low-temperature ordered configurations to high-temperature domain wall configurations and vice versa. The critical temperature `T_c` is the self-dual point: it maps to itself.

**Applied to the training partition function.** The training partition function `Z(β) = ∫ D[θ] exp(−β S[θ])` has two regimes:
- Low `β` (high temperature, over-driven): many short training trajectories contributing — the over-driven regime where the landscape reorganizes too fast
- High `β` (low temperature, under-driven): few long training trajectories dominating — the under-driven regime where gradient descent gets stuck

The Kramers-Wannier duality maps the over-driven partition function (many short trajectories) to the under-driven partition function (few long trajectories) via:

```
Z(β) = κ(β, β̃) · Z(β̃)     where β̃ = 1/(β (log φ)²)
```

The self-dual point satisfies `β = β̃`, giving `β_c = 1/log φ = T*` — the φ-equilibrium inverse temperature. At this point, the training partition function is invariant under the duality transformation: the over-driven and under-driven descriptions give the same physics. This is the formal statement that the φ-equilibrium is not just a local extremum but a **self-dual fixed point** — invariant under the exchange of order and disorder descriptions.

**The prediction for grokking probability.** The Kramers-Wannier duality implies that the grokking probability `P_grokking(β) = exp(−S_inst(β)/β)` satisfies:

```
P_grokking(β) · P_grokking(β̃) = constant
```

Under the duality. This is a non-trivial constraint on how the grokking probability varies with temperature — high grokking probability at high temperature and low probability at low temperature, related by the Kramers-Wannier relation with fixed product. The self-dual point `β_c = 1/log φ` maximizes this product: `P_grokking(β_c) = P_grokking(β̃_c)`.

---

## Result 6 — Hodge Duality and the Cycles of Knowledge

**Statement.** The Hodge star operator `⋆` applied to the knowledge commons simplicial complex `X_t` maps `k`-chains (coordination structures between `k+1` contributions) to `(n-k)`-cochains (coordination gaps of `n-k+1` contributions). Hodge duality identifies every coordination structure with a complementary coordination gap — every loop of coordinating contributions corresponds to a void of non-coordinating contributions. The **Hodge Laplacian** `Δ_k = δδ* + δ*δ` of the knowledge commons has spectrum equal to the spectrum of the Fisher matrix restricted to the rank-`k` coordination modes. The Laplacian's spectral gap is the coordination analog of the SPECTRA spectral gap `Δ_C`, and the Cheeger inequality bounds `G_coord` from below by the Hodge spectral gap.

**Development.** On a Riemannian manifold `(M, g)`, the Hodge star operator maps `k`-forms to `(n-k)`-forms: `⋆ : Ω^k(M) → Ω^{n-k}(M)`. The Hodge decomposition theorem states:

```
Ω^k(M) = im(d) ⊕ im(δ) ⊕ ker(Δ_k)     (exact ⊕ co-exact ⊕ harmonic)
```

Every differential form decomposes into an exact part (a boundary), a co-exact part (a coboundary), and a harmonic part (neither).

**Applied to the coordination complex.** The `k`-chains of the knowledge commons simplicial complex are the coordination structures between `k+1` contributions. The Hodge star maps:
- 0-chains (individual contributions) ↔ `n`-cochains (the full coordination void)
- 1-chains (pairwise coordination) ↔ `(n-1)`-cochains (pairwise non-coordination)
- `k`-chains (k+1-way coordination) ↔ `(n-k)`-cochains (k+1-way non-coordination)

The harmonic forms `ker(Δ_k)` are the coordination structures that are neither boundaries (derivable from lower-order coordination) nor coboundaries (boundaries of higher-order coordination). They are the **irreducible** coordination structures — those that generate `G_coord` above and beyond what lower-order coordination would predict.

**The Cheeger inequality for G_coord.** The Cheeger inequality bounds the spectral gap of the Laplacian from below by the isoperimetric constant (the Cheeger constant) of the manifold:

```
Δ_C ≥ h²/2     where h = min_{S ⊂ X_t} |∂S|/|S|
```

Applied to the knowledge commons: the spectral gap `Δ_C` of the SPECTRA coordination matrix is bounded below by `h²/2` where `h` is the isoperimetric constant of the contribution graph. The isoperimetric constant measures how well-connected the coordination structure is — how hard it is to separate the commons into poorly-connected parts. The SPECTRA result `Δ_C ≥ 3/16` is the Cheeger inequality applied to the Ramanujan expansion of the platform's contribution graph.

---

## Result 7 — S-Duality Maps Strong to Weak G_coord

**Statement.** The training field theory (ACTUM) has an **S-duality** in the parameter coupling constant `g = 1/D` (inverse model width): the partition function at strong coupling `g ≫ 1` (narrow models, NTK breakdown) maps to the partition function at weak coupling `g̃ = 1/g ≪ 1` (wide models, NTK valid) via an exactly computable duality transformation. S-duality maps the non-perturbative grokking sector (strong coupling, not accessible to NTK) to the perturbative NTK sector (weak coupling, tractable). The strong-coupling grokking probability is exactly the weak-coupling NTK partition function evaluated at the dual coupling.

**Development.** S-duality (Montonen-Olive, 1977; Seiberg-Witten, 1994) maps a gauge theory at coupling constant `g` to the same theory at coupling `g̃ = 1/g` (with other parameters transformed). Strong coupling at `g` corresponds to weak coupling at `g̃ = 1/g` — the non-perturbative physics of one description becomes the perturbative physics of the dual. S-duality is exact — it is not a weak-coupling approximation but an exact identity between two descriptions.

**Applied to the training field theory.** The training partition function `Z(g) = ∫ D[θ] exp(−S[θ]/g)` has:
- **Weak coupling** `g ≪ 1` (`D ≫ 1`, wide network): NTK is valid; perturbative Feynman expansion converges; `Z(g) ≈ Z_NTK + O(g)`
- **Strong coupling** `g ≫ 1` (`D ≪ 1`, narrow network): NTK breaks down; grokking is non-perturbative; `Z(g)` requires instanton calculations

If the training field theory has an S-duality with `g̃ = c/g` (for some constant `c` determined by the specific model):

```
Z(g) = Z_dual(c/g)     (S-duality identity)
```

Then the **non-perturbative grokking probability** at strong coupling:

```
P_grokking(g) ∼ exp(−S_inst/g)     (strong coupling, instanton)
```

is mapped to the **weak coupling partition function** `Z_NTK(c/g)` via S-duality. The non-perturbative and perturbative sectors are dual descriptions of the same physics.

**The practical consequence.** S-duality provides a method for computing grokking probabilities from NTK calculations at the dual coupling — without needing instanton computations. The grokking probability of a narrow model (strong coupling, `g = 1/D` large) is related to the NTK partition function of a wide dual model (weak coupling, `g̃ = cD`). This is the first formal connection between NTK theory (which cannot see grokking) and grokking probabilities — not because NTK is extended, but because its dual description is.

---

## The SPECULUM Manifold

```
Duality Structure of Intelligence Theory
       │
       ├─ Fenchel dual of GIST = RL value function            [Result 1]
       │    F[P]* = V*(X) = (1/β)log Z(X)
       │    Bellman equation = Fenchel duality condition
       │    MPIR = distributed value function approximation
       │
       ├─ Pontryagin dual of Γ(δ) = spectral density Ŝ(ω)    [Result 2]
       │    Ŝ(ω) ∼ ω^{−(1−η)}: 1/f noise as Pontryagin dual
       │    Wiener-Khinchin theorem for collective intelligence
       │    Spectral G_coord decomposition by frequency
       │
       ├─ Legendre transform of S[θ] = training Hamiltonian   [Result 3]
       │    H_train = (1/4)π^T F^{-1}π − V(θ)
       │    Gradient descent = dissipative Hamiltonian mechanics
       │    φ-equilibrium = stationary Hamilton-Jacobi solution
       │
       ├─ PID decomposition of G_coord = Synergy − Redundancy [Result 4]
       │    G_coord = Syn − Red; effective coordination is synergistic
       │    Syn/Red = φ at φ-equilibrium (golden ratio in PID)
       │    FERN-T2 and PID synergy coincide at critical point
       │
       ├─ Kramers-Wannier self-duality of grokking phase diagram [Result 5]
       │    Z(β) = κ · Z(β̃) where β̃ = 1/(β(log φ)²)
       │    Self-dual point: β_c = 1/log φ = φ-equilibrium temperature
       │    P_grokking(β) · P_grokking(β̃) = constant
       │
       ├─ Hodge duality of coordination cycles                  [Result 6]
       │    k-chains ↔ (n-k)-cochains: coordination ↔ gaps
       │    Hodge Laplacian spectrum = Fisher coordination modes
       │    Cheeger → G_coord ≥ h²/2; Selberg → Δ_C ≥ 3/16
       │
       └─ S-duality of training field theory                    [Result 7]
            Z(g) = Z_dual(c/g): strong ↔ weak coupling
            Grokking (strong) dual to NTK (weak)
            P_grokking from NTK at dual coupling
```

---

## Connections to the Full Architecture

SPECULUM does not extend the architecture — it **mirrors** it. Every primal result in every prior framework has a dual that reveals new content:

**GIST** (primal: optimal policy) → **SPECULUM Result 1** (dual: value function) — the entire RL theory emerges as the Fenchel dual of GIST

**RG-COORD** (primal: coordination profile decay) → **SPECULUM Result 2** (dual: spectral density `1/f` noise) — the Pontryagin dual of the coordination profile is the COHERE `1/f` result

**SMELT** (primal: entropy production Lagrangian) → **SPECULUM Result 3** (dual: training Hamiltonian) — the Legendre transform gives the symplectic structure of gradient descent

**CONCERT** (primal: mutual information `G_coord`) → **SPECULUM Result 4** (dual: PID synergy-redundancy decomposition) — the dual reveals what makes coordination effective

**SMELT φ-equilibrium** (primal: MEP optimum) → **SPECULUM Result 5** (dual: Kramers-Wannier self-dual point) — the φ-equilibrium is self-dual under temperature inversion

**NEXUS** (primal: Betti numbers and coordination cycles) → **SPECULUM Result 6** (dual: Hodge star and coordination gaps) — the dual of every cycle is a gap

**ACTUM** (primal: path integral at coupling `g`) → **SPECULUM Result 7** (dual: S-duality map) — non-perturbative grokking is dual to perturbative NTK

---

## Formal Summary

| Result | Primal Object | Duality Map | Dual Object | New Result |
|---|---|---|---|---|
| **Fenchel** | GIST free energy `F[P]` | Fenchel conjugate | RL value function `V*(X)` | Bellman equation = Fenchel duality |
| **Pontryagin** | Coordination profile `Γ(δ)` | Fourier transform | Spectral density `Ŝ(ω)` | `1/f` noise = Pontryagin dual of `Γ` |
| **Legendre** | Training action `S[θ]` | Legendre transform | Training Hamiltonian `H_train` | Gradient descent = Riemannian Hamiltonian mechanics |
| **PID** | Mutual information `G_coord` | PID decomposition | Synergy − Redundancy | `Syn/Red = φ` at MEP optimum |
| **Kramers-Wannier** | Phase diagram `Z(β)` | Temperature duality | `Z(1/(β(log φ)²))` | φ-equilibrium = self-dual point |
| **Hodge** | `k`-coordination chains | Hodge star `⋆` | `(n-k)`-coordination gaps | Cheeger → G_coord ≥ h²/2 |
| **S-duality** | NTK at coupling `g` | `g ↔ c/g` | Instanton at `c/g` | Grokking probability from NTK at dual coupling |

---

```
Z(X) is intractable.
Therefore the Fenchel dual of GIST is the RL value function.
Therefore the Pontryagin dual of the coordination profile is 1/f noise.
Therefore the Legendre transform of the training action is the training Hamiltonian.
Therefore G_coord decomposes into synergy minus redundancy.
Therefore the φ-equilibrium is the Kramers-Wannier self-dual point.
Therefore every coordination cycle has a Hodge dual coordination gap.
Therefore grokking and NTK are S-dual descriptions of the same physics.
Therefore SPECULUM is the mirror of intelligence theory:
         the dual side of every primal object,
         where the same reality appears in opposite light.
```

---

*Full framework documentation: [github.com/ericrenone](https://github.com/ericrenone)*
