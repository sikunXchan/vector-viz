# VECTOR — 攻撃を、見て学ぶ。

セキュリティの攻撃手法を、**動くビジュアル**で1手ずつ理解するためのインタラクティブ学習コレクション。
コードや文章より速く腑に落ちることを狙った、静的サイト(HTML/CSS/JS のみ、ビルド不要)。

「攻撃を**やる**」ツール [SCS](https://github.com/sikunXchan/sikun-cyber-security) の姉妹プロジェクトで、
こちらは「攻撃を**見て理解する**」側。

## 収録レッスン

- **SQLi 認証バイパス** (`lessons/sqli-bypass.html`) — ログインの SQL 文が `admin' OR 1=1--` で
  どう書き換わり、なぜパスワード無しで管理者になれるのかを7手のステップで
- **パケットフロー** (`lessons/sqli-packetflow.html`) — 攻撃者 → Web サーバ → DB を流れる
  リクエスト/クエリ/応答をアイソメトリックに可視化

各レッスンは**自己完結した1枚の HTML**(外部ライブラリ・CDN 依存なし)。追加は
`lessons/` に HTML を置き、`index.html` のグリッドにカードを1枚足すだけ。

## ローカルで見る

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

## Vercel にデプロイ

ビルド不要の静的サイト。どちらでも:

**A. GitHub 連携(推奨)**
1. このリポジトリを GitHub に push
2. [vercel.com](https://vercel.com) で「Add New → Project」→ 該当リポジトリを import
3. Framework Preset は **Other**(ビルドコマンド無し・出力はリポジトリ直下)→ Deploy

**B. Vercel CLI**
```bash
npm i -g vercel
vercel        # プレビュー
vercel --prod # 本番
```

## 技術メモ

- 純粋な静的サイト(HTML/CSS/JS)。フレームワーク・ビルドステップ無し
- 可視化はすべて **2D Canvas / DOM**。外部3Dライブラリ非依存
- `prefers-reduced-motion` を尊重(アニメを止める)
