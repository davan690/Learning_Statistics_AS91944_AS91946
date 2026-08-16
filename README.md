# Learning Statistics for AS91944 & AS91946

A Quarto + R textbook for **NCEA Level 1 Achievement Standards 91944 & 91946** —
*Interpret and apply mathematical and statistical information in context* (4
credits, external exam). Designed for Year 11 students in New Zealand.

## Contents

| Chapter | Topic |
| ------- | ----- |
| Welcome | Introduction and overview of the standard |
| 1 | Combined AS1.1 and AS1.3 approach |
| 2 | What is Statistics? (statistical questions, context, core terms) |
| 3 | The PPDAC enquiry cycle |
| 4 | Types of Data and Variables (categorical, numerical, ordinal, etc.) |
| 5 | Independent and Dependent Variables (explanatory vs response roles) |
| 6 | Measures of Spread Study Notes (range, quartiles, IQR) |
| 7 | Statistical Graphs and Displays (bar charts, histograms, box plots, scatter plots) |
| 8 | Bivariate Data in Ecology (koura example) |
| 9 | Measures of Centre and Spread (mean, median, IQR, standard deviation) |
| 10 | Practice Questions and Exam Tips (Achieved / Merit / Excellence) |
| 11 | Probability (classical, experimental, two-way tables, tree diagrams) |
| 12 | Interpreting Statistical Information (bias, correlation vs causation, critical reading) |

## Rendering the book

### Prerequisites

- [R](https://www.r-project.org/) (≥ 4.3)
- [Quarto](https://quarto.org/) (≥ 1.4)

### Install R packages

```r
source("setup.R")
```

### Render (HTML + PDF)

```powershell
.\render.ps1
```

Or, if `quarto` is already on your PATH:

```bash
quarto render
```

The output is written to the `_book/` directory. Open `_book/index.html` in
any browser to read the HTML version.

`render.ps1` locates `quarto.exe` itself (falling back to common install
paths) so rendering still works in a PowerShell session where PATH hasn't
picked up a recent Quarto install — see [Troubleshooting](#troubleshooting).

### Render HTML only

```powershell
.\render.ps1 -To html
```

### Render PDF only

```powershell
.\render.ps1 -To pdf
```

> PDF rendering requires a LaTeX installation. We recommend
> [TinyTeX](https://yihui.org/tinytex/): `quarto install tinytex`

## Troubleshooting

**`quarto : The term 'quarto' is not recognized...`**

This happens when a PowerShell/terminal session was started before Quarto was
installed or added to PATH — Windows does not push environment variable
changes to already-running shells. Fixes, in order of preference:

1. Open a new terminal (PATH is re-read on session start).
2. Use `.\render.ps1`, which resolves `quarto.exe` directly instead of relying
   on PATH.
3. Call the executable by its full path, e.g.
   `& "$env:LOCALAPPDATA\Programs\Quarto\bin\quarto.exe" render`.

**`render.ps1 cannot be loaded because running scripts is disabled...`**

PowerShell's default execution policy blocks local `.ps1` scripts. Either run
it once per session with:

```powershell
powershell -ExecutionPolicy Bypass -File .\render.ps1
```

or allow local scripts permanently (per-user, no admin required):

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

## Repository structure

```text
.
├── _quarto.yml          # Quarto book configuration
├── index.qmd            # Welcome page
├── chapters/
│   ├── 01-intro.qmd                # Combined AS1.1 and AS1.3 approach
│   ├── 02-what-is-statistics.qmd
│   ├── 03-ppdac.qmd
│   ├── 04-data-types.qmd
│   ├── 04-1-dependent-independent-variables.qmd
│   ├── 04-2-measures-of-spread.qmd
│   ├── 05-graphs.qmd
│   ├── 06-1-koura-example.qmd
│   ├── 07-measures.qmd
│   ├── 08-practice.qmd
│   ├── 09-probability.qmd
│   └── 10-inference.qmd
├── references.qmd       # References page
├── references.bib       # BibTeX bibliography
├── setup.R              # R package installer
└── README.md
```

## Contributing

Contributions are welcome! Please open an issue or pull request. When adding
or editing content, ensure:

- New Zealand context is maintained throughout
- R code chunks are reproducible (use `set.seed()` for random examples)
- All cross-references use Quarto's `@sec-` syntax
- Grade-level callouts (Achieved / Merit / Excellence) are clearly labelled

## Licence

MIT © Anthony R Davidson — see [LICENSE](LICENSE).
