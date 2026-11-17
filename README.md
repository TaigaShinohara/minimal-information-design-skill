# Minimal Information Design Skill

アプリの情報量を減らし、認知負荷を下げ、読まなくても直感的に使えるようにするための AI エージェント用スキルです。

核は8つの原則です。文字は最低限にし、増やすほど伝わらなくなる前提で、アイコン・図形・画像・操作UIへ置き換え、ページ分割と折りたたみで同時表示を減らし、重要でないものは切り捨てるか別の場所へまとめ、アニメーションで段階表示し、色・形・フォントの種類を増やさず、情報は重要度順に並べます。

## 特徴

- **物差しは1つ**：「読まなくても分かるか。3秒で次にすることが分かるか」
- **仕分けの型**：全要素を A（常時表示）／B（畳む・後出し）／C（消す・別場所・既定値）に分け、行き先のない要素は残さない
- **置換の優先順位**：実物・状態 → アイコン＋色 → 図形と量 → 色と状態変化 → 短い文字 → 文章（最終手段）
- **数値は正直に扱う**：要素の数え方を定義し、3割などの目安は「根拠のない目安、超えたら理由を記録するトリガー」と明記。一覧・表・ダッシュボードなど密度自体が価値の画面は例外
- **プラットフォームで分ける**：下部・右下のボタン配置は片手タッチ操作のモバイルだけ。デスクトップ／Webは読み順末尾と慣習位置、フォーカス順で判定
- **副作用への受け皿**：畳んだ・移した情報の到達確認（ステップ数と代表タスクの完遂）と、アクセシビリティ確認（読み上げ名、コントラスト、動きを減らす設定への追従など）を必須検証に含む
- **検証の手順つき**：3秒テスト・無読テスト・ぼかし見テストは初見の人が実施者。実画面が得られない場合の仮判定と未確認の閉じ方まで規定

## 構成

| ファイル | 内容 |
| --- | --- |
| `skills/minimal-information-design/SKILL.md` | スキル本体（8原則、重要度ランク、数え方、作業の流れ、検証の正本） |
| `skills/minimal-information-design/references/checklist.md` | 棚卸し記録、数値の目安、仕分けと検証の記録欄 |
| `skills/minimal-information-design/references/patterns.md` | 置換・分割・並び順・段階表示・切り捨ての場面別パターン |
| `skills/minimal-information-design/skill.yaml` | Muse 用スキル定義 |
| `skills/minimal-information-design/agents/openai.yaml` | Codex 用インターフェース定義 |

## インストール

このリポジトリを取得して、`skills/minimal-information-design/` をフォルダごとコピーします。補助資料も一緒に読み込めるよう、`SKILL.md` と `references/` を同じフォルダに置きます。

| エディター | 個人用スキルの保存先 |
| --- | --- |
| [Codex](https://learn.chatgpt.com/docs/build-skills)・[Cursor](https://cursor.com/docs/skills)（ローカル） | `~/.agents/skills/` |
| [Devin Local（Devin Desktop）](https://docs.devin.ai/desktop/devin-local/customizations) | `~/.agents/skills/` |
| [Claude Code](https://code.claude.com/docs/en/skills) | `~/.claude/skills/` |
| [VS Code の GitHub Copilot](https://code.visualstudio.com/docs/agent-customization/agent-skills) | `~/.copilot/skills/` |

macOS / Linux で Codex と Cursor の両方に導入する例です。

```sh
git clone --depth 1 https://github.com/TaigaShinohara/minimal-information-design-skill.git
mkdir -p "$HOME/.agents/skills"
cp -R minimal-information-design-skill/skills/minimal-information-design "$HOME/.agents/skills/"
```

ほかの Agent Skills 対応エディターでは、そのエディターのスキル保存先へ同じフォルダを配置します。初回の導入後は新しいチャットを開き、スキルが表示されない場合はエディターを再起動します。

以前のパス `minimal_information_design` から手動で導入していた場合は、古いフォルダをスキルの検索対象外へ移します。登録済みの呼び出し名は `minimal-information-design` に更新します。

## 使い方

「この設定画面の情報量を減らして、次にすることがすぐ分かるようにして」と依頼します。明示的に呼び出す場合は Codex で `$minimal-information-design`、Cursor と Claude Code で `/minimal-information-design` を使います。エディター側にスキル機能がない場合も、`SKILL.md` と `references/` をチャットで参照できます。

このスキルは単体で使えます。画面の狙いを決めるときは、利用できる環境で meaningful_app_design も併用できます。

## 経緯

2026-11-17 に作成し、同日に独立審査（条件付き合格 → 指摘6件すべて解消 → 再審査で合格）を経て v1.0.0 として公開。

## License

MIT License
