# ドリブルストライカー 3D（Dribble Striker 3D）

スマホ縦持ち向けの3Dサッカー・ドリブルゲームです。守備網をかわしてドリブルし、GKの逆を突いてシュートを決めます。速さ（秒数）と成功率で高得点を狙います。

## 遊び方

- 画面左の**バーチャルスティック**で前後左右に移動、右下の**SHOOTボタン**でシュート。
- PCは**矢印キー / WASD**で移動、**Space**でシュート。
- 守備（赤）にボールへ踏み込まれると奪取されます。GK（黄）の逆サイドを狙って決めましょう。
- 全5ステージ。守備人数が 3 → 5 → 7 → 9 → 11 人と増えて難化します。
- 右上のミニMAPと上部のリアルタイム指標（速度・走行距離・ゴールまでの距離・ボール速度）を参考に攻めてください。

## 公開方法（GitHub Pages）

1. GitHub で新しいリポジトリを作成します（例：`dribble-striker`）。
2. `index.html` をリポジトリ直下にアップロードします（`.nojekyll` も一緒に置くと安全です）。3Dモデルは `index.html` に埋め込み済みなので、`Man.glb` のアップロードは不要です。
3. リポジトリの **Settings → Pages** を開きます。
4. **Build and deployment** の Source を **Deploy from a branch** にし、Branch を `main`（フォルダは `/root`）に設定して保存します。
5. 数十秒〜数分後、`https://<ユーザー名>.github.io/<リポジトリ名>/` で公開されます。

## 動作要件 / オフラインでの遊び方

3D描画エンジン **Three.js** は容量が大きいため `index.html` には埋め込まず、起動時に読み込みます。読み込み順は次の通りで、**ローカルファイルを最優先**します。

1. `index.html` と同じフォルダの `three.min.js`（無ければ `libs/` や `vendor/` も探索）
2. 見つからなければ CDN（cdnjs → jsdelivr → unpkg）を自動で順に試行

つまり、**オンラインなら何も用意せずそのまま動作**します。

### 「3Dライブラリを読み込めませんでした」と出る場合

インターネット未接続、または社内ネット/広告ブロッカーが CDN を遮断しています。オフラインで遊ぶには、ネットに繋がる端末で下記を保存し、`index.html` と同じフォルダに置いてください（1ファイルだけでOK）。

- `three.min.js` ← https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js

選手の3Dモデルもオフライン表示したい場合は、次の2つも同じフォルダに追加します（無くても簡易な人型表示で動作します）。

- `GLTFLoader.js` ← https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/loaders/GLTFLoader.js
- `SkeletonUtils.js` ← https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/utils/SkeletonUtils.js

## ファイル構成

- `index.html` … ゲーム本体（これ単体で動作します）
- `.nojekyll` … GitHub Pages で余計な処理を無効化するための空ファイル
- `Man.glb` … 選手3Dモデルの元データ（埋め込み済みのため公開には不要・任意）
