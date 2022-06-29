# Class 14

## Matplotlib tutorial

### What is Matplotlib

matplotlib is probably the single most used Python package for 2D-graphics.
It provides both a very quick way to visualize data from Python and publication-quality figures in many
formats. We are going to explore matplotlib in interactive mode covering most common cases.

### IPython

IPython is an enhanced interactive Python shell that has lots of interesting features including named inputs
and outputs, access to shell commands, improved debugging and much more. It allows interactive matplotlib
sessions that have Matlab/Mathematica-like functionality.

### Pyplot

pyplot provides a convenient interface to the matplotlib object-oriented plotting library.
It is modeled closely after Matlab(TM). Therefore, the majority of plotting commands in pyplot have
Matlab(TM) analogs with similar arguments. Important commands are explained with interactive examples.

---
Ex:

```python
import numpy as np

X = np.linspace(-np.pi, np.pi, 256, endpoint=True)
C, S = np.cos(X), np.sin(X)

plt.figure(figsize=(10,6), dpi=80)
plt.plot(X, C, color="blue", linewidth=2.5, linestyle="-")
plt.plot(X, S, color="red",  linewidth=2.5, linestyle="-")
```

### Figures

A figure is the windows in the GUI that has "Figure #" as title. Figures are numbered starting from 1 as
opposed to the normal Python way starting from 0. This is clearly MATLAB-style. There are several parameters
that determine what the figure looks like:

edgecolor figure.edgecolor color of edge around the drawing background
frameon True draw figure frame or not

| Argument  | Default          | Description                                 |
|-----------|------------------|---------------------------------------------|
| num       | 1                | number of figure                            |
| figsize   | figure.facecolor | figure size in in inches (width, height)    |
| dpi       | figure.dpi       | resolution in dots per inch                 |
| facecolor | figure.facecolor | color of the drawing background             |
| edgecolor | figure.edgecolor | color of edge around the drawing background |
| frameon   | True             | draw figure frame or not                    |

### Subplots

With subplot you can arrange plots in a regular grid. You need to specify the number of rows and columns
and the number of the plot. Note that the gridspec command is a more powerful alternative.

### Axes

Axes are very similar to subplots but allow placement of plots at any location in the figure.
So if we want to put a smaller plot inside a bigger one we do so with axes.

### Ticks

Well formatted ticks are an important part of publishing-ready figures.
Matplotlib provides a totally configurable system for ticks.
There are tick locators to specify where ticks should appear and tick formatters to give ticks the
appearance you want. Major and minor ticks can be located and formatted independently from each other.
By default minor ticks are not shown, i.e. there is only an empty list for them because it is as NullLocator

#### Tick Locators

* NullLocator
  * No ticks.
* IndexLocator
  * Place a tick on every multiple of some base number of points plotted.

* FixedLocator
  * Tick locations are fixed.

* LinearLocator
  * Determine the tick locations.

* MultipleLocator
  * Set a tick on every integer that is multiple of some base.

* AutoLocator
  * Select no more than n intervals at nice locations.

* LogLocator
  * Determine the tick locations for log axes.

### Animation

 animation in matplotlib was not an easy task and was done mainly through clever hacks. However,
 things have started to change since version 1.1 and the introduction of tools for creating animation very
 intuitively, with the possibility to save them in all kind of formats (but don't expect to be able to run
 very complex animations at 60 fps though).

> The most easy way to make an animation in matplotlib is to declare a FuncAnimation object that specifies
to matplotlib what is the figure to update, what is the update function and what is the delay between frames.

### Drip drop

A very simple rain effect can be obtained by having small growing rings randomly positioned over a figure.
Of course, they won't grow forever since the wave is supposed to damp with time. To simulate that, we can use
a more and more transparent color as the ring is growing, up to the point where it is no more visible. At this
point, we remove the ring and create a new one.

### There is much more see the Resource

### [Source](https://github.com/rougier/matplotlib-tutorial)

---

## Bokeh Tutorial

Bokeh is an interactive visualization library that targets modern web browsers for presentation
. It is good for:

* Interactive visualization in modern browsers
* Standalone HTML documents, or server-backed apps
* Expressive and versatile graphics
* Large, dynamic or streaming data
* Easy usage from python (or Scala, or R, or...)

And most importantly:
Bokeh is an interactive visualization library for modern web browsers. It provides elegant,
concise construction of versatile graphics, and affords high-performance interactivity over large or
streaming datasets. Bokeh can help anyone who would like to quickly and easily make interactive plots,
dashboards, and data applications.

## [Source](https://notebooks.gesis.org/binder/jupyter/user/bokeh-bokeh-notebooks-34ctsw0e/notebooks/tutorial/01%20-%20Basic%20Plotting.ipynb)

---

## Also, I reviewed the seaborn tutorial

from this [Source](https://seaborn.pydata.org/tutorial.html)
