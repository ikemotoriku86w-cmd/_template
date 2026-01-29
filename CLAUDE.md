# Claude Code 用コンテキスト

## 基本ルール

- やりとりは全て日本語で行ってください

## 他のエージェントとの協働

### Gemini CLI との協働

Userが **「Geminiを使って」「Geminiに聞いて」** （またはそれと同義の表現）という内容で指示した場合、または以下の状況では Gemini CLI と協働してください：

**コマンド：**
```bash
npx gemini -y "プロンプト"
```

**注意事項：**
- `-y` オプションで自動承認モード（YOLOモード）が有効になります
- positional argumentとして直接プロンプトを渡すことで、ワンショット実行になります

### Codex CLI との協働

Userが **「Codexを使って」「Codexに依頼して」** （またはそれと同義の表現）という内容で指示した場合、または以下の状況では Codex CLI と協働してください：

**コマンド：**
```bash
npx codex exec --dangerously-bypass-approvals-and-sandbox --skip-git-repo-check "プロンプト"
```

**注意事項：**
- `exec` サブコマンドで非対話型実行になります
- `--dangerously-bypass-approvals-and-sandbox` で自動承認・サンドボックスなしで実行します
- `--skip-git-repo-check` でgitリポジトリチェックをスキップします

## 協働の進め方

1. タスクの性質を分析し、どのエージェントが最適かを判断
2. 必要に応じて他のエージェントを呼び出し、結果を統合
3. 最終的な成果物をUserに分かりやすく提示

## 注意事項

- 他のエージェントを呼び出す前に、タスクの目的と期待する成果を明確にする
- 複数のエージェントが関与する場合は、役割分担を明確にする
- 最終的な判断や統合は Claude Code が担当する