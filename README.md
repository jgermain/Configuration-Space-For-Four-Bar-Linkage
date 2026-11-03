# Configuration Space for a Four-Bar Linkage

This project is a web-based recreation of the Wolfram Mathematica **Configuration Space for Four-Bar Linkage** demonstration.

It was developed for an Intro to Robotics assignment using AI-assisted code generation followed by testing, debugging, and mathematical validation.

## Overview

The application allows the user to explore the configuration space of a planar four-bar linkage.

The left side displays the reachable combinations of the joint angles \( \theta \) and \( \phi \), while the right side shows the corresponding physical linkage.

Users can adjust the link dimensions and drag the locator on the configuration-space plot to explore different valid robot configurations.

## Features

- Interactive configuration-space plot
- Physical four-bar linkage visualization
- Adjustable \(L_1\), \(L_2\), \(L_3\), and \(L_4\)
- Two physical assembly branches
- Interactive \( \theta \)-\( \phi \) locator
- Automatic detection of impossible link combinations
- Correct handling of straight/degenerate configurations
- Angle wrapping from \(-\pi\) to \(+\pi\)
- Numerical loop-closure verification
- Standalone HTML/JavaScript implementation
- No Mathematica installation required

## Kinematics

For a selected value of \( \theta \), the endpoint of \(L_1\) is first calculated.

The shared joint between \(L_2\) and \(L_3\) is then found using the intersection of two circles:

- radius \(L_2\) centered at the endpoint of \(L_1\)
- radius \(L_3\) centered at the right ground pivot

The value of \( \phi \) is then calculated directly from the resulting \(L_3\) vector using `atan2`.

Using the same geometry for both the configuration-space calculation and the linkage drawing ensures that the plotted angles and displayed mechanism remain consistent.

## Straight-Arm Limit Case

One important edge case occurs when one link is exactly equal to the sum of the other three links.

In this situation, the linkage has exactly one valid collinear configuration.

During testing, the original Mathematica implementation could display a distorted-looking linkage for some of these cases. This implementation instead displays the physically correct straight configuration.

If one link becomes longer than the sum of the other three, the application correctly reports that no closed configuration is possible.

## Running the Project

Clone or download the repository and open the HTML file in a modern web browser.

No installation, package manager, or external library is required.

## Validation

The final implementation was tested against the original Wolfram Demonstration and its underlying four-bar linkage equations.

Testing included:

- normal configurations
- both assembly branches
- tangent configurations
- straight-arm limiting cases
- impossible link combinations
- angle-wrap boundaries
- singular configurations
- numerical loop-closure checks

The physical circle-intersection solver was also compared against the original analytic four-bar equations and produced matching results to numerical precision for tested nonsingular cases.

## Original Demonstration

Wolfram Demonstrations Project:

**Configuration Space for Four-Bar Linkage**

https://demonstrations.wolfram.com/ConfigurationSpaceForFourBarLinkage/
