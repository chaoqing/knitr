# Chunk Options #

knitr has an extremely well thought out set of chunk options that allows the user to modify the display of various elements like source code and results. The numerous options available might seem daunting to a novice. The objective of this wiki page is to organize and present the chunk options logically. I have borrowed heavily from [Yihui's page] (http://yihui.github.com/knitr/options#package_options), and readers are directed there for more details.


## Text Settings ##

Options to control basic **display** (boolean)

1. `message`, `warning`, `error`, and `prompt` are boolean options that control whether or not messages, warnings, errors and the prompt are to be displayed. All options with the exception of `prompt` are TRUE by default.

2. `echo`, `tidy`, and `highlight` are boolean options that control whether or not source code is to be displayed, tidied (by `formatR`), and highlighted (by `highlight`)

Options to control **display** of results

3. `results` control how the output is displayed. It takes three possible values. `markup` writes the results using an output hook, with a default based on document type. For example, in a latex document, the default output hook puts results in a special LaTeX environment, similar to `results = tex` in Sweave. `asis` writes the raw output from R in the output document(equivalent to verbatim in Sweave). The output can be hidden by setting results=hide. 

## Plot Settings ##

Options to control plot **setup**

1. `fig` is a boolean that specifies if a plot should be generated. `fig.dev` specifies the graphics device for generating the plot. A total of 20 built-in devices are supported, which includes the common graphics drivers like `pdf`, `eps`, `png`, `bmp`, `tikz` and `svg`. The user can specify `dpi` (default 72) to control the dimensions of plots created by bitmap devices. `tikz` plots can be externalized (pre-compiled to `pdf`) by setting external to TRUE, and sanitized by setting sanitize to TRUE. 

2. `prefix.string` specifies the path prefix to be appended before chunk labels to make filenames for saving figures. For example, setting `fig.prefix` to _figure/prefix_ will save all figures to the **figure** directory (creating it if it does not exist), under the name _prefix-chunk_. `fig.ext` specifies the file extension of the figure output. The default is derived from the graphical device (see `knitr:::dev2ext` for details)

3. `align` specifies the alignment of figures (`left`, `right` and `center`) in the output document.

Options to control plot **display** (boolean)

1. `fig.hold`: All plots are displayed inline, just as if the code was run in an R terminal. Setting `fig.hold` to TRUE holds all plots generated, and displays them at the end of the code chunk.

2. `fig.low`: Low-level plotting functions like `line`, `text` etc. only add to the current plot and do not produce new plots. Setting `fig.low` to `TRUE` allows these plots to be treated as new plots.

3. `fig.last`: All plots generated by high-level plotting functions are displayed. Setting `fig.last` to `TRUE` allows retaining only the last plot generated, and discarding all the others.

4. `animate`: Creates an animated display using the multiple plots generated in a chunk. The pause between frames (in seconds) is controlled using `interval`. Further options can be configured using `ani.opts`. 

Options to control plot **dimensions**.

1. `width`, `height` specify the size of the plot used by the graphics device in inches.

2. `out.width`, `out.height` specify the size of the plot saved to file. It can be different from width and height, and can also be specified relative to the document.

3. `resize.width`, `resize. height`