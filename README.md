# LaTeX Template for Hokudai Dissertation

## Introduction
This is a LaTeX template based on [Dissertate Project](https://github.com/suchow/Dissertate). See the sample of Hokudai alumni [HERE](https://eprints.lib.hokudai.ac.jp/dspace/bitstream/2115/70225/1/Zhai_HongJie.pdf). The template is designed under AGPL license.

## Getting started
1. Install LaTeX. For Mac OS X, we recommend MacTex (http://tug.org/mactex/); for Windows, MiKTeX (http://miktex.org/); and for Ubuntu, Tex Live (`sudo apt-get install texlive-full`)
2. Install the default fonts: EB Garamond, Lato, and Source Code Pro. The files are provided in `fonts/EB Garamond`, `fonts/Lato`, `fonts/Source Code Pro`, and `fonts/Palatino Linotype Bold.ttf`.
3. Personalize the document by filling out your name and all the other info in `frontmatter/personalize.md`.
4. Build your dissertation with `build`, located in the `scripts` directory (e.g., you can `cd` into the main directory and then run `./scripts/build`). We also provide `.vscode/settings.json` for Visual Studio Code users. You can use the `LaTeX Workshop` extension to build the document.
5. I also recommend using https://github.com/xu-shi-jie/bib-journal-abbreviator to abbreviate the journal names in the bibliography. You can clone the repository and uncomment the line in `scripts/build` to integrate the abbreviator into the build process.
    ```bash
    python ../bib-journal-abbreviator/main.py references-raw.bib
    mv references-raw-abbr.bib references.bib
    ```

## FAQ
- How do I change the fonts and colors?
  The fonts are set in the `dissertate.cls` file. You can change the fonts and colors there. The configuration lines look like this:
    ```latex
    \definecolor{SchoolColor}{rgb}{0.2157, 0.3882, 0.1529} % Crimson
    \definecolor{chaptergrey}{rgb}{0.5, 0.5, 0.5} % for chapter numbers
    ......
    \setromanfont[Numbers=OldStyle, Ligatures={Common, TeX}, Scale=1.0]{EB Garamond}
    ```
- How do I change the title papge?
    The title page is set in the `dissertate.cls` file. You can change the title page there. The configuration lines look like below. You can customize many things like the logo, text, and margins.
    ```latex
    \renewcommand{\maketitle}{
        \thispagestyle{empty}
        \begin{center}
            \includegraphics[width=\textwidth]{figures/logo.pdf}
        \end{center}
        \vspace*{\fill}
        \vspace{100pt}
        \begin{center}
            \setstretch{2.0}
            \textcolor{SchoolColor}{\Huge\thetitle} \normalsize \\
            \setstretch{1.0}
            \vspace{80pt}
            \textsc{A Doctoral Thesis \\ by \\ {\bf \theauthor}\\
            \vspace{80pt}
            Submitted to \\ \@department \\ \@university \\ \@universitycity, \@universitystate \\
            \@degreemonth\ \@degreeyear}
        \end{center} \vspace*{\fill}
    }
    ```
- How do I change the order of the front matter?
  The order of the front matter is set in the `dissertate.cls` file. You can change the order of the front matter there. The configuration lines look like this:
    ```latex
    \renewcommand{\frontmatter}{
        \input{frontmatter/personalize}
        \maketitle
        \copyrightpage
        \acknowledgments
        % \dedicationpage
        \tableofcontents
        \listoffigures % optional
        % \listoftables % optional
        \input{frontmatter/glossary}\printglossaries % optional
        \abstractpage
    }
    ```
- How do I make the text justified instead of ragged right?
  Remove or comment out the line `\RaggedRight` from the .cls file.
- How can I change the title break?
  Use \mbox{} to contain the words that you don't want to break. Please also change the vertical spaces in `Dissertate.cls` file to ensure title in one page.