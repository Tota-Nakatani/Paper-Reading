## どんなもの

### 論文

M2Det: A Single-Shot Object Detector based on Multi-Level Feature Pyramid Network

### 著者・所属機関


Qijie Zhao et al(北京大学・アリババ・テンプル大学)
### 投稿日
2019

## Abstract
すげー複雑にしてマルチスケールのfeature mapを利用(MLFPN)して小物体まで検知できるモデル

精度・速度ともにすごい


## 先行研究と比べて何がすごい？
SOTAのYOLOv3に対して, 速度・精度ともに上回る

## 技術や手法のキモはどこ？

### 全体構造

![image](https://user-images.githubusercontent.com/57211829/81301048-7da91480-90b3-11ea-90c9-9fb9b34f97e9.png)

かなり複雑そう・・・

１つ１つ分解してみていく

### BackBone

![image](https://user-images.githubusercontent.com/57211829/81301174-a9c49580-90b3-11ea-8efd-66dbfb85da5d.png)

SSDやFaster R-CNNのように特徴抽出を行うベースネットワークとしてVGGとResNetを採用


### MLFPN (Mulyi Level Feature Pyramid Networks)

### FFM_v1 (Feature Fusion Module)

![image](https://user-images.githubusercontent.com/57211829/81301878-9960ea80-90b4-11ea-9417-ffbd8ae279f3.png)

Backbone（ここではVGG)のconv4_3とconv5_3を解像度の大きい方に合わせてC方向にconcateすることによりBase featureを得る
SSDのように1つのfeature mapのみを使用するのではなく解像度の違う層をfusionさせることによりマルチスケールに対応する


### TUM(Thinned U-shape Module)

![image](https://user-images.githubusercontent.com/57211829/81302156-f2308300-90b4-11ea-9f1f-825659796081.png)

FFMの出力を入力とし, FCNのようなencoder-decoderのautoencoder構造になっている

encoder側とdecoder側のfmapを1:1対応でfusionさせ, pyramid構造のfmapを得る.

ただし, 足し合わせるfampの解像度は異なる. これによりまたマルチスケール対応.

このpyramidのうち最も解像度の高いものをFFM2に入力

### FFM_v2
TUMの最大解像度のfmapとbase featureをconcateしてまた次のTUMへ

これ繰り返すことにより **(高解像度のfmapに対するFFM_v2,TUMを繰り返す)Deepな特徴（小物体、エッジ)を捉えることができる!!**

###  SFAM (scale-wise Feature Aggregation Module )

![image](https://user-images.githubusercontent.com/57211829/81303799-273dd500-90b7-11ea-9374-2e8f571c4093.png)

TUMの出力のPyramid型のfmapたちのそれぞれ同じ解像度同士fmapをconcateして, SEモジュールを適用して１つのPyramid型のfmapに

以降はSSDと同じでconvかけてregとclsで学習する



## 参考
https://qiita.com/kzykmyzw/items/1831f70dcade04db2210
