# bayesian design opt
### abstruct
Recent advancements in CAD applications have improved access to parametric design, however, their optimization methods predominantly emphasize quantitative metrics such as environmental or structural performance. Consequently, for subjective aspects, designers rely on manual "slider" adjustment, which is often inefficient, susceptible to cognitive biases, and can lead to confinement within local optima. This study proposes a human-centric computational design framework that integrates human-in-the-loop and Bayesian optimization (BO) to incorporate subjective evaluation into the design process. We demonstrated this framework using a pavilion design task defined by six parameters and evaluated it via a user study (N = 40) comparing the proposed "Bayesian method" with the conventional "slider-based" method. Results showed that the Bayesian method outperformed the slider-based method in terms of final design selection, overall satisfaction, and perceived design diversity. It helped users discover their latent preferences by exploring parameter regions that might have been overlooked manually. Furthermore, the "transparency" of the BO process was essential for fostering user trust and maintaining their sense of agency. This approach is a promising interactive tool for facilitating exploratory design in the early stages, particularly for users with uncertain preferences.

## Getting Started

To get started, simply install the required dependencies using pip.

```bash
python3.9 -m venv bayesian-design-opt

# Windows
bayesian-design-opt\Scripts\activate
# macOS/Linux
source bayesian-design-opt/bin/activate

pip install requirements.txt
```

anaconda

```bash
conda create -n bayesian-design-opt python=3.9

conda activate bayesian-design-opt

conda install requirements.txt
```

## How to Use
Please replace the specified part in `main.py` with your own path.
Open the Grasshopper file (`tutorial.gh`), then open the terminal (Anaconda Prompt) and activate your virtual environment.
Type the following command:

```
python main.py
```

If you see

```
 * Running on http://127.0.0.1:5000
[INFO] Press CTRL+C to quit
```

it means everything is working correctly.

Feel free to modify the pavilion part in the tutorial to your liking and experiment with it!

## Contributions

We welcome bug reports and feature requests via GitHub Issues. Pull requests are also highly appreciated.

-----

**Developer**: [ru0108kf]
