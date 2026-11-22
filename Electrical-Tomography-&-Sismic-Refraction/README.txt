
# Electrical Resistivity Tomography (ERT) and Seismic Refraction Tomography (SRT)

## Project Overview

This project focuses on the geophysical investigation of the subsurface using two complementary geophysical methods: **Seismic Refraction Tomography (SRT)** and **Electrical Resistivity Tomography (ERT)**.

The objective is to characterise the underground structure of a selected area by analysing the propagation velocity of seismic waves and the electrical resistivity distribution. Both methods provide complementary information that can be used to identify geological structures, material variations, and possible subsurface anomalies.

The experimental measurements were carried out in the gardens of the Faculty of Earth Sciences at the University of Barcelona, Spain.

## Objectives

The main objectives of this project are:

- Understand the physical principles behind seismic refraction and electrical resistivity tomography.
- Acquire and process geophysical field measurements.
- Obtain two-dimensional subsurface models using numerical inversion.
- Analyse the distribution of seismic wave propagation velocities and electrical resistivities.
- Compare the results from both methods and investigate possible correlations between their physical properties.

## Geophysical Methods

### 1. Seismic Refraction Tomography (SRT)

SRT is based on analysing the propagation of elastic waves through the subsurface.

A hammer and metal plate are used as the seismic source, generating waves that are detected by an array of 24 vertical geophones distributed along a 24-metre profile.

The first arrival times of P-waves are manually identified through a process known as *picking*. These measurements are subsequently used to perform a numerical inversion and reconstruct a two-dimensional model of seismic propagation velocities.

**Main acquisition parameters:**

| Parameter | Value |
|---|---|
| Number of geophones | 24 |
| Profile length | 24 m |
| Geophone spacing | 1 m |
| Natural frequency | 10 Hz |
| Hammer mass | 5 kg |
| Shot spacing | 3 m |
| Recording length | 128 ms |
| Sampling interval | 0.125 ms |

**Software:** PyCKSTER

### 2. Electrical Resistivity Tomography (ERT)

ERT determines the distribution of electrical resistivity in the subsurface by injecting an electrical current into the ground and measuring the resulting potential differences.

A total of 36 electrodes, separated by 1 metre, were installed along the survey profile.

Two electrode configurations were investigated:

- **Wenner-Schlumberger (W-S):** Provides a stronger and more stable signal, making it suitable for identifying horizontal variations and shallow structures.
- **Dipole-Dipole (D-D):** Provides higher lateral resolution and greater investigation depth, although it is generally more sensitive to noise.

The apparent resistivity measurements are processed using numerical inversion to obtain two-dimensional resistivity models.

**Software:** ResIPy

## Data Processing and Inversion

### SRT Processing

1. Import the seismic records into PyCKSTER.
2. Identify the first P-wave arrivals through manual picking.
3. Define the source and geophone positions.
4. Configure the travel-time inversion parameters.
5. Perform the numerical inversion.
6. Analyse the resulting velocity model and travel-time residuals.

### ERT Processing

1. Import the field measurements into ResIPy.
2. Filter anomalous measurements.
3. Estimate measurement noise using a linear error model.
4. Generate a triangular finite-element mesh.
5. Perform numerical inversion by solving Poisson's equation.
6. Evaluate the inversion quality using the RMS error.
7. Obtain the final two-dimensional resistivity sections.

**Coordinate correction:** The ERT electrode numbering follows the opposite direction to the SRT coordinate system. Therefore, the ERT data must be reversed before comparing both models spatially.

## Main Results

### Seismic Refraction Tomography

The SRT inversion reveals:

- Low propagation velocities near the surface, approximately between 300 and 400 m/s.
- Differences in propagation velocity at intermediate depths.
- Lower velocities near the northern end of the profile, around 380 m/s at approximately 4 metres depth.
- Faster propagation velocities in the central section of the profile.

The experimental configuration provides reliable information down to approximately 4–5 metres depth.

### Electrical Resistivity Tomography

The ERT inversion reveals several resistivity anomalies:

- A low-resistivity anomaly of approximately 10 Ω·m, located between 20 and 25 metres from the origin. This could be associated with saturated clay/silt materials or water pipes.
- A high-resistivity anomaly of approximately 150 Ω·m near the origin, potentially associated with concrete or foundations.

The two electrode configurations provide complementary information about the subsurface structure.

### Comparison Between SRT and ERT

Comparing both inversion models reveals a possible relationship between electrical and seismic properties:

- Regions of high electrical conductivity appear to overlap with areas of high seismic propagation velocity.
- Regions of higher electrical resistivity appear to coincide with areas of lower seismic propagation velocity.

These observations suggest a possible correlation between the electrical and seismic properties of the subsurface.

## Tools and Technologies

- **PyCKSTER:** Seismic data processing, first-arrival picking, and travel-time inversion.
- **ResIPy:** Electrical resistivity data processing and inversion.
- **Python:** Programming environment underlying the seismic processing software.
- **LaTeX:** Preparation and formatting of the practical report.

**Academic Year:** 2026–2027

## Acknowledgements

This project was developed as part of a practical geophysics course at the University of Barcelona, involving field data acquisition, geophysical data processing, numerical inversion, and interpretation of subsurface properties.

