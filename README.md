# Cosmos

## 環境構築
- OS: Amazon Linux 2023
- EC2インスタンスはオンプレではなくAWSのクラウド上に立っているのでプロキシ設定は不要

## git設定
- git --version
- sudo dnf install -y git
- フォーク作成＆クロー
  - GitHub/GitLab上でフォーク作成
  - mkdir projects
  - cd projects
  - git clone https://github.com/nvidia-cosmos/cosmos-predict1.git
- フォーク確認
  - cd cosmos-predict1
  - git remote -v
- upstream (公式) リモートを追加
  - git remote add upstream https://github.com/nvidia-cosmos/cosmos-predict1.git
  - git remote -v
- 公式リポジトリの最新情報を取り込む
  - git fetch upstream
  - git branch -rで確認
- 実験用ブランチを切る（新ブランチを作成し切替）
  - git checkout -b experiment-1 upstream/main
  - git branchで確認
- コードを改造してコミット
  - touch tmp.py
  - git add .
  - git commit -m "add tmp.py"
- 実験ブランチをorigin（自分用写し）にpush
  - git push -u origin experiment-1
