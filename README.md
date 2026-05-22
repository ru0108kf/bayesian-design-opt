# bayesian design opt

## Abstract

Recent advancements in CAD applications have improved access to parametric design, however, their optimization methods predominantly emphasize quantitative metrics such as environmental or structural performance. Consequently, for subjective aspects, designers rely on manual "slider" adjustment, which is often inefficient, susceptible to cognitive biases, and can lead to confinement within local optima. This study proposes a human-centric computational design framework that integrates human-in-the-loop and Bayesian optimization (BO) to incorporate subjective evaluation into the design process. We demonstrated this framework using a pavilion design task defined by six parameters and evaluated it via a user study (N = 40) comparing the proposed "Bayesian method" with the conventional "slider-based" method. Results showed that the Bayesian method outperformed the slider-based method in terms of final design selection, overall satisfaction, and perceived design diversity. It helped users discover their latent preferences by exploring parameter regions that might have been overlooked manually. Furthermore, the "transparency" of the BO process was essential for fostering user trust and maintaining their sense of agency. This approach is a promising interactive tool for facilitating exploratory design in the early stages, particularly for users with uncertain preferences.

**Note:** The code in this repository was created for research purposes. Please note that it contains experimental features and may not work as intended in all environments, but I hope you find it useful as a reference.

## Prerequisites

* Rhino 7 or 8 / Grasshopper
* Python 3.9
* [uv](https://docs.astral.sh/uv/getting-started/installation/)
* [Hops](https://www.food4rhino.com/en/app/hops)
* [Human-UI](https://www.food4rhino.com/en/app/human-ui)

## Getting Started

Install dependencies:

```bash
uv sync
```

Copy `.env.example` to `.env` and set your path:

```bash
cp .env.example .env
```

Edit `.env`:

```.env
SAVE_FOLDER_PATH=C:\path\to\your\save_folder
```

## How to Use

Open the Grasshopper file (`tutorials.gh`), then run the server:

```bash
uv run main.py
```

If you see

```note
 * Running on http://127.0.0.1:5000
[INFO] Press CTRL+C to quit
```

everything is working correctly.

Feel free to modify the pavilion part in the tutorial to your liking and experiment with it!

## Contributions

We welcome bug reports and feature requests via GitHub Issues. Pull requests are also highly appreciated.

-----

**Developer**: [ru0108kf]
