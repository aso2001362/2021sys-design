```uml
@startuml
opt 未登録
ユーザー-> webサーバー:ユーザー登録
webサーバー -> DBサーバー : ユーザー登録
DBサーバー -> DBサーバー : 登録処理
DBサーバー -> webサーバー : 登録結果

alt 登録成功
 webサーバー -> ユーザー : 登録メッセージを表示
else 登録失敗
 webサーバー -> ユーザー : 失敗メッセージを表示
 
 end
end

@startuml
 ユーザー -> webサーバー : ログイン
 webサーバー -> DBサーバー : ログイン照会
 DBサーバー -> DBサーバー : ログイン処理
 DBサーバー -> webサーバー : 認証結果
 
 activate ユーザー
 alt 認証成功
 webサーバー -> ユーザー : ユーザー名を表示
 else 認証失敗
 webサーバー -> ユーザー : 失敗メッセージを表示
 end
 opt ログイン中
 ユーザー -> webサーバー : ログアウト
 webサーバー -> DBサーバー : ログアウト照会
 DBサーバー -> DBサーバー : ログアウト処理
 DBサーバー -> webサーバー : ログアウト結果
 webサーバー -> ユーザー : ログアウト結果
 end
 
 deactivate ユーザー
 @enduml
```

```uml
@startuml
ユーザー-> webサーバー:商品の購入
alt ログイン済み
webサーバー -> DBサーバー : 商品の購入
DBサーバー -> DBサーバー : 決済処理
DBサーバー -> webサーバー : 決済完了のメッセージを表示
webサーバー -> ユーザー : 決済完了のメッセージを表示
else 未ログイン
alt ユーザー登録済み
webサーバー -> 
 webサーバー -> ユーザー :ログインを促すメッセージを表示
else ユーザー未登録
webサーバー -> ユーザー : 新規のログインの案内メッセージを表示
 end
end
 @enduml
```

```uml
@startuml
ユーザー -> webサーバー:商品検索ボタンを押す
webサーバー -> ユーザー:顧客に合った商品を絞り込むためのアンケートを表示
alt アンケートに回答
ユーザー -> ユーザー:アンケート記入
ユーザー ->webサーバー:アンケート送信
webサーバー -> DBサーバー:商品の絞り込み
DBサーバー -> DBサーバー:商品の絞り込み
DBサーバー -> webサーバー:絞り込み結果を表示
webサーバー -> ユーザー:絞り込み結果を表示
else アンケート未回答
webサーバー -> ユーザー:商品一覧を表示
end
@enduml
```