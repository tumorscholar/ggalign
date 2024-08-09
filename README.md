
<!-- README.md is generated from README.Rmd. Please edit that file -->

# ggalign

This package extends ggplot2 and offers several benefits for organizing
and arranging plots. It is specifically designed to align the axes of
multiple ggplot objects consistently. This functionality is particularly
useful for plots where data order needs to be manipulated. One common
application of this package is in effectively organizing combinations of
plots, such as a dendrogram and a heatmap.

## Installation

You can install the development version of `ggalign` from
[GitHub](https://github.com/) with:

``` r
# install.packages("remotes")
remotes::install_github("Yunuuuu/ggalign")
```

This package now depends on some un-merged features of patchwork. Please
see <https://github.com/thomasp85/patchwork/pull/373>. If you want to
try it, you should install patchwork with
`pak::pkg_install(Yunuuuu/patchwork@align_axis_title)`.

The documentation for `ggalign` is currently in progress.

## Features

`ggalign` pacakge provides two layout to arrange ggplot objects:

- `layout_heatmap()`/`ggheamtap()`: Arrange ggplot into a Heatmap
  layout. See `vignette("layout-heatmap")` for details.

- `layout_stack()`/`ggstack()`: Arrange ggplot vertically or
  horizontally. See `vignette("layout-stack")` for details.

To further customize these layouts, the `ggalign` package offers several
`Align` objects:

- `align_group()`: Group layout axis into panel with a group variable.
- `align_kmeans()`: Group layout axis into panel by kmeans
- `align_reorder()`: Reorders layout observations based on weights or
  summary statistics.
- `align_dendro()`: Reorder or Group layout based on hierarchical
  clustering

For more detailed instructions on customizing layouts, see the vignette:
`vignette("align-layout")`.

Additionally, the following `Align` objects can be used to add plots
directly into the layout:

- `align_gg()`/`ggalign()`: Create ggplot object with a customized data.
- `align_panel()`/`ggpanel()`: Create ggplot object with the layout
  panel data.

For more information on adding plots, refer to the vignette:
`vignette("align-plot")`.

## Examples

## Compare with ComplexHeamtap
