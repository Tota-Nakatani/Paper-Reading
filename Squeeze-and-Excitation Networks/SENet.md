## どんなもの

### 論文
Squeeze-and-Excitation Networks



### 著者・所属機関
Jie Hu,Li Shen,Samuel Albanie,Gang Sun,Enhua Wu


### 投稿日
25 Oct 2018


## Abstract
SEモジュールを従来のCNNモデルに導入することで, チャンネル方向の特徴を強調し, 計算量をほとんど増やさずに精度を向上することができる.

## 先行研究と比べて何がすごい？
空間方向への工夫からチャンネル方向に対しての工夫への転換点

## 技術や手法のキモはどこ？
### Squeeze-and-Excitation 構造

![image](https://user-images.githubusercontent.com/57211829/80678614-38567700-8af6-11ea-90a8-69da9c504436.png)

1. Global Average PoolingでSqueezeして空間方向を潰す(1,1,C)
2. FCでchannelをC/rへ(1,1,C/r)
3. ReLU関数
4. FCでchannelをCへ(1,1,C)
5. Sigmoid関数
6. 元のFeature mapに対して5.の出力をかける(Excitation)


なお, FCはConv2D(1,1,C/r)に等価.

#### squeeze
空間方向の大域的情報を取り出す.
そのため, 層が浅くて畳み込みが十分に繰り返されてない状況でその効果を発揮(入力に近い層では大域的特徴が保持されている)
実験でも,深いところのSE moduleを取り除いても性能はほぼ変わらないことが示されている.

#### Excitation
flexibility を高めるためにチャンネル間の非線形な関係を学習できるものにしたいのでReLUを入れる
複数チャンネル同士の相互作用を考慮してsoftmax(特定のチャネルのみが特徴付けられてしまう)ではなくsigmoidでweightを作る

## 次に読むべき論文は？
scSENet
