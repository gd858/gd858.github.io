# quickest way to get latex compiler running on linux OS specifically fedora?

```
sudo dnf install texlive
```

this will install the basic TeX Live distribution. 

if I need additional packages later I can install them using 'tlmgr' which is the TeX Live package manager. 


inside 'test.tex' 

```latex
\documentclass{article}
\begin{document}
Hello, world!
\end{document}
```

compile with: 

```
pdflatex test.tex
```
That’s it! You should now have a working LaTeX setup on Fedora.
it worked! lets go.
