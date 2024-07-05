---
marp: true
theme: academic
paginate: true
math: katex

---
<!-- _class: lead -->
# 正規分布とは
#### ~ 確率になれよう ~

<br>

**もちくん（森田 嵩基）**
jack 4年生（名大５年生）

---
<!-- _header: 確率｜なぜ確率を勉強するのか -->
## 人類には不確かさを表見する力が必要
- 世の中はわからないことだらけ
- 必ずそうなると言えることは少ない
- e.g. サイコロ, 天気, サザエさんのじゃんけん, etc

### ということで確率のお勉強です

---
<!-- _header: 確率の基礎｜復習(1) -->
### 確率変数
- 値が確率的に決まる変数
- e.g. サイコロの目, トランプの数字
$$ 
p(x=1) = \frac{1}{6} 
$$

### 確率分布
- 確率変数の取りうる全ての値に対しての確率を表したもの
$$
p(x)
$$


--- 
<!-- _header: 確率の基礎｜復習(2) -->
### 確率分布の満たす条件
#### 離散
$$
0 \le p(x_k) \le 1　(k = 1,2,...,N)
$$
$$
\sum_{k=1}^{N}p(x_k) = 1
$$


--- 
<!-- _header: 確率の基礎｜復習(3) -->
### 確率分布の満たす条件
#### 連続
$$
任意のxに対して，p(x) \ge 0
$$
$$
\int_{-\infty}^{\infty}p(x)dx = 1
$$

- 連続の場合，確率分布ではなく**確率密度関数**という
- ※単に確率分布ということも多い
- ある確率変数の値を与えたときの確率密度関数の値を<br>**確率密度**あるいは**尤度**という


--- 
<!-- _header: 確率の基礎｜復習(4) -->
### 期待値 $\mu$
#### 離散
$$
\mathbb{E}[x] = \sum_{k=1}^{N}x_kp(x_k)
$$
#### 連続
$$
\mathbb{E}[x] = \int_{-\infty}^{\infty}xp(x)dx
$$

--- 
<!-- _header: 確率の基礎｜復習(5) -->
### 分散 $\sigma^2$
#### 離散
$$
\mathbb{V}[x] = \mathbb{E}[(x-\mu)^2] = \sum_{k=1}^{N}(x_k - \mu)^2p(x_k) 
$$
#### 連続
$$
\mathbb{V}[x] = \mathbb{E}[(x-\mu)^2] = \int_{-\infty}^{\infty}(x-\mu)^2p(x)x
$$
- 分散の平方根である$\sigma$を**標準偏差**という

---
<!-- _header: 正規分布 -->
- 正規分布$\mathcal{N}$（ガウス分布）
- 「確率変数が平均$\mu$と標準偏差$\sigma$の正規分布に従う」とは

$$
x \sim \mathcal{N}(x;\mu, \sigma)
$$
$$
p(x) = \mathcal{N}(x;\mu, \sigma) = \frac{1}{\sqrt{2\pi} \sigma}\exp(-\frac{(x - \mu)^2}{2 \sigma^2})
$$

- $\mathcal{N}(x;\mu, \sigma)$:$\mu$と$\sigma$が与えられたときの正規分布
- ";"の左側が確率変数, 右側がパラメータ



---
<!-- _header: 正規分布｜python -->
```python
import numpy as np

def normal(x, mu=0, sigma=1):
  return 1/ (np.sqrt(2 * np.pi) * sigma) * np.exp(-(x-mu)**2 / (2 * sigma**2))

```
![w:500 center](./images/normal00.png)


---
<!-- _header: 正規分布｜python -->
- $\mu$と$\sigma$を変えてみる
- 確率密度が最大となる位置や分布の山の形が変わる

![](./images/normal01.png) ![](./images/normal02.png)


---
<!-- _header: 中心極限定理 -->
- **任意の**確率分布$p(x;\mu,\sigma)$に従う確率変数$x$を$N$点サンプリング
- サンプルの平均$\bar{x}$は **正規分布** $\mathcal{N}(\bar{x}; \mu, \frac{\sigma^2}{N})$に従う
- サイコロをいっぱい振れば出目の平均は$\frac{7}{2}=3.5$に近くなる

![h:400](./images/normal03.png) ![h:400](./images/normal04.png)

---
<!-- _header: 中心極限定理｜サンプル和の分布 -->
$$
\bar{x} \sim \mathcal{N}(\bar{x}; \mu, \frac{\sigma^2}{N})
$$
- サンプル和$s$の分布はどうなる？
$$
s = \sum_{k=0}^{N}x_k = N\bar{x}
$$
- $\bar{x}$が正規分布に従うので，$N\bar{x}$も正規分布に従う
$$
\mathbb{E}[N\bar{x}] = N\mathbb{E}[\bar{x}] = N\mu \\
\mathbb{V}[N\bar{x}] = N^2 \mathbb{V}[\bar{x}] = N^2 \frac{\sigma^2}{N} = N\sigma^2
$$

---
<!-- _header: まとめ -->

- 正規分布は確率論において最も基礎的で最も重要な分布
- 中心極限定理によって任意の分布と正規分布がつながっている
- 身の回りは正規分布であふれている
  - 測定誤差
  - 製品サイズ
  - 身長 
- 一つひとつは小さな誤差でも計測環境や計測過程，製造工程，遺伝，家庭環境，食生活など誤差の発生要因が重なると誤差の総和は正規分布に近づく
---










