# 正方形上を動く球体の通過領域の可視化 (Swept Volume of Sphere on Square)

1辺の長さが1の正方形 $ABCD$ の辺上を、半径1の球体の中心 $P$ が1周するときに通過する**完全な通過領域（通行領域／掃引立体）**を、HTML5 / WebGL (Three.js) を用いてリアルタイム3Dで可視化するWebアプリケーションです。

![Three.js](https://img.shields.io/badge/Three.js-r128-black?style=flat-square&logo=three.js)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v3-38BDF8?style=flat-square&logo=tailwind-css)
![GitHub Pages](https://img.shields.io/badge/GitHub_Pages-Compatible-22C55E?style=flat-square&logo=github)

---

## 📐 数学的な問題定義と解

### 問題設定
3次元空間内において、1辺の長さが $1$ の正方形 $ABCD$ の辺上を点 $P$ が1周運動する。点 $P$ を中心とする半径 $1$ の球体（内部含む）が通過する領域 $V$ の形状と体積を求めよ。

### 立体の幾何学的構造
通過領域は、全高 $y \in [-1, 1]$（高さ 2）にわたる以下の3つの領域の和集合（Union）として構成されます。

1. **中央の直方体**: 正方形 $ABCD$ を底面とし、高さ $2$（$y \in [-1, 1]$）の $1 \times 1 \times 2$ の直方体。
2. **4つの側面円柱**: 正方形の4辺（長さ 1）に沿って半径 $1$ の球が移動してできる、長さ 1 の直円柱側面。
3. **4つの角（コーナー）の球状部分**: 頂点 $A, B, C, D$ を中心とする半径 1 の球体が、隣接する円柱と隙間なく滑らかに接続された1/4球（扇形）構造。

### 体積の理論解
高さ $y \in [-1, 1]$ における断面積 $S(y)$ の積分により求められます。
半径を $r(y) = \sqrt{1 - y^2}$ とすると、断面 $S(y)$ は中央の正方形、4つの長方形、および4つの四分円弧で構成されるカプセル型となります。

$$S(y) = 1 + 4r(y) + \pi r(y)^2$$

これを $y \in [-1, 1]$ で体積積分すると：

$$V = \int_{-1}^{1} S(y) \, dy = 2 + 8 \int_{0}^{1} \sqrt{1-y^2} \, dy + 2\pi \int_{0}^{1} (1-y^2) \, dy$$

$$\mathbf{V = 2 + 2\pi + \frac{4}{3}\pi = 2 + \frac{10}{3}\pi \approx 12.472}$$

---

## ✨ 主な機能

- **3D インタラクティブ操作**: ドラッグで回転、スクロールで拡大縮小、右ドラッグで移動。
- **運動アニメーション**: 点 $P$ が正方形の辺上を動く速度の制御および一時停止/リセット。
- **累積軌跡表示**: 点 $P$ が移動したパスに連続して配置される球群の軌跡（トグル切り替え可能）。
- **断面カット表示 (Clipping Plane)**: Y軸方向の任意の高さで立体をスライスし、**内部が充填されている様子（ソリッド構造）**を確認可能。
- **不透明度調整**: 外形のメッシュを半透明にして、内部の正方形フレームや点 $P$ を透視。
- **数学的解説モーダル**: ダイアログで形状の分解構造や体積の導出を表示。

---

## 🚀 使い方 / 動作方法

### 1. ローカルで実行する場合
特別なビルド環境やNode.jsの設定は不要です。

1. このリポジトリをクローンまたはZIPダウンロードします。
   ```bash
   git clone https://github.com/<your-username>/<your-repo-name>.git
   ```
2. ダウンロードしたフォルダ内の `index.html` を任意のWebブラウザ（Chrome, Edge, Firefox, Safari等）で開きます。

### 2. GitHub Pages で公開する場合
1. GitHub にリポジトリを作成し、`index.html` をルートディレクトリに push します。
2. リポジトリの **Settings** ➔ **Pages** に移動します。
3. **Source** を `Deploy from a branch` に設定し、`main` (または `master`) ブランチの `/ (root)` を選択して保存します。
4. 数分後に発行される URL にアクセスするとブラウザ上で閲覧・操作可能です。

---

## 🛠 使用技術・ライブラリ

- **HTML5 / CSS3**: レイアウトおよびUIコントロール
- **JavaScript (ES6+)**: 立体幾何アルゴリズムおよびコントロールロジック
- **[Three.js (r128)](https://threejs.org/)**: 3D レンダリング・メッシュ生成・ライティング
- **[Tailwind CSS](https://tailwindcss.com/)**: モダンでレスポンシブなUIデザイン
- **[FontAwesome](https://fontawesome.com/)**: アイコン表示

---

## 📄 ライセンス

MIT License

自由にフォーク、改変、学習や授業等の教材としてご利用ください。
