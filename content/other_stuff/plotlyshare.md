---
title: "PlotlyShare"
description: "Link-based sharing of `plotly` plots with a private web app"
date: 2024-06-18
tags: ["plotly", "collaboration", "link sharing"]
lang: python
cover:
  image: plotlyshare-main-combined.png
  caption: Screenshots of the admin dashboard
  relative: true
accent: "#e685b5"
---

# `plotlyshare`

The purpose of this package is to provide a seamless way to share interactive `plotly` plots, providing a similar experience to google docs/etc. 

This requires installing a python package of the same name - `pip install "plotlyshare>=1.10.0"` [Find it on PyPI!](https://pypi.org/project/plotlyshare/).

The idea is to preserve the interactivity and responsiveness of `plotly` plots with the ease of **link-based sharing** and without all the hassle of sending an html file, or worse, a static image/document.

To use this, first run `python -m plotlyshare setup`
and then whenever making a plot,

```py
...
import plotly.express as px
import plotly.graph_objects as go
import plotlyshare
...
fig = px.line(...)
fig = go.Figure(...)
fig.show(renderer='plotlyshare')
```

and that's it, the package will upload your plot to your instance of plotlyshare running in deta space and assign it a randomly generated name (which can be edited from the app's page) 
It will print the name that was generated and the direct link to the plot, ready to share with anyone.

## Web-App Routes
- `/` - This route serves as your home page, where all your plots are visible  
![screenshot-main-combined](/plotlyshare-main-combined.png) 
- `/plot/<plot_id>` - This **public** unique page is made for each plot and displays the plot with the corresponding id. It also displays how many users are active at a given moment (accurate to 10s on desktop and 10min on mobile).
![screenshot-plot](/plotlyshare-plot_16x10-2.png)
