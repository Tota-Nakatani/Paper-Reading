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

![CodeCogsEqn-4](https://user-images.githubusercontent.com/57211829/79951430-a0cca500-84b3-11ea-805d-a4053618d1d5.png)

シグナル関数でバイナリ化を行う.

2. Stochastic

![CodeCogsEqn-5](https://user-images.githubusercontent.com/57211829/79951773-47b14100-84b4-11ea-8b3e-12fb33840e04.png)

ただしσはハードシグモイド関数である.

つまり, まとめると以下の数式になる.

![CodeCogsEqn-6](https://user-images.githubusercontent.com/57211829/79952114-df169400-84b4-11ea-8932-ffd71043a977.png)


## Algorithm

学習の処理をforward propagation, backward propagation, updateと分類すると, forward propagationとbackward propagationではweightをbinarizationし, updateでは実数を使用します. updateを実数で行う理由は, parameterの変化量は非常に小さいため.


![a](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.amazonaws.com%2F0%2F100523%2F88ccb10d-675d-a57e-017d-ef60976f96e3.png?ixlib=rb-1.2.2&auto=format&gif-q=60&q=75&w=1400&fit=max&s=6c01ddfa17abf71cbafb39c4230dda36)



## 議論はある？
全ての計算がバイナリ化されているのではなく, 重みのみでしか行われていない.


## 次に読むべき論文は？
Binarized Neural Networks: Training Neural Networks with Weights and Activations Constrained to +1 or −1

## 参考
・　https://metrica-tech.hatenablog.jp/entry/2019/06/15/000000

・　https://qiita.com/supersaiakujin/items/fb0f6201a6a6da1981b2
