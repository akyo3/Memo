# Macで自動生成される.DS_Storeをgithubの全リポジトリで管理対象外にする

#### 実施詳細
1. Homeディレクトリに移動します。
```console
cd
```

2. .gitignore_globalファイルを生成します。
```console
touch ~/.gitignore_global
```

3. .gitignore_globalファイルを展開後、内容を記載し保存します。
```console
nano ~/.gitignore_global
.DS_Store
Ctrl + o
Ctrl + x
```

4. 以下のコマンド実行し、設定を反映します。
```console
git config --global core.excludesfile ~/.gitignore_global
```
