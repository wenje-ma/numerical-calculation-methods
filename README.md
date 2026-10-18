# Numerical Calculation Methods

> Numerical analysis lecture notes and 8 weeks of fully worked homework, bilingual (Chinese/English) — the most compact repository in the notes series.

## Repository structure

```
numerical-calculation-methods/
├── cn/
│   ├── notes.md              # Chinese lecture notes (single file, 637 lines)
│   └── homework/
│       └── week1.md … week8.md
├── en/
│   ├── notes.md              # Complete English translation (637 lines, aligned)
│   └── homework/
│       └── week1.md … week8.md
└── textbooks/
    ├── numerical-calculation-methods_part1.pdf   # Textbook part 1 (240 pp.)
    ├── numerical-calculation-methods_part2.pdf   # Textbook part 2 (107 pp.)
    └── *_ocr.pdf                                 # OCR (searchable) copies
```

## The notes

`notes.md` is a single file organized as **8 algorithm-dense chapters**:

1. Introduction and significant digits — errors, significant figures, error propagation
2. Direct methods for systems of linear equations — Gaussian elimination, Doolittle/LU decomposition, Cholesky decomposition
3. Iterative methods for linear systems
4. Eigenvalue computation
5. Interpolation
6. Function approximation
7. Numerical differentiation and numerical integration
8. Methods for nonlinear equations

Statements are bold-tagged entries (**Definition**, **Theorem**, **Algorithm**, **Formula**) with mathematics in `$…$` / `$$…$$`.

## The homework

Each `homework/weekN.md` follows the series-wide format:

1. **Toolbox** — a blockquote restating the definitions and theorems needed;
2. **Problems** — the assigned exercises (derivations and numerical estimates);
3. **Solutions** — complete worked solutions ending with `$\blacksquare$`.

There are **8 weeks** of problem sets in each language — a one-semester half-course.

## Bilingual layout

- `cn/` — authoritative Chinese version.
- `en/` — complete parallel English translation; files share identical names and line counts.

## The `textbooks/` folder

The four PDFs are the scanned textbook (split into two parts due to size) and their OCR copies — **external reference material**, not compiled from the notes. There is no build system; everything is plain Markdown rendered with GitHub's LaTeX support.

## Related repositories

Other course-notes repositories in the same series: [mathematical-analysis](https://github.com/wenje-ma/mathematical-analysis), [ordinary-differential-equations](https://github.com/wenje-ma/ordinary-differential-equations), [mathematical-statistics](https://github.com/wenje-ma/mathematical-statistics), and the full list on the [profile page](https://github.com/wenje-ma).
