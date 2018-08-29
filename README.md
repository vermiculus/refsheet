# refsheet

A Reference sheet class for LaTeX2e.

According to [Wikipedia](https://en.wikipedia.org/wiki/Cheat_sheet), 
a cheat sheet is a concise set of notes used for quick reference.
Some might even call it a [reference sheet](https://en.wikipedia.org/wiki/Reference_card), 
hence the name.
In lieu of a proper documentation, we provide herewith a 
[reference sheet](documentation.pdf) for the documentclass `refsheet`.

This small class is aimed to make the typesetting of 
reference sheets a bit less tedious, so you can focus on using them.
The class is inspired from the question and answer 
[Document Class for Reference Cards](https://tex.stackexchange.com/q/99765).

Since `refsheet` is based on `article` most options can be passed on.

## Additional Options

  * `rscols=<num>`    How many columns, default is 3.
  * `margin=<length>` Passed to `geometry`, default 1 cm.

## Disabled Options

  * `portrait`   only supports `landscape`; ignored, warning.
  * `titlepagei` saving space, so no title page; ignored, warning.
  * `twocolumn`  class uses `multicol`; break, error.

## Features

  * Dense settings to save maximum space.
  * No enumeration of \texttt{(sub)section}s.
  * Customised itemise environments.

## Environments

### Description based environments

All of the environments below have a mandatory argument, 
which determines the width of the description label. 
Therefore it should contain the longest lable which is in use.

  * `rslist`    Description based list, normal text
  * `rslisttt`  dito, label in  `truetype`
  * `rslistbf`  dito, label in  **bold**
  * `rslistit`  dito, label in  _italics_

For example:

```
\begin{rslisttt}{rslisttt}
\item[rslist]    Description based [...]
\item[rslisttt]  dito, label in \texttt{truetype}
\item[rslistbf]  dito, label in \textbf{bold}
\item[rslistit]  dito, label in \textit{italics}
\end{rslisttt}
```

### Inline description list

With the environment  `rsinline` the list will be
set as a single paragraph.
It takes one optional argument for the font of the label:
  `bfseries` **bold**;
  `itshape`  _italics_;
  `ttfamily`  `truetype`,
which is the default if omitted.

A similar list like the above can be created with the following code.

```
One optional argument:
\begin{rsinline}{\ttfamily}
\item[bfseries] \textbf{bold};
\item[itshape]  \textit{italics};
\item[ttfamily] \texttt{truetype},
\end{rsinline}
which is the default.
```

### Column assorted list

The environment  `rscolslist` provides acess to a list, 
which is set in multiple columns.
The number of these can be given as an optional argumnet,
the default is to use two.

The following example produces such a list:

```
\begin{rscolslist}[3]
\item[\( \times \)]   \lstinline|\times| 
\item[\( \infty \)]   \lstinline|\infty| 
\item[\( \supset \)]  \lstinline|\supset|
\item[\( \alpha \)]   \lstinline|\alpha| 
\item[\( \epsilon \)] \lstinline|\epsilon|
\item[\( \theta \)]   \lstinline|\theta| 
\item[\( \lambda \)]  \lstinline|\lambda|
\item[\( \pi \)]      \lstinline|\pi| 
\item[\( \Psi \)]     \lstinline|\Psi|
\end{rscolslist}
```

### Legacy environment

  * `ttdesc`    Description based list, label has variable width 
  in the  `truetype` style

## Table based environments

The table based environments uses the  `tabularx` package.
They predefine the table to fill the whole line.

The first one is  `rstable`, which 
has a mandatory argument for the number of columns. 
An optional argument for the alignment of all but the last column can be specified.
The last column is special, because it is used to balance the table and 
therefore the columntype  `X`.

| Mand. | Opt. | Description                                                 |
| ----- | ---- | ----------------------------------------------------------- |
|  `2`  |  `c` | First column centred, last column is a parbox.              |
|  `3`  |  `l` | First two columns left aligned, last column is a parbox.    |
|  `4`  |  `r` | First three columns right aligned, last column is a parbox. |
|  `4`  | -    | Four columns of type  `X`                                   |

For example:

```
\begin{rstable}[c]{3}
\hline
Mand.      & Opt.       & Description \\\hline
\texttt{2} & \texttt{c} & First column [...].\\
\texttt{3} & \texttt{l} & First two    [...],%
                          last column  [...].\\
\texttt{4} & \texttt{r} & First three  [...],%
                          last column  [...].\\
\texttt{4} & -          & Four [...] \texttt{X}\\
\hline                          
\end{rstable}
```

The second one is meant to be used for maths notation,
called  `rsmathtable`, which has no argument.
The first column is set in displaystyle maths mode and 
will be fitted to the widest entry.
The second one is meant for the description and 
like before of columntype  `X`.

For example:

```
\begin{rsmathtable}
  pV = nRT   &  ideal gas law \\
  0 = e^{i\pi} + 1 & Euler's identity \\
  \log(MN) = \log(M) + \log(N) & Log. addition rule\\
\end{rsmathtable}
```

## Acknowledgments

 * Mike Renfro, original code, 
  [Mike Renfro](https://tex.stackexchange.com/users/3345)
  [mikerenfro](https://github.com/mikerenfro)
 * Sean Allred, class implementation, 
  [Sean Allred](https://tex.stackexchange.com/users/17423)
  [vermiculus](https://github.com/vermiculus)
 * Eric Berquist], further development, 
  [berquist](https://github.com/berquist)
 * Martin C Schwarzer, further development, 
  [Martin-マーチン](https://chemistry.stackexchange.com/users/4945)
  [polyluxus](https://github.com/polyluxus)

The class and the document are licensed [CC-BY-SA 4.0](LICENSE.markdown).

