![PythonCall.jl logo](https://raw.githubusercontent.com/cjdoris/PythonCall.jl/master/logo-text.svg)
---
[![Project Status: Active – The project has reached a stable, usable state and is being actively developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)
[![Stable Documentation](https://img.shields.io/badge/docs-stable-blue.svg)](https://cjdoris.github.io/PythonCall.jl/stable)
[![Dev Documentation](https://img.shields.io/badge/docs-dev-blue.svg)](https://cjdoris.github.io/PythonCall.jl/dev)
[![Test Status](https://github.com/cjdoris/PythonCall.jl/workflows/Tests/badge.svg)](https://github.com/cjdoris/PythonCall.jl/actions?query=workflow%3ATests)
[![Codecov](https://codecov.io/gh/cjdoris/PythonCall.jl/branch/master/graph/badge.svg?token=A813UUIHGS)](https://codecov.io/gh/cjdoris/PythonCall.jl)

Bringing [**Python®**](https://www.python.org/) and [**Julia**](https://julialang.org/) together in seamless harmony:
- Call Python code from Julia and Julia code from Python via a symmetric interface.
- Simple syntax, so the Python code looks like Python and the Julia code looks like Julia.
- Intuitive and flexible conversions between Julia and Python: anything can be converted, you are in control.
- Fast non-copying conversion of numeric arrays in either direction: modify Python arrays (e.g. `bytes`, `array.array`, `numpy.ndarray`) from Julia or Julia arrays from Python.
- Helpful wrappers: interpret Python sequences, dictionaries, arrays, dataframes and IO streams as their Julia couterparts, and vice versa.
- Beautiful stack-traces.
- Works anywhere: tested on Windows, MacOS and Linux, 32- and 64-bit, Julia 1.0 upwards and Python 3.5 upwards.

⭐ If you like this, a GitHub star would be lovely thank you. ⭐

To get started, read the [documentation](https://cjdoris.github.io/PythonCall.jl/stable).

## Example 1: Calling Python from Julia

In this example, we use `PythonCall.jl` from a [`Pluto`](https://github.com/fonsp/Pluto.jl) notebook to inspect the Iris dataset:
- We load the Iris dataset as a Julia [`DataFrame`](https://dataframes.juliadata.org/stable/) using [`RDatasets.jl`](https://github.com/JuliaStats/RDatasets.jl).
- We use `pytable(df)` to convert it to a Python [`pandas.DataFrame`](https://pandas.pydata.org/).
- We use the Python package [`seaborn`](https://seaborn.pydata.org/) to produce a pair-plot, which is automatically displayed.

![Seaborn example screenshot](https://raw.githubusercontent.com/cjdoris/PythonCall.jl/master/examples/seaborn.png)

## Example 2: Calling Julia from Python

In this example we use the Python module `juliacall` from an IPython notebook to train a simple neural network:
- We generate some random training data using Python's `numpy`.
- We construct and train a neural network model using Julia's `Flux`.
- We plot some sample output from the model using Python's `matplotlib.pyplot`.

![Flux example screenshot](https://raw.githubusercontent.com/cjdoris/PythonCall.jl/master/examples/flux.png)

## What about PyCall?

The existing package [`PyCall`](https://github.com/JuliaPy/PyCall.jl) is another similar interface to Python. Here we note some key differences, but a more detailed comparison is in the documentation.
- PythonCall supports a wider range of conversions between Julia and Python, and the conversion mechanism is extensible.
- PythonCall by default never copies mutable objects when converting, but instead directly wraps the mutable object. This means that modifying the converted object modifies the original, and conversion is faster.
- PythonCall does not usually automatically convert results to Julia values, but leaves them as Python objects. This makes it easier to do Pythonic things with these objects (e.g. accessing methods) and is type-stable.
- PythonCall installs dependencies into a separate conda environment for each Julia project. This means each Julia project can have an isolated set of Python dependencies.
- PythonCall supports Julia 1.0+ and Python 3.5+ whereas PyCall supports Julia 0.7+ and Python 2.7+.
