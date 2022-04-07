# Plotting in Python with `matplotlib`

## Jupyter Noteboook

Code corresponding to these notes about custom functions in Python can be found in the `Plotting.ipynb` Jupyter notebook in this repository.

## Additional Resources

- [Rougier's `matplotlib` Tutorial](https://github.com/rougier/matplotlib-tutorial)
- [`matplotlib` Homepage](https://matplotlib.org/index.html)
- [`matplotlib` Usage Guide](https://matplotlib.org/tutorials/introductory/usage.html)
- [`matplotlib` Gallery](https://matplotlib.org/gallery.html)

## Introduction

`Matplotlib` is a Python module that's commonly used for plotting. There are different ways to interact with `matplotlib`, but we'll be relying on the `pyplot` submodule. To import this module, it's helpful to give it a shorter "nickname"

`import matplotlib.pyplot as plt`

When a module (or submodule) is imported with the `as` keyword, it gives us a different (hopefully shorter) name with which to reference it.

Another module that's commonly used when analyzing and plotting data is `numpy`

`import numpy as np`

## Our First Plot

To generate some coordinates for plotting, we'll start by using a `numpy` function that creates a series of numbers on a regular interval

`x = np.linspace(1,10,0.25)`

Now, we'll create `y` values by first setting them equal to the `x` values (using a deep copy)

`y = copy.copy(x)`

and then adding some random noise

```
for i in range(len(y)):
    y[i] = y[i] + np.random.normal(0,0.5,1)
```

To create a simple line plot, we can use the `.plot()` function of `pyplot`

`plt.plot(x,y)`

![plot1](https://raw.githubusercontent.com/FoundCompBio-Spr22/Plotting_Week10/main/images/plot1.png)
