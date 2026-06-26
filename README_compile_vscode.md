# Compile the thesis LaTeX project in VS Code

This folder is a standalone LaTeX version of the thesis. The entry point is `main.tex`.

## Requirements

1. Install a TeX distribution. On macOS, MacTeX is the easiest option: https://tug.org/mactex/
2. Install Visual Studio Code.
3. Install the VS Code extension **LaTeX Workshop**.
4. Use XeLaTeX because the thesis contains Vietnamese Unicode names and text.

## Compile from VS Code

1. Open VS Code.
2. Choose **File -> Open Folder...** and open `/Users/Yuki/TKNT/Thesis_LaTeX`.
3. Open `main.tex`.
4. Press `Cmd + Option + B`, or run **LaTeX Workshop: Build LaTeX project** from the Command Palette.
5. The PDF will be generated at `build/main.pdf`.

The included `.vscode/settings.json` already sets the default recipe to `latexmk (xelatex)`.

## Compile from Terminal

```bash
cd /Users/Yuki/TKNT/Thesis_LaTeX
latexmk -xelatex -interaction=nonstopmode -halt-on-error -outdir=build main.tex
```

`latexmk` will automatically run `biber` when the bibliography needs updating.

To clean auxiliary files:

```bash
latexmk -c -outdir=build main.tex
```

## Project structure

- `main.tex`: entry point.
- `metadata.tex`: thesis title, student name, supervisor, school, and date.
- `preamble.tex`: packages and formatting.
- `frontmatter/`: cover, acknowledgments, abstract, abbreviations.
- `chapters/`: one `.tex` file per chapter.
- `figures/`: figures extracted from the DOCX chapters.
- `references.bib`: unified bibliography for all chapters.

## Notes

- Overview and per-chapter conclusion sections were intentionally removed from the converted chapter files.
- Chapter-level reference lists were removed and merged into `references.bib`.
- If VS Code reports that `latexmk`, `xelatex`, or `biber` cannot be found, install MacTeX or add `/Library/TeX/texbin` to your shell PATH.
