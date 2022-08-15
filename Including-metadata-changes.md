# プール情報(pool.cert)の更新

## poolMetaData.jsonの修正
### Githubでホストしている場合
1-1. Githubアカウントへログインします

  - [poolMetaData.json](https://github.com/Dow-shi/cardano-stake-pool/blob/main/poolMetaData.json)

---

1-2. ログインしたらファイルを編集しますので赤枠の箇所をクリックします
![1](https://user-images.githubusercontent.com/80967103/184645390-6c38d896-b90b-4595-b234-5167c5bd2815.png)

---

1-3. poolMetaData.json内の内容を変更します  
`留意点`：  
1. `ticker名の長さ`は`3～5文字以内`で、`A-Zと0-9のみ`で構成する必要があります。  
2. `descriptionの長さ`は`255文字以内(255byte)`となります。（`ひらがな、漢字、カタカナは1文字2byte`）  
3. `<>←山かっこ内と<>は不要です`
```
{
"name": "<新しいプールの名前>",
"description": "<プール説明>",
"ticker": "<ティッカー名>",
"homepage": "https://twitter.com/Dow_shi1",
"extended": "https://raw.githubusercontent.com/Dow-shi/cardano-stake-pool/main/extendedmeta.json"
}
```

---

1-4. 変更し終えたら、「Commit changes」をクリックしてコミットします
![2](https://user-images.githubusercontent.com/80967103/184645692-3b4ca575-3380-405e-83d3-cdb23a53905e.png)

---

1-5. 「Raw」ボタンをクリックして、「 https://raw ~ 」から始まるURLをコピーします。
![3](https://user-images.githubusercontent.com/80967103/184646301-db076ca7-10f4-4b3a-a77e-f3eef725b2b8.png)  
> お使いのブラウザのURL  
![4](https://user-images.githubusercontent.com/80967103/184646900-0ea38022-ef87-4d0c-ab1e-f2e33594d020.png)

---

1-6. URLは64文字より短くする必要があるため、以下のサイトでURLを短縮します。  
[bitly.com](https://bitly.com/)  
「Get Started for Free」→「FREE」内の「Get Started」→現在使用しているGoogleアカウントでbitlyのアカウントを作成する場合は、「Sign up with Google」をクリックして進めてください。そうでない場合は、必要項目を入力してください。

---

1-7. 「+」→「Link」をクリックします  
![5](https://user-images.githubusercontent.com/80967103/184650279-fec4164d-8804-48d2-9b70-585b2973f882.png)

---

1-8. 「ENTER LONG URL」欄へ「 https://raw ~ 」のURLをペーストし「CREATE」をクリックして短縮URLを作成します  
![6](https://user-images.githubusercontent.com/80967103/184650553-e7f2f37e-e05e-4f8e-942f-b153e0a35293.png)

---

## 以降は以下の手順を見て実施してください
[プール情報(pool.cert)の更新](https://docs.spojapanguild.net/operation/cert-update/#__tabbed_1_1)

`注意点`：
1. 「メタデータ更新を含む場合」タブを実施
2. 以下のpoolMetaData.jsonの隣のURLは先ほど作成したbitlyの短縮URLへと変更する  

`×`  
> wget -O poolMetaData.json https://git.io/****  

`◯`  
> wget -O poolMetaData.json https://bit.ly/****  
3. 「登録証明書トランザクションを作成する」の「エアギャップオフラインマシン」下部のコマンドの`--metadata-url https://xxx.xxx.xxx/poolMetaData.json \`の箇所は先ほど作成したbitlyの短縮URLへと変更する  
(参考)： 
```
--metadata-url https://bit.ly/**** \
```
4. 念の為の振り返りとして  

`誓約(Pledge)について`
```
自分のプールに保証金を預けることをPledge(誓約)と呼びます  
・支払い用アドレス(payment.addr)の残高はPledge額よりも大きい必要があります。  
・誓約金はpayment.addrに入金されている必要があります。  
・設定した誓約数よりpayment.addrに入金されてるADAが下回っている場合、プール報酬が０になります。  
・誓約金はロックされません。いつでも自由に取り出せますがプール登録証明書を再提出する必要があります。  
```

---

## 忘れずにsjg-validation.jsonのティッカー名も変更しておきましょう
> こちらはトランザクション送信しないので最後に書きました。  

https://github.com/Dow-shi/cardano-stake-pool/blob/main/sjg-validation.json
