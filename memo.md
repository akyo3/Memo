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

## その他は後ほど記述予定。
