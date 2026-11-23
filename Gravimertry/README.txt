SEISMIC REFRACTION ANALYSIS - README

OVERVIEW
This project analyzes seismic refraction survey data to estimate subsurface properties using inverse methods. The notebook loads geophone recordings, visualizes travel-time data, and applies linear regression to determine seismic wave velocities and the thickness of the first subsurface layer.

BACKGROUND
In seismic refraction surveys, waves travel through the subsurface via different paths:

- Direct waves: Travel along the surface.
- Reflected waves: Bounce off deeper interfaces.
- Refracted waves: Travel along deeper, faster layers and return to the surface.

These paths have different lengths and velocities, so they arrive at geophones at different times, producing a travel-time curve with distinct regimes (slopes) that reveal subsurface structure.

DATA
- Input file: data.txt
- Format: Two columns - geophone offset (m) and recording time (s).
- Loaded with numpy.loadtxt.
- First column = response.
- Second column = time.

WORKFLOW

1. DATA VISUALIZATION
Plots geophone offset against recording time to inspect the travel-time curve and identify propagation regimes.

2. VELOCITY AND LAYER THICKNESS ESTIMATION
Two linear regressions are fitted to the separate propagation regimes (first 11 points and remaining points):

- v1 = slope of first regime (velocity in first layer).
- v2 = slope of second regime (velocity in second layer).

Layer thickness formula:

h = (-b2 / (2*v2)) * (v2*v1 / sqrt(v2^2 - v1^2))

Where b2 is the intercept of the second regression.

Fitted lines are overlaid on the observed data to confirm the two regimes.

RESULTS
- Velocity in first medium (v1): 500 m/s
- Velocity in second medium (v2): 1500 m/s
- Thickness of first layer (h): 20 m

REQUIREMENTS
- Python 3.13 (XPython kernel)
- numpy
- matplotlib
- scipy

USAGE
1. Place data.txt in the working directory (two columns: offset, time).
2. Run the notebook cells in order:

   Cell 1: Loads data and plots the raw travel-time curve.

   Cell 2: Fits the two regimes, computes velocities and layer thickness, and plots the fitted lines.

NOTES AND CAVEATS
- Regime boundaries (indices [:11] and [12:]) are hardcoded to this dataset; adjust for other surveys.
- Velocities and thickness are cast to int, which rounds results. Remove int() calls if higher precision is needed.
- linregress(..., alternative='greater') applies a one-sided test, expecting positive slopes.
- The formula assumes a two-layer model with a planar interface and the standard crossover-distance relationship.

FILE STRUCTURE
- data.txt       : Raw survey data (offset, time)
- analysis.ipynb : Notebook with visualization and inversion
- README.md      : Project documentation
