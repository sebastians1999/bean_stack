# Visualise

Lean visuals. Show one idea per visual. Use colour only when it carries meaning, such as one colour per vector or a highlight on the part that changed.

## Pick the lightest form that shows it

1. **ASCII diagram.** Default. Fastest. Use it for vectors, bases, matrix shapes, block structure, flows, and small trees.
2. **Plot.** Use it when the idea is quantitative, such as a curve, a transformation of a grid, eigenvectors under a map, or convergence. Write a short matplotlib script, run it, and show the image.
3. **Interactive HTML.** Use it only for a complex topic where playing with a parameter builds intuition, such as a slider on a matrix entry, an angle, or a step size. One self-contained file with no build step.

Climb only when the lighter form cannot show the idea.

## ASCII

Label every axis and vector. Keep it under about 15 lines.

```
  y
  ^     Av
  |    /
  |   /   v
  |  /  /
  | / /
  +---------> x
```

## Plots

- Equal aspect for geometry (`ax.set_aspect("equal")`).
- Few elements. Label vectors on the plot, not only in a legend.
- Grey for context, one or two colours for what matters.
- No titles that restate the axes.

## Interactive HTML

- One HTML file, plain JS or a single CDN library.
- One or two sliders, each named for the quantity it changes.
- Show the current value next to each slider.

## After the visual

Ask what they notice. Let them read it before you explain it.
