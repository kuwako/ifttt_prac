# IFTTTとRocketChatBotの連携方法
## RocketChat側準備
### WebHookUrl発行
  1. RocketChatの左上のにある自分の名前をクリック
  - 「管理」をクリック
    - 「管理」がない人は権限ないので管理者の方に権限をもらう
  - 「サービス連携」をクリック
  - 新しいサービス連携をクリック
  - Incoming WebHookをクリック
  - 以下の内容で適宜作り変更を保存をクリック
    - 有効: はい
    - 名前: {{わかりやすい名前}}
    - 投稿先チャンネル: {{投稿したいチャンネル名 (先頭に#をつける (ex: #bot_prac))}}
    - 投稿ユーザー: {{自分のユーザー名とか (ex: tanaka)}}
    - エイリアス: {{表示上の名前 (ex: ロケチャボット)}}
    - アバターURL: {{適当な画像URL}}
    - 絵文字: {{記入しなくて良い}}
    - スクリプトを有効にする: いいえ
    - Script: {{記入しなくて良い}}
  - Webhook URLができているはずなので、コピーする

## IFTTT側準備
### トリガー側を作る
  1. トリガーしたいサービスとイベントを作る (ex: tweetをlikeしたら...)
    - https://ifttt.com/create/if?sid=0
    - ここがわからない方はまずIFTTTの使い方を調べてください

### 実行側を作る
  1. Makerというサービスと連携する
    - Searchから検索するか、https://ifttt.com/maker 直接飛んでください
  - Makerの設定まで漕ぎ付ける
    - ここまでできない人はまずIFTTTの使い方を調べてください
  - Makerの設定をする
    - URL: {{発行したWebHookURLを貼り付ける}}
    - Method: POST
      - ※Saveして戻ってくるとなぜかGETになっているが、ちゃんと保存はされている
    - Content Type: application/json
    - Body: {"text": "hogehoge"}
      - ※真下あたりに[+Ingredient]とあるところをクリックすると、トリガーとして連携しているサービスで引っ張ってこれる変数が出るので、クリックすると使える
  - Saveをクリック
  - 連携をOnにする

以上
