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

スピードも向上(1画像あたりの処理時間はFats R-CNNの10分の１の0.2secondsに)

## 技術や手法のキモはどこ？
**Resion Proposal Net(RPN)** 

VGG16, ZFNet等のBaseCNNからの出力(Feature map)を受け取り, 低次元のFeature mapへ. 領域が物体か背景か(objectness)および位置の補正データ(corrdinates)を出力する.
BaseCNNからRPNまで統一された１つのNeual Network(**One-stage**)で構築できるため同時に学習(**End-to-End**)することができる.

![image](https://user-images.githubusercontent.com/57211829/79826102-cdaa8a80-83d5-11ea-9e70-1aff5595d46c.png)![image](https://user-images.githubusercontent.com/57211829/79826130-e024c400-83d5-11ea-81b1-82dee13d1cfc.png)

**全体の流れ**

1. BaseNet(VGG16)に画像を入力し, 中間層の特徴マップを得る.(H/16, W/16, 512)
2. BaseNetから得た特徴マップ(H/16, W/16,512)にConv2D((3,3),512)
3. さらにConv2d((1,1),k)とConv2D((1,1),4k)を掛ける. それぞれclsとregになっている.(RPNの出力)
4. RPNからのBBはIoU>0.7:positiveとIoU<0.3:negativeとしてNMSを適用したものを学習に使用
5. 特徴マップのBBのエリアに対してRoI Poolingを行い、(N,7,7,512)tensorを出力. ここでNはBBの総数
6. Flatten, FCにより他クラス分類と矩形回帰(Reg)を行う.



## 次に読むべき論文は？
Mask R-CNN, YOLO,SSD
