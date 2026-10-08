# Math 23 · AI-Assignment 4: The Ellipsoid Grill

Open `ellipsoid-grill.html` in a browser (it needs internet to load three.js). Drag to rotate, use the sliders for `a` and `b`, and press **Cook**.

## Geometry

The grill is the ellipsoid of revolution about the z-axis

    z²/a² + (x² + y²)/b² = 1,   a > b > 0

- Foci: `c = √(a² − b²)`. Coals at `F₁(0, 0, −c)`, food at `F₂(0, 0, +c)`.
- Eccentricity `e = c/a`. A ray from `F₁` that reflects off the wall passes through `F₂`.
- Traces:
  - `z = 0` (xy-plane): `x² + y² = b²`, a circle of radius `b` (the rim).
  - `x = 0` (zy-plane): `y²/b² + z²/a² = 1`, an ellipse.
  - `y = 0` (xz-plane): `x²/b² + z²/a² = 1`, the same ellipse turned 90°.
  - At a focus (`z = ±c`) the cross-section is a circle of radius `b²/a`.
- If `a < b` the surface is flattened (oblate) and has no foci on the z-axis, so the sliders keep `b ≤ a − 1`.

Example with `a = 40`, `b = 30`: `z²/1600 + (x² + y²)/900 = 1`, `c = √700 ≈ 26.46 cm`, foci at `(0, 0, ±26.46)`, `e ≈ 0.661`.

## Model

| Quantity | Formula | Assumption used |
|---|---|---|
| Surface area | `S = 2πb²[1 + (a/(b·e))·arcsin e]` | full closed shell |
| Efficiency | `η = 0.4 + 0.5e` | |
| Cooking time | `T = T₀·(qty/qty₀)/η` | `T₀ = 6 min`, `qty₀ = 4` |
| Capacity | hexagonal packing of 4-in (10.16 cm) patties on a disc of area `πb²` | |
| Cost | `S·price + hardware` | `$85/m²`, `$40` hardware |
| Doneness | core reaches 135 °F (medium rare, 130–135 °F) from 40 °F | |

The assumption values can be changed in the page under "Model assumptions".

## Comparison (full load)

| Design | a (cm) | b (cm) | c (cm) | e | η | S (m²) | Max burgers | Time (min) | min/burger | Cost ($) | $/burger slot |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Tall | 50 | 30 | 40.00 | 0.800 | 0.800 | 1.658 | 23 | 43.1 | 1.88 | 181 | 7.87 |
| Default | 40 | 30 | 26.46 | 0.661 | 0.731 | 1.389 | 23 | 47.2 | 2.05 | 158 | 6.87 |
| Round-ish | 36 | 33 | 14.39 | 0.400 | 0.600 | 1.452 | 31 | 77.5 | 2.50 | 163 | 5.27 |
| Slim | 50 | 20 | 45.83 | 0.917 | 0.858 | 1.046 | 8 | 14.0 | 1.75 | 129 | 16.11 |
| Large | 60 | 45 | 39.69 | 0.661 | 0.731 | 3.126 | 58 | 119.1 | 2.05 | 306 | 5.27 |

## Conclusions

- **Capacity depends only on `b`.** The grate area is `πb²`, so a wider grill holds more burgers. Making the grill taller (larger `a`) adds no capacity.
- **Focusing depends on the shape ratio.** A larger `a/b` raises `e`, which raises `η` and cuts the time per burger. The slim grill (e = 0.917) is the fastest per burger and the cheapest to build, but it holds only 8.
- **Total cooking time grows with the load.** With `T` linear in `qty`, the large grill takes about 2 hours to cook 58 burgers. The round-ish grill (e = 0.40) has the worst focusing and the slowest time per burger.
- **Cost per burger slot falls as `b` grows**, because the shell area grows more slowly than the packing area. The large and round-ish designs are the cheapest per slot (about $5.27).
- **Trade-off:** pick a large `a/b` for speed, a large `b` for capacity. The tall design (a = 50, b = 30) keeps the default capacity of 23 while cutting the time by about 9% for $23 more.

## AI prompt used

The simulation was generated from the assignment's sample prompt ("Create a single-file HTML/JS interactive 3D simulation titled 'The Ellipsoid Grill' …") with the setup, controls, display, and model assumptions listed in the assignment. Additions: live equation, foci, and trace readouts; a burgers-to-cook slider; editable assumptions; a packing top view; and a comparison table.
