# 2018年度CPU実験7班のコンパイラコード
clone元は[こちら](https://github.com/esumii/min-caml)

## 概要

- makeでMakefileすべての操作を実行します
- make bcでテストスクリプトの実行を無効化できます
- min\_caml\_print\_intのアセンブリコードはコンパイルの都度、作成されるアセンブリコードの先頭に埋め込まれるようにしました

## コンパイル方法

- file.mlをコンパイルしたいときは、./min-caml \[-options\] \[file\] でコンパイル可能です
- fileと同じディレクトリにfile.sが作成されます
- optionsは、main.mlの下の方を読むとだいたい解ると思いますが、全部の処理の過程を見たいときは、とりあえず-dumpallをつかえばいいです。

## ふぁー、文字化けがやばいな...

- 途中からutf-8に変えたので、各所で文字化けがやばいです

## メモ

- let f x y = f y x in let g x = f 0 1 in () のようなプログラムは、インライン展開でとまらない。
- f x (fun r -> t) は、let r = f x in tとして読めば理解しやすい
- コンパイラ向け課題のフォーマットはcompiler-学籍番号.zip

## esumiiさんのmin-camlレポジトリにあるREADME

An educational compiler for a minimal subset of OCaml, written in
~2000 lines of OCaml.  For details, see:

http://esumii.github.io/min-caml/ (Japanese Web page)
http://esumii.github.io/min-caml/jpaper.pdf (Japanese academic paper)
http://esumii.github.io/min-caml/index-e.html (English Web page)
http://esumii.github.io/min-caml/paper.pdf (English academic paper)

1. Install OCaml (http://caml.inria.fr/) if you haven't

2. Download (and expand) MinCaml, e.g.
   git clone https://github.com/esumii/min-caml.git

3. cd min-caml/

4. Execute ./to\_x86 for x86
   (or ./to\_sparc for SPARC, ./to\_ppc for PowerPC)

5. make

6. If you like, try the ray tracer

     cd min-rt/ ; make

   though it takes time because of OCaml bytecode (for testing by
   comparison), not MinCaml

[FAQ 1] Is there an x86\_64 version?

[A] There is, but it is left as an exercise for students and _not_
included in this distribution.

[FAQ 2] Is there a version that emits C code?

[A] See above.

[Updates on October 9, 2013]

- Moved from SourceForge https://sourceforge.net/p/min-caml/code/ to
  GitHub https://github.com/esumii/min-caml

- Merged the Mac OS patch by shinh
  https://twitter.com/shinh/status/322043108021907458

[Update on July 24, 2012]

- 32-bit x86 (with SSE2, that is, Pentium IV or later) is now
  supported (on Linux and Cygwin); execute ./to\_x86 before make.

[Updates on September 17, 2008]

- PowerPC is now supported (in addition to SPARC), thanks to
  Ms. Masuko and Prof. Asai in Ochanomizu University.  You _must_
  execute either ./to\_ppc or ./to\_sparc _before_ make.

- The register allocator now uses a simpler algorithm.  It omits the
  backtracking (ToSpill and NoSpill) in previous versions.
