# IWBIS Program Book

LaTeX source for the ICACSIS 2026 program book.

## Requirements

Install a LaTeX distribution that includes:

- `pdflatex`
- `latexmk`
- Packages used by the document, including `tikz`, `geometry`, `graphicx`, and `fancyhdr`

On macOS, install [MacTeX](https://www.tug.org/mactex/). TeX Live is also suitable on Linux and Windows.

## Build

Clone the repository and enter its directory:

```bash
git clone https://github.com/<your-username>/<your-repository>.git
cd <your-repository>
```

Build the PDF with `latexmk`:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
```

The generated document will be saved as `_build/main.pdf`. Auxiliary files are also kept in `_build/`.

## Overleaf

Upload or import the repository into Overleaf, set `main.tex` as the **Main document**, and compile normally. Keep `assets/` and `images/` in the same locations.

Overleaf manages its compilation workspace internally and does not guarantee that generated files will be exposed in the project as `_build/`. The `_build/` configuration is intended for local `latexmk` and VS Code builds. The source remains compatible with Overleaf because all document assets are referenced using relative paths.

Do not commit generated files from `_build/`; they are ignored by Git. Download the compiled PDF from Overleaf when needed, or build locally to obtain `_build/main.pdf`.

## Alternative Build Command

If `latexmk` is unavailable, run `pdflatex` directly. Run it twice so references and layout are fully resolved:

```bash
mkdir -p _build
pdflatex -output-directory=_build -interaction=nonstopmode -halt-on-error main.tex
pdflatex -output-directory=_build -interaction=nonstopmode -halt-on-error main.tex
```

## Clean Build Files

Remove auxiliary files while keeping the generated PDF:

```bash
latexmk -c
```

To remove all generated files, including the PDF:

```bash
latexmk -C
```

## Project Structure

```text
.
├── main.tex                 # Main LaTeX source
├── .latexmkrc               # Local latexmk output configuration
├── .vscode/settings.json    # Local VS Code LaTeX Workshop configuration
├── _build/                  # Local generated PDF and auxiliary files
├── assets/                  # Background and other document assets
└── images/                  # Logos, cover image, and sponsor images
```

Keep the `assets/` and `images/` directories in the same relative locations because they are referenced by `main.tex`.
