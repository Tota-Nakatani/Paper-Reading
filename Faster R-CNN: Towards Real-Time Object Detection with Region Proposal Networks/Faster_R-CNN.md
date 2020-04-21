## どんなもの

### 論文
Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks 



### 著者・所属機関
Shaoqing Ren・Kaiming He・Ross Girshick・Jian Sun 

### 投稿日
4 Jun 2015(CVPR)


## Abstract
Region Proposalを行うCNNをSelective Search等の手法の代わりにし,1つのネットワークに. Region Proposalから識別までを一括で学習(End to End)し高精度化

## 先行研究と比べて何がすごい？
RPNにより提案領域数抑制&mAP向上

スピードも向上(一画像あたりの処理時間はFats R-CNNの10分の１の0.2secondsに)

## 技術や手法のキモはどこ？
**Resion Proposal Net(RPN)** 
CNNからの入力(Feature map)を受け取り、低次元のFeature mapへ. 領域が物体か背景か(objectness)および位置の補正データ(corrdinates)を出力する.







## 議論はある？

## 次に読むべき論文は？
