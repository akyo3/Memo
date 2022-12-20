## ありがちな問題

`git@github.com: Permission denied (publickey).`

```
ssh-add -l -E sha256
→The agent has no identities.
```

## 対処法
```
ssh-add ~/.ssh/(Your rsa)
```

## 結論
SSHの秘密鍵のロードを忘れずに。


## リポジトリ毎でアカウント指定（localユーザー指定）

```
cd [Git Repository]
git config user.name "Your Another Name"
git config user.email "Your Another Name"
```

## 以下のエラー対応

> ! [rejected]        main -> main (fetch first)
>error: failed to push some refs to 'gitMain:akyo3/Memo.git'

```console
git fetch
git merge
```

---

### 少し雑ですが忘れない為にメモしておきます。

## 複数アカウント切替え

```
nano ~/.bashrc

function gitMain() {
  git config --global user.name "MainUserName"
  git config --global user.email "MainUserEmail"
  git config --list
}

function gitSub() {
  git config --global user.name "SubUserName"
  git config --global user.email "SubUserEmail"
  git config --list
}

source ~/.bashrc
```

- Main
`$gitMain`

- Sub
`$gitSub`

# set
```
ディレクトリ移動後
git remote set-url origin gitMain:MainUserName/repo.git
git remote -v
```

# ssh疎通確認
```
ssh -T gitMain
or
ssh -T gitSub
```

- 疎通OKメッセージ
`Hi UserName! You've successfully authenticated, but GitHub does not provide shell access.`
