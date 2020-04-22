## どんなもの

### 論文
BinaryConnect: Training Deep Neural Networks with binary weights during propagations

### 著者・所属機関
Matthieu Courbariaux(E ́cole Polytechnique de Montre ́al)・Yoshua Bengio(Universite ́ de Montre ́al, CIFAR Senior Fellow)


### 投稿日
18 Apr 2016


## abstract
近年Deep Learningの発展に伴い, 学習時や本番環境での計算量が膨大になっている. Deep Learnigにおける計算は行列の乗算が主である.

**重みの2値化** によるDeepLearningの計算高速化の手法の1つとして, **BinaryConnect(BC)** を提案した. これにより乗算が加算に置き換えられ計算量が削減された.


## 先行研究と比べて何がすごい？
既存研究では, 重みの更新にExpectation Back Propagetion (EBP)を用いていたが, 本研究ではBack Propagation(BP)を行った。

CNNの学習に成功した

## 技術や手法のキモはどこ？
### 重みのバイナリ化
決定的(Determnistic)な方法と, 確率的(Stochastic)な方法がある.

1. Deterministic

<img src="https://latex.codecogs.com/gif.latex?w_{b}=\begin{cases}&space;&plus;1\hspace{6}&space;if&space;w\geq&space;0,\\&space;-1&space;\hspace{6}&space;otherwise.&space;\end{cases}"







## 議論はある？

## 次に読むべき論文は？
