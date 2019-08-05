# pysolarRadiation

[![Build Status](https://travis-ci.com/aqreed/pysolarRadiation.svg?branch=master)](https://travis-ci.com/aqreed/pysolarRadiation)
[![codecov.io](https://codecov.io/gh/aqreed/pysolarRadiation/branch/master/graph/badge.svg)](https://codecov.io/gh/aqreed/pysolarRadiation/branch/master)
[![license](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](https://github.com/aqreed/pysolarRadiation/raw/master/COPYING)

|  |  |
| ------ | ------ |
| Description | Python Solar Radiation model |
| Author | aqreed |
| Version | 0.2.dev0 |
| Python Version | 3.6 |
| Requires | Numpy, Matplotlib, scikit-aero |

This packages aims to provide a reliable solar radiation model, mainly based on the work of Duffie, J.A., and Beckman, W. A., 1974, "Solar energy thermal processes".

The main purpose is to generate a **solar beam irradiance** (W/m2) prediction on:
* **any plane**, thanks to the calculation of the solar vector in NED (North East Down) coordinates, suitable for its use in flight dynamics simulations...
* **any place of the earth**, taking into account the solar time wrt the standard time, the latitude effect on solar azimuth and altitude as well as sunset/sunrise time and hour angle, etc.
* **any day of the year**, taking into account the variations of the extraterrestrial radiation, the equation of time, the declination, etc., throughout the year

Solar [irradiance](https://en.wikipedia.org/wiki/Solar_irradiance) on the southern hemisphere on October 17, at sea-level 13.01UTC (plane pointing upwards)?

```
import pysolar.radiation as psr

vnorm = np.array([0, 0, -1])  # plane pointing zenith
h = 0  # sea-level
n = psr.day_of_the_year(10, 17)  # October 17
lat = -13.1  # southern hemisphere
hour, minute = 13, 1  # midday

i = psr.irradiance_on_plane(vnorm, h, n, lat, hour, minute)

print(i)
```

A dedicated Jupyter Notebook on beam irradiance can be found [here](https://github.com/aqreed/pysolarRadiation/blob/master/examples/solar_irradiance.ipynb).

Solar [declination](https://en.wikipedia.org/wiki/Position_of_the_Sun#Declination_of_the_Sun_as_seen_from_Earth) on August 5?

```
import pysolar.radiation as psr

n = psr.day_of_the_year(8, 5)  # August 5
dec = psr.declination(n)

print(dec)
```

Please find more notebooks on the 'examples' folder.

### Dependencies

This package depends on Python, NumPy and scikit-aero and is usually tested on Linux with the following versions:

Python 3.6, NumPy 1.16, scikit-aero0.2.dev0

### Installation

pysolarRadiation has been written in Python3

```sh
$ git clone https://github.com/aqreed/pysolarRadiation.git
$ cd pysolarRadiation
$ pip install -e . -r requirements.txt
```

### Testing

pysolarRadiation recommends py.test for running the test suite. Running from the top directory:

```sh
$ pytest
```

### License

MIT (see `COPYING`)