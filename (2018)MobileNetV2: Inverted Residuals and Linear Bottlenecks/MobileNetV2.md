
## どんなもの

### 論文
Mobilenetv2: Inverted residuals and linear bottlenecks


### 著者・所属機関
Sandler, Mark, et al(Google)


### 投稿日
2018


## Abstract
Pointwiseの1*1Convの計算量を減らす**bottleneck構造(Inverted Residual)** を導入してMobileNetをさらに軽量化


## 先行研究と比べて何がすごい？
さらに軽量化された

## 技術や手法のキモはどこ？
### 元々のBottleneck(ResNetのやつ)

![image](https://user-images.githubusercontent.com/57211829/81262869-9399e380-9079-11ea-8f09-ea4efa79254b.png)

これはplainな構造

![image](https://user-images.githubusercontent.com/57211829/81262894-9dbbe200-9079-11ea-82f8-c5e79a36e79b.png)

![image](https://user-images.githubusercontent.com/57211829/81263100-0a36e100-907a-11ea-8820-d7979d32ac0b.png)


こう変更しても計算量が同じだがlayer数も増え, 特徴をより捉える

 C方向は**thcik-thin-thick**
 
 ### Inverted Residual Block
 **thin-thick-thin**とResNetと反対の構造
 
 必要な特徴はthinに詰まっているためthin同士をshortcut
 
 ![image](https://user-images.githubusercontent.com/57211829/81263445-a234ca80-907a-11ea-87f0-bd11e511222f.png)

 3x3Depthwise Convを1x1Conv(Pointwise Conv)で挟む
 
**小さな1x1Conv**を2つ使うことで計算量ボトルネックであった1x1Convを小さな計算量で近似


![image](https://user-images.githubusercontent.com/57211829/81263543-d1e3d280-907a-11ea-9f24-bbfac4389b29.png)


## 次に読むべき論文は？
MobileNet_v3(SE モジュールの導入)

