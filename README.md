## Python libraries for regressions with fixed effect

OLS in statsmodels does not automatically use demeaning or absorb fixed effects when many dummy variables are included as regressors. This is problematic not only for the computational burden (inversion of large matrix) but also for the accuracy in case of near collinearity. It is highly recommended to demean the dataset by the set of dummy variables based on the Frisch-Waugh-Lovell theorem.

A non-comprehensive list of options:

1. statsmodels.api (**sm**)
2. statsmodels.formula.api (**smf**; accepts Patsy)
3. linearmodels.panel.**PanelOLS** (accepts Formulaic)
4. linearmodels.iv.**AbsorbingLS**
5. **pyfixest** (accepts Formulaic)
6. **reghdfe**

The main takeaways:
- Standard errors from **pyfixest** was the closest to that obtained from xtreg in Stata.
- Standard errors from **reghdfe** are sometimes ~10 times larger than the rest (not recommended).
- For complex combinations of FE, **smf** may not remove all the collinearities (not recommended).
- In terms of execution time, **AbsorbingLS, pyfixest, reghdfe** outperformed PanelOLS and sm/smf.
- The current results confirm my personal choice of pyfixest.
