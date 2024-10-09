
<!-- README.md is generated from README.Rmd. Please edit that file -->

# ggalign <a href="https://yunuuuu.github.io/ggalign/"><img src="man/figures/logo.png" align="right" height="139" alt="ggalign website" /></a>

<!-- badges: start -->

[![R-CMD-check](https://github.com/Yunuuuu/ggalign/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/Yunuuuu/ggalign/actions/workflows/R-CMD-check.yaml)
[![Codecov test
coverage](https://codecov.io/gh/Yunuuuu/ggalign/branch/main/graph/badge.svg)](https://app.codecov.io/gh/Yunuuuu/ggalign?branch=main)
[![CRAN
status](https://www.r-pkg.org/badges/version/ggalign)](https://CRAN.R-project.org/package=ggalign)
<!-- badges: end --> This package extends ggplot2 by providing advanced
tools for aligning and organizing multiple plots, particularly those
that automatically reorder observations, such as dendrogram. It offers
fine control over layout adjustment and plot annotations, enabling you
to create complex, publication-quality visualizations while still using
the familiar grammar of ggplot2.

## Why use `ggalign`?

`ggalign` focuses on aligning observations across multiple plots. It
leverages the `"number of observations"` in the
[vctrs](https://vctrs.r-lib.org/reference/vec_size.html) package or
`NROW()` function to maintain consistency in plot organization.

If you’ve ever struggled with aligning plots with self-contained
ordering (like dendrogram), or applying consistent grouping or ordering
across multiple plots (e.g., with k-means clustering), `ggalign` is
designed to make this easier. The package integrates seamlessly with
ggplot2, providing the flexibility to use its geoms, scales, and other
components for complex visualizations.

## Installation

You can install `ggalign` from `CRAN` using:

``` r
install.packages("ggalign")
```

Alternatively, install the development version from
[GitHub](https://github.com/Yunuuuu/ggalign) with:

``` r
# install.packages("remotes")
remotes::install_github("Yunuuuu/ggalign")
```

## Getting Started

The usage of `ggalign` is simple if you’re familiar with `ggplot2`
syntax, `ggalign` works with a simple workflow:

- Initialize the layout using `ggheatmap()` or `ggstack()`.
- Customize the layout with:
  - `align_group()`: Group layout axis into panel with a group variable.
  - `align_kmeans()`: Group layout axis into panel by kmeans
  - `align_reorder()`: Reorder layout observations based on statistical
    weights or allows for manual reordering based on user-defined
    criteria.
  - `align_dendro()`: Reorder or Group layout based on hierarchical
    clustering
- Adding plots with `ggalign()` or `ggpanel()`, then add ggplot2
  elements like geoms, stats, scales.

## Basic example

Below, we’ll walk through a basic example of using `ggalign` to create a
heatmap with a `dendrogram`.

``` r
library(ggalign)
set.seed(123)
small_mat <- matrix(rnorm(81), nrow = 9)
rownames(small_mat) <- paste0("row", seq_len(nrow(small_mat)))
colnames(small_mat) <- paste0("column", seq_len(ncol(small_mat)))

# initialize the heatmap layout, we can regard it as a normal ggplot object
ggheatmap(small_mat) + 
    # we can directly modify geoms, scales and other ggplot2 components
    scale_fill_viridis_c() +
    # add annotation in the top
    hmanno("top") +
    # in the top annotation, we add a dendrogram, and split observations into 3 groups
    align_dendro(aes(color = branch), k = 3) +
    # in the dendrogram we add a point geom
    geom_point(aes(color = branch, y = y)) +
    # change color mapping for the dendrogram
    scale_color_brewer(palette = "Dark2")
```

![](https://yunuuuu.github.io/ggalign/articles/complete-examples_files/figure-html/unnamed-chunk-3-1.png)

## Compare with other ggplot2 heatmap extension

The main advantage of `ggalign` over other extensions like
[ggheatmap](https://github.com/XiaoLuo-boy/ggheatmap) is its full
compatibility with the ggplot2 grammar. You can seamlessly use any
ggplot2 geoms, stats, and scales to build complex layouts, including
multiple heatmaps arranged vertically or horizontally.

## Compare with ComplexHeatmap

### Pros

- Full integration with the `ggplot2` ecosystem.
- Heatmap annotation axes and legends are automatically generated.
- Dendrogram can be easily customized and colored.
- Flexible control over plot size and spacing.
- Can easily align with other `ggplot2` plots by panel area.

### Cons

Fewer Built-In Annotations: May require additional coding for specific
annotations or customization compared to the extensive built-in
annotation function in ComplexHeatmap.

## More Complex Examples

Here are some more advanced visualizations using `ggalign`:
![](https://yunuuuu.github.io/ggalign/articles/more-examples_files/figure-html/unnamed-chunk-3-1.png)
![](https://yunuuuu.github.io/ggalign/articles/more-examples_files/figure-html/unnamed-chunk-2-1.png)

## Further Documentation

- [Heatmap
  Layout](https://yunuuuu.github.io/ggalign/articles/heatmap-layout.html)
- [Layout
  Customization](https://yunuuuu.github.io/ggalign/articles/layout-customize.html)
- [Layout
  Plot](https://yunuuuu.github.io/ggalign/articles/layout-plot.html)
- [Stack
  Layout](https://yunuuuu.github.io/ggalign/articles/stack-layout.html)
- [Scales and
  Facets](https://yunuuuu.github.io/ggalign/articles/scales-and-facets.html)
