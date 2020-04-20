
## どんなもの

### 論文

Distilling the Knowledge in a Neural Network



### 著者・所属機関
Geoffrey Hinton(Google)・Oriol Vinyal(Google)・Jeff Dean(Google)



### 投稿日
9 Mar 2015(NIPS 2015 Deep Learning Workshop)



## Abstract
CNNのデータ圧縮・軽量化に関する論文

トレーニング時は大量の訓練データを用いて、大規模なモデル(教師モデル)を訓練して精度を高めることが目標である. しかし, 実環境・本番では計算ソースに限りがあるためモデルがメモリに乗らないなどの問題がある. 本論文では, 教師モデルから精度を保ったまま小規模モデル(生徒モデル)へ知識を蒸留する.

温度つきSoftmax cross-entropyによる大規模モデルから小規模モデルへの知識の転移手法 Distillation を提案. 画像認識(MNIST)と音声認識タスクで効果を確認


## 先行研究と比べて何がすごい？
Caruanaらの教師出力と生徒出力(共にSoftmax)の二乗誤差を最小化する手法を改良

## 技術や手法のキモはどこ？
モデルの知識が入力から出力への写像によって獲得されるものであると考える. つまり, 特定の入力を与えた時の出力に有益な情報が存在していると考える.
Distillationは, Teacherの出力 (予測確率)を使ってStudentの学習を行う手法.
ここでは具体例として分類モデルについて考える.
通常の分類モデルでは, 確率正解ラベルyに対する対数尤度pをSoftmax cross-entropyで学習を行う.
![CodeCogsEqn-2](https://user-images.githubusercontent.com/57211829/79750759-76140c80-834c-11ea-980d-fdc1bb932e10.png)

この副作用として, 不正解ラベルに対する予測確率も得られる. 
例えば, 正解ラベルがsports carであるとき同時に成果ではないTrack carやCarrotの予測確率も同時に得られる.
![class](https://paperdrip-dl.github.io/assets/img/20181223/classification.png)
本論文は, この確率分布自体(sports car以外の確率も学習させる)を生徒モデルでは学習することで知識の蒸留が行われるという考え方.

教師モデルの出力をSoft Taeget, GroundTruthの分布をHard Targetとしてそれぞれのcross entropyを組み合わせた誤差関数を最適化する.
ここでSoft Targetに対するSoftmaxに**温度付きSoftmax関数**を導入したことが一番のキモ.
これにより, 小さな出力(不正解ラベルの出力)も強調され, 正解ラベルだけではなく確率分布全体を表現できる.
温度付きSofmax関数は次の式で表される. Tは温度定数(T>1)であり強調度合いを決定するパラメータである.
![CodeCogsEqn-3](https://user-images.githubusercontent.com/57211829/79752836-deb0b880-834f-11ea-986f-be85f217170c.png)



## 参考
