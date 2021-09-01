---
title: Visualizing Tabular Data
teaching: 15
exercises: 0
questions:
- "How can I visualize tabular data in Python?"
- "How can I group several plots together?"
objectives:
- "Plot simple graphs from data."
- "Group several graphs in a single figure."
keypoints:
- "Use the `pyplot` module from the `matplotlib` library for creating simple visualizations."
---

## Visualizing data
The mathematician Richard Hamming once said, "The purpose of computing is insight, not numbers," and
the best way to develop insight is often to visualize data.  Visualization deserves an entire
lecture of its own, but we can explore a few features of Python's `matplotlib` library here.  While
there is no official Python plotting library, `matplotlib` is the _de facto_ standard.  First, we will
import the `pyplot` module from `matplotlib` and use two of its functions to create and display a
heat map of our data:

~~~
from matplotlib import pyplot
~~~
{: .language-python}

Note the slightly different grammar this time for the `import` statement. 
Using `from` we import the library `matplotlib.pyplot` so that we don't import every module in `matplotlib` but just the plotting module.

Furthermore, with this grammar we only have to call it `pyplot`. 
We could have abbreviated more by using a shortcut, e.g., to refer to the `matplotlib.pyplot` library as just `plt`, we could use either: 

`from matplotlib import pyplot as plt`

`import matplotlib.pyplot as plt`

Now let's plot the medical data we read previously:

~~~
image = pyplot.imshow(data)
pyplot.show()
~~~
{: .language-python}

![Heatmap of the Data](../fig/inflammation-01-imshow.svg)

Blue pixels in this heat map represent low values, while yellow pixels represent high values.  As we
can see, inflammation rises and falls over a 40-day period.  

To continue, close the plot window.

Let's take a look at the average inflammation over time:

~~~
ave_inflammation = numpy.mean(data, axis=0)
ave_plot = pyplot.plot(ave_inflammation)
pyplot.show()
~~~
{: .language-python}

![Average Inflammation Over Time](../fig/inflammation-01-average.svg)

Here, we have put the average inflammation per day across all patients in the variable `ave_inflammation`, then
asked `matplotlib.pyplot` to create and display a line graph of those values.  The result is a
roughly linear rise and fall, which is suspicious: we might instead expect a sharper rise and slower
fall.  Let's have a look at two other statistics:

~~~
max_plot = pyplot.plot(numpy.max(data, axis=0))
pyplot.show()
~~~
{: .language-python}

What is this showing?  Can you deduce it from the name of the `numpy` function? 

How about if you try the `numpy.std` method?

~~~
std_plot = pyplot.plot(numpy.std(data, axis=0))
pyplot.show()
~~~
{: .language-python}

{% include links.md %}
