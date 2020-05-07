
## どんなもの

### 論文
Mobilenets: Efficient convolutional neural networks for mobile vision applications



### 著者・所属機関
Howard, Andrew G., et al(Google)


### 投稿日
April 2017


## Abstract
Mobile端末向けの軽量CNNモデル

## 先行研究と比べて何がすごい？
Conv2Dを２つの構造に分けた**Depthwise Seperable Conv**に

1/8~1/9程度パラメータを減らした


## 技術や手法のキモはどこ？
### 通常のConv

![image](https://user-images.githubusercontent.com/57211829/81260323-c2fa2180-9074-11ea-9c9a-5da12db2f21b.png)

パラメータ数:M * K * K * N * F * F

これを空間方向へのConv(Depthwise)とチャンネル方向のConv(Poinwise)を**順番に行うことで近似(計算量はdown)**

###Depthwise Conv

![image](https://user-images.githubusercontent.com/57211829/81260590-44ea4a80-9075-11ea-9772-8cf104ec8fae.png)

**チャンネル毎に1対１対応**するフィルターで畳み込み

パラメータ数:K * K * N * F * F

### Pointwise Conv

![image](https://user-images.githubusercontent.com/57211829/81260707-87138c00-9075-11ea-9698-62562d337d8b.png)

1*1の畳み込み, つまり空間方向はそのままでC方向の圧縮・拡大を行なっている

パラメータ数:M * N * F * F * 1 * 1

### パラメータ数

MK^2NF^2/(K^2NF^2+MNF^2)=(1/K^2)+(1/M)

と削減される

## 議論はある？
Conv(1,1)の計算量
## 次に読むべき論文は？
MobileNet_v2
## 参考
https://qiita.com/omiita/items/77dadd5a7b16a104df83
