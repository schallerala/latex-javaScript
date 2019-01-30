# Latex-JavaScript
Typeset JavaScript codes in Latex based on the [Boxy Yesterday](https://marketplace.visualstudio.com/items?itemName=trongthanh.theme-boxythemekit#user-content-boxy-yesterday) scheme.

Keywords from

    - JavaScript (ES 6)
    - Node.js
    - Express.js
    - Jasmine

Original color scheme:
![Sample](https://cloud.githubusercontent.com/assets/5876481/26476923/c2932232-4176-11e7-9017-329709928c3d.png)


# Installation
    kpsewhich -var-value=TEXMFHOME # outputs the path in which to place the .sty. For example: ~/Library/texmf on Mac
    cp jslistings.sty ~/Library/texmf/tex/latex/local
    texthash ~/Library/texmf # to update tex's database
    kpsewhich jslistings.sty # to make sure it knows it

# Issue
Unable to color closing parentheses when `breaklines` is set to `true` like:
```latex
\lstset{
    % ...
    breaklines=true,
    % ...
}
```

Then use the package `etoolbox` to add the `patchcmd` command and use it this way ([Stackoverflow answer](https://tex.stackexchange.com/a/172975/164820)):
```latex
\usepackage{etoolbox} % provides the \patchcmd macro
% ...
\makeatletter
\patchcmd{\lsthk@SelectCharTable}{`)}{``}{}{} % patch listings
%\patchcmd{\lsthk@SelectCharTable}{``}{`)}{}{} % undo patch if needed
\makeatother
```

# More

Didn't look more for it, but can generate an dtx from the sty:

    sty2dtx jslistings.sty