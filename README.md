# ⚛️ ION-X: The Atomic Intelligence Lab

**Learn chemistry by thinking, not memorizing.**

ION-X is an interactive web lab that turns ionization energy from a memorization topic into a scientific investigation. You are given the successive ionization energies of a hidden atom. You analyze the data, find the jump, and work out which element it is.

🔗 **Live demo:** https://RAHAF-Mohamed08.github.io/ion-x/



---

## Why this project?

Most resources explain ionization energy or show solved examples. ION-X makes the student do the reasoning:

| Typical resources | ION-X |
| --- | --- |
| Explain the concept | Analyze unknown data |
| Solved examples | Discover the element yourself |
| Static charts | Algorithm that detects the jump |
| Fixed questions | Levels, score and streaks |

## Features

- **Mystery Lab:** a hidden element appears as a bar chart of IE₁, IE₂, IE₃… You identify its valence electrons, then the element itself.
- **Jump Detector:** an algorithm that finds the largest jump in successive ionization energies and highlights it on the chart.
- **Analyzer:** paste your own values (from a textbook or lab sheet) and get the predicted valence electrons, group and closest matching element.
- **Scientific explanations:** after every answer, the app explains why the jump happens and what it means for the atom’s structure.
- **Game system:** score, streak bonuses, levels and three difficulty modes (Groups 1–2, Groups 1–2 and 13–14, All elements).
- **Log / linear scale:** switch chart scales to see small and huge values clearly.
- **Light and dark themes**, fully responsive for mobile and desktop.
- **Zero dependencies:** one HTML file with plain HTML, CSS and JavaScript.

## How it works

Removing electrons from an atom gets harder each time. The energy rises slowly while valence electrons are removed, then jumps sharply once removal starts to break into the inner shell, which sits much closer to the nucleus.

ION-X detects this with a ratio test:

```text
ratio[i] = IE[i+1] / IE[i]
jump index = position of the largest ratio
valence electrons = jump index + 1
group = valence electrons (1–2) or valence electrons + 10 (3–8)
```

Example with sodium (kJ/mol):

| IE₁ | IE₂ | IE₃ |
| --- | --- | --- |
| 496 | 4562 | 6910 |

IE₂ / IE₁ = 9.2 is by far the largest ratio, so the jump comes after IE₁: **1 valence electron → Group 1 → sodium (Na)**.

To pick the exact element within a group, the Analyzer compares your IE₁ to the elements in that group. IE₁ decreases going down a group because the outer electron is farther from the nucleus.

## Data

The dataset covers 18 elements (Li to Ne, Na to Ar, plus K and Ca) with rounded successive ionization energies in kJ/mol, based on standard reference tables. Values are for educational use.

To add an element, append an object to the `EL` array in `index.html`:

```js
{ s: "Na", n: "Sodium", v: 1, ie: [496, 4562, 6910] }
```

- `s`: symbol
- `n`: name
- `v`: number of valence electrons
- `ie`: successive ionization energies in kJ/mol (include at least `v + 2` values so the jump is visible)

## Run locally

No build step is needed.

```bash
git clone https://github.com/YOUR-USERNAME/ion-x.git
cd ion-x
# open index.html in your browser
```

## Deploy with GitHub Pages

1. Go to **Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select **main** and **/ (root)**, then **Save**.
4. Your site will be live at `https://YOUR-USERNAME.github.io/ion-x/`.

## Project structure

```text
ion-x/
├── index.html   # app: markup, styles, data and logic
├── README.md
└── LICENSE
```

## Tech stack

- HTML5 and CSS3 (custom properties, responsive layout, light/dark theming)
- Vanilla JavaScript (ES6)
- Inline SVG for charts

## Roadmap

- [ ] Add more elements (periods 4–5 and transition metals)
- [ ] Add hydrogen-like ions and a "which period?" challenge
- [ ] Arabic / English language switch
- [ ] Timed challenge mode and a local leaderboard
- [ ] Export results as a worksheet for teachers
- [ ] Unit tests for the detection algorithm

## Screenshots

Add screenshots of the Mystery Lab and Analyzer here, for example:

```md
![Mystery Lab](docs/mystery-lab.png)
```

## Contributing

Ideas and pull requests are welcome. Open an issue to discuss a change, then fork the repo, create a branch and submit a pull request.

## License

Released under the [MIT License](LICENSE).

---

Made for students who prefer to figure things out.
