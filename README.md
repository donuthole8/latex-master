# latex-master

## 概要
修士論文のLaTex文書管理


## Mac環境構築
https://qiita.com/muro5866/items/c8a3217132abff93e848


## PDF生成
LaTex Workshop必要
- https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop

```
% eval "$(/usr/libexec/path_helper)"
% latexmk thesis.tex
```

## 備忘録
### 図表の挿入エラー
```
! LaTeX Error: Cannot determine size of image in XXX (no BoundingBox)
```
https://paper.hatenadiary.jp/entry/2017/01/16/221112
```
! LaTeX Error: Option clash for package graphicx.
```
→
```
\usepackage[dvips]{graphicx}  % 削除
\usepackage[dvipdfmx]{graphicx}  % こちらに置き換える
```


### 参考文献bibエラー
```
! Undefined control sequence.
```
https://sonickun.hatenablog.com/entry/2015/01/07/233530
→
```
\usepackage{url}  % 追記
```


### プリアンブル
本文以外の各種設定やパッケージをpreamble.texに記載して
```
\input{preamble}
```
で記載した設定等を読み込みできる （編集済み） 


### 参照マクロ
preamble.texに
```
% 参照マクロ
\newcommand{\fref}[1]{\textbf{図\ref{#1}}}
\newcommand{\Fref}[1]{\textbf{式\ref{#1}}}
\newcommand{\tref}[1]{\textbf{表\ref{#1}}}
```
記載しておくと\fref{label_name}とかで図表参照できて便利


### LaTex Workshop
VSCodeでLatex Workshop入れてないとVSCode上でpdf見れないぽい


### Github
https://github.com/donuthole8/latex-master 


### Issues
https://github.com/donuthole8/latex-master/issues


## その他
容量が10MB以上のファイルはGithubにアップロードできないため.gitignoreにPDFと画像を追記
