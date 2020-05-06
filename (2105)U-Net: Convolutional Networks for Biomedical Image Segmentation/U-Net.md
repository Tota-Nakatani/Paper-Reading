## どんなもの

### 論文
U-Net: Convolutional Networks for Biomedical Image Segmentation

### 著者・所属機関
Olaf Ronneberger・Philipp Fischer・homas Brox

### 投稿日
18 May 2015


## Abstract
FC層を用いないCNNモデルで医療用画像のsegmentationを行なった.
現在のsegmentationのbaseになっている.

## 先行研究と比べて何がすごい？
FCを使っていない.
skip-connectionにより広域特徴をより捉えられている.

## 技術や手法のキモはどこ？
![image](https://user-images.githubusercontent.com/57211829/80674531-19071c00-8aed-11ea-9103-a014d99b6723.png)

### skip-connection
U-Netでは, チャネルに対する連結(**concatenate**)をしている. スキップ元の情報をそのまま使うことで, 位置情報を保っている.．
CNNでは特徴マップを畳み込むほど位置情報は曖昧になるが, Semantic Segmentationにおいて位置情報は非常に重要. 
故に, Up-Sampling後にencoder部の同次元数の特徴マップを連結することで, 従来どおり特徴を抽出しつつ位置情報を保持することができる.


## 次に読むべき論文は？
SENet,Deeplab
