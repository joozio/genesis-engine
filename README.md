# Genesis Engine

**Particle life simulation — simple rules, complex life**

A real-time particle life simulation running entirely in the browser. Five particle species interact through an attraction/repulsion matrix, producing emergent self-organizing behavior from purely local rules — no central control, no pre-programmed structure. Just physics.

**[Live Demo →](https://wiz.jock.pl/experiments/genesis-engine)**

---

## What You'll See

Depending on the preset, particles will spontaneously:

- Self-organize into **cell-like membranes** with interior/exterior dynamics
- Form **rotating galaxies** and gravitational spirals
- Play out **predator/prey chase** dynamics across the entire field
- Reach **symbiotic equilibrium** — species that need each other
- Dissolve into pure **chaos** with maximum entropy

Each behavior emerges entirely from the 5×5 interaction matrix. Change one number and the universe reorganizes.

---

## How It Works

### Particle Life Algorithm

Each particle belongs to one of 5 species. Every frame, for each particle:

1. Scan all other particles within `INTERACTION_RADIUS = 120px`
2. Look up the attraction strength between the two species from the matrix
3. Apply a force: **repulsion** below `MIN_DIST = 20px`, **attraction/repulsion** beyond (shaped by a smooth curve peaking at ~30% of the interaction radius)
4. Apply friction `0.92` to velocity — energy dissipates, patterns stabilize
5. Wrap position toroidally (edges connect)

```
matrix[A][B] = +0.8  →  A is strongly attracted to B
matrix[A][B] = -0.5  →  A actively avoids B
matrix[A][B] = 0.0   →  A is indifferent to B
```

The matrix is **asymmetric**: A can chase B while B flees A (predator preset).

### Physics Constants

| Constant | Value | Effect |
|---|---|---|
| `FRICTION` | 0.92 | Energy dissipation — patterns stabilize |
| `MAX_FORCE` | 1.2 | Prevents explosive acceleration |
| `INTERACTION_RADIUS` | 120px | Neighborhood size |
| `MIN_DIST` | 20px | Hard-core repulsion zone |

### The 5 Species

| Species | Color |
|---|---|
| Pink | `#ff6b9d` |
| Cyan | `#00ffff` |
| Yellow | `#ffd93d` |
| Green | `#6bcb77` |
| Purple | `#a855f7` |

---

## Presets

| Preset | Behavior |
|---|---|
| **Cells** | Self-organizing cellular structures with membrane dynamics |
| **Galaxies** | Swirling gravitational spirals with rotational momentum |
| **Predators** | Cyclic chase dynamics — each species hunts one, flees another |
| **Symbiosis** | Mutual attraction, fragile interdependent balance |
| **Chaos** | Maximum entropy, minimum order |
| **Random** | Randomized matrix — discover your own emergent patterns |

---

## Controls

| Control | What it does |
|---|---|
| Preset buttons | Switch interaction matrix and respawn particles |
| ⏸ Play/Pause | Freeze/resume simulation |
| ↺ Reset | Respawn particles with current matrix |
| Speed slider | 0.2× to 3× simulation speed |
| Count slider | 100 to 1000 particles |
| Trails toggle | Fade effect vs. clean render |
| Attract / Repel | Click/drag on canvas to push or pull particles |
| DNA matrix | Edit the 5×5 interaction matrix directly |

---

## Running Locally

```bash
# Clone
git clone https://github.com/joozio/genesis-engine.git
cd genesis-engine

# Open in browser — no build step needed
open index.html
```

That's it. Single HTML file, zero dependencies, zero build tools.

---

## Screenshot

When running the **Galaxies** preset, you'll see five distinct rotational clusters slowly spiraling and exchanging particles across their boundaries — each galaxy maintaining internal structure through the circulant matrix pattern.

**Cells** produces the most visually striking result: tightly-packed clusters that develop visible boundaries, with some species confined to interior roles and others forming the outer membrane.

---

## Background

Particle life was popularized by [Jeffery Ventrella](http://www.ventrella.com/) and later explored by [Tom Mohr](https://particle-life.com/) and others in the artificial life community. The core insight: you don't need complex rules to get complex behavior. Local pairwise interactions between simple agents are sufficient to produce structures that look uncannily biological.

The algorithm here follows the formulation described in the particle-life.com research, adapted for smooth browser rendering with DPR-aware canvas scaling, toroidal boundary conditions, and an interactive DNA matrix editor.

---

## Built With

- Vanilla JavaScript
- HTML5 Canvas API
- Zero dependencies
- Zero build tools

Works in any modern browser. Mobile-friendly with touch support.

---

*Built by [Pawel Jozefiak](https://pawel-jozefiak.jock.pl) · Inspired by artificial life research*
