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

Now, let's say we want to label our axes (which, as good scientists we should always do!). We can call the `.xlabel()` and `.ylabel()` functions from `pyplot` before we call `.plot()`.

```
plt.ylabel("Distance")
plt.xlabel("Day")
plt.plot(x,y)
```

![plot2](https://raw.githubusercontent.com/FoundCompBio-Spr22/Plotting_Week10/main/images/plot2.png)

Ok, this is looking better, but now we'd like to know how the observed trend compares to a line with slope 1 and intercept 0. We can add a second line to our plot with the x values on both axes.

```
plt.ylabel("Distance")
plt.xlabel("Day")
plt.plot(x,y)
plt.plot(x,x)
```

![plot3](https://raw.githubusercontent.com/FoundCompBio-Spr22/Plotting_Week10/main/images/plot3.png)

Note how `matplotlib` automagically changes the color of our 2nd line to be different than the first.

I actually really like these defaults, but let's say that we have a good reason that we want to make some changes. First, we want our 1:1 line underneath and we want it to be a blue, dashed line. For our data, we want to try red dots. `pyplot` let's us pass a third argument to `.plot()` that will adjust the color and style of plotting. The first letter (`b` or `r` here) will set the color and the next symbols (`o` or `--` here) change the plotting style.

```
plt.ylabel("Distance")
plt.xlabel("Day")
plt.plot(x,x,'b--')
plt.plot(x,y,'ro')
```

![plot4](https://raw.githubusercontent.com/FoundCompBio-Spr22/Plotting_Week10/main/images/plot4.png)

Here's a variant that uses a dotted 1:1 line.

```
plt.ylabel("Distance")
plt.xlabel("Day")
plt.plot(x,x,'b:')
plt.plot(x,y,'ro')
```

![plot5](https://raw.githubusercontent.com/FoundCompBio-Spr22/Plotting_Week10/main/images/plot5.png)

Ok, I actually prefer the solid 1:1 line, so let's go back to that, but let's make the line thicker.

```
plt.ylabel("Distance")
plt.xlabel("Day")
plt.plot(x,x,'b',linewidth=3)
plt.plot(x,y,'ro')
```

![plot6](https://raw.githubusercontent.com/FoundCompBio-Spr22/Plotting_Week10/main/images/plot6.png)

In many cases, we have multiple groups that we want to depict in a single scatter plot. In this case, we can use two `.plot()` calls back-to-back and `matplotlib` will color the two groups separately.

```
x_1 = np.random.normal(5,1,300)
y_1 = np.random.normal(5,1,300)

x_2 = np.random.normal(7,1,300)
y_2 = np.random.normal(7,1,300)

plt.plot(x_1,y_1,'o')
plt.plot(x_2,y_2,'o')
plt.xlabel("Trait 1")
plt.ylabel("Trait 2")
```

![plot7](https://raw.githubusercontent.com/FoundCompBio-Spr22/Plotting_Week10/main/images/plot7.png)

Because the two groups overlap some and the points are relatively large, it can be difficult to see some points. In this case, we may want to reduce the sizes of the points using the `markersize` argument. We can also make the symbols different between the groups to make them more distinctive.

```
x_1 = np.random.normal(5,1,300)
y_1 = np.random.normal(5,1,300)

x_2 = np.random.normal(7,1,300)
y_2 = np.random.normal(7,1,300)

plt.plot(x_1,y_1,'^',markersize=3)
plt.plot(x_2,y_2,'o',markersize=3)
plt.xlabel("Trait 1")
plt.ylabel("Trait 2")
```

![plot8](https://raw.githubusercontent.com/FoundCompBio-Spr22/Plotting_Week10/main/images/plot8.png)
