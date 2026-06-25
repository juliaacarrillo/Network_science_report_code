# Final report bundle — Julia

## Files included

- `report.tex` — the LaTeX report (revtex4-2, two-column). Compile with `pdflatex report.tex` (twice for cross-refs). It uses the four figures listed below.
- `fig_curves_g25.png` — raw observables vs λ for γ=2.5 (Fig. 1).
- `fig_exponents_combined.png` — combined scaling analysis (λ_p fit + β/ν) for γ=2.5 (Fig. 2).
- `fig_collapse_g25.png` — finite-size scaling data collapses (Fig. 3).
- `sis_lifespan_commented.cpp` — your `sis_lifespan_v2.cpp` with inline `//` comments explaining every block (CSR layout, Gillespie loop, O(1) swap-with-last trick, moment accumulators). Functionally identical to the original.

## Expected output

3 pages in revtex 2-column. The article 10pt 2-column test produced 4 pages including a wasted abstract-only first page; revtex puts the abstract inline with the title, saving that page.

## To add γ=3.5 figures with the same look

In your `analysis_v5.ipynb`, change the configuration cell to:

```python
GAMMA  = 3.5
PREFIX = 'g35'
```

re-run all cells; this will write to `results/`:

- `g35_v2_curves.png`           → rename to `fig_curves_g35.png`
- `g35_v2_step3_lambda_fit.png` → use for the λ_p fit panel
- `g35_v2_step5_beta_nu.png`    → use for the β/ν panel
- `g35_v2_step6_collapse.png`   → rename to `fig_collapse_g35.png`

Then in `report.tex` either (a) duplicate the three figure blocks with `_g35` suffix and add a second column to Table II with the γ=3.5 numbers; or (b) replace each PNG by a side-by-side composite of γ=2.5 and γ=3.5 (use the same `Pillow` recipe used in the bundle to build `fig_exponents_combined.png`).

## Page budget

If revtex still spills over 3 pages on your machine: drop Fig. 3 (the collapses) and shorten the Discussion paragraph — the exponents table and Fig. 2 already convey the essential FSS story.
