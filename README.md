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

### 図表メモ

#### 画像3枚（横並び）

```
\begin{figure}[tbp]
  \begin{minipage}[c]{0.329\hsize}
    \centering
    \includegraphics[width=4.5cm]{image/exmaple/input1.jpg}
    \subcaption{入力画像例1}
    \label{入力画像例1}
  \end{minipage}
  \begin{minipage}[c]{0.329\hsize}
    \centering
    \includegraphics[width=4.5cm]{image/exmaple/input2.jpg}
    \subcaption{入力画像例2}
    \label{入力画像例2}
  \end{minipage}
  \begin{minipage}[c]{0.329\hsize}
    \centering
    \includegraphics[width=4.5cm]{image/exmaple/input3.jpg}
    \subcaption{入力画像例3}
    \label{入力画像例3}
  \end{minipage}
  \caption{災害後空撮画像の例}
  \label{空撮画像例}
\end{figure}
```


#### 設定値＋画像

```
\begin{figure}[tbp]
  \begin{minipage}[c]{0.45\hsize}
    \centering
    \includegraphics[width=4.5cm]{image/setting/alignment.jpg}
    \subcaption{設定値}
  \end{minipage}
  \begin{minipage}[c]{0.45\hsize}
    \centering
    \includegraphics[width=9cm]{image/exmaple/alignment.jpg}
    \subcaption{処理結果}
  \end{minipage}
  \caption{写真のアラインメント}
  \label{写真のアラインメント結果}
\end{figure}
```


#### 概念図

```
\begin{figure}[tbp]
  \centering
  \includegraphics[width=12cm]{image/method/processing-flow.png}
  \caption{提案手法概要図}
  \label{提案手法概要図}
\end{figure}

\begin{figure}[tbp]
  \centering
  \includegraphics[width=6cm]{image/method/mesh.png}
  \caption{傾斜角度・傾斜方位におけるメッシュ図}
  \label{メッシュ図}
\end{figure}
```


#### 画像2枚（縦長でない場合，小サイズ画像は都度調整）

```
\begin{figure}[tbp]
  \begin{minipage}[c]{0.5\hsize}
    \centering
    \includegraphics[width=0.9\linewidth]{image/mean-shift.png}
    \subcaption{傾斜角度モデル}
  \end{minipage}
  \begin{minipage}[c]{0.5\hsize}
    \centering
    \includegraphics[width=0.9\linewidth]{image/mean-shift.png}
    \subcaption{傾斜方位モデル}
  \end{minipage}
  \caption{傾斜角度・傾斜方位モデル}
\end{figure}
```


#### 画像3枚（上段＋下段）

```
\begin{figure}[tbp]
  \begin{tabular}{cc}
    \begin{minipage}[c]{0.329\hsize}
      \centering
      \includegraphics[width=4.5cm]{image/setting/georeferencer.png}
      \subcaption{設定値}
    \end{minipage} &
    \begin{minipage}[c]{0.329\hsize}
      \centering
      \includegraphics[width=4.5cm]{image/exmaple/geo_dsm.png}
      \subcaption{災害後DSM}
    \end{minipage}
  \end{tabular} \\
  \centering
  \includegraphics[width=4.5cm]{image/exmaple/geo_ortho.png}
  \subcaption{オルソ画像}
  \caption{ジオリファレンサ3枚組テスト}
\end{figure}
```