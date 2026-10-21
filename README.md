# Skyrmion-Based Physical Reservoir Computing

A computational study of spin-orbit-torque-driven skyrmion dynamics in a dumbbell-shaped Pt/Co bilayer for physical reservoir computing and handwritten-digit classification.

**Author:** Efe Kaan Tağa  
**Institution:** Boğaziçi University, Department of Physics  
**Supervisor:** Prof. Özhan Özatay  
**Course:** PHYS491 - Introduction to Research in Physics I

## Project report

[Read the full project report](report.pdf)

The report presents the physical background, device geometry, simulation methodology, extracted skyrmion states, and classification results. A representative OOMMF input file, Mathematica state-extraction code, and Python classification code are included in its appendices.

## Workflow

1. **Electromagnetic modeling:** Calculate spatial current-density and Oersted-field distributions using COMSOL Multiphysics.
2. **Micromagnetic simulation:** Transfer the distributions to OOMMF and simulate skyrmion dynamics driven by bipolar current pulses.
3. **Input encoding:** Simulate all 16 four-bit sequences, with `1` encoded as a positive current pulse and `0` as a negative current pulse.
4. **State extraction:** Extract the final skyrmion position `(x, y)` and effective radius `r` using Mathematica.
5. **Classification:** Map four-bit groups from binarized MNIST images to a fixed lookup of simulated states and train a logistic-regression readout using Python and scikit-learn.

Only the software readout is trained; the 16 simulated reservoir states remain fixed.

## Reported results

MNIST classification uses 60,000 training images and 10,000 test images.

| Input representation | Test accuracy |
| --- | ---: |
| Raw binary pixels | 91.29% |
| Four-bit integer codes | 89.39% |
| Skyrmion position `x` | 87.48% |
| Skyrmion features `(x, y, r)` | **90.27%** |

The combined `(x, y, r)` representation gives the highest accuracy among the physical feature combinations evaluated in the report.

## Software used

- COMSOL Multiphysics
- OOMMF
- Wolfram Mathematica
- Python, NumPy, and scikit-learn

## Research context

The device and reservoir framework follows:

W. Jiang et al., "Physical reservoir computing using magnetic skyrmion memristor and spin torque nano-oscillator," *Applied Physics Letters* **115**, 192403 (2019).

This project investigates the use of skyrmion position and radius as reservoir features within that framework. Full references and model limitations are provided in the report.

