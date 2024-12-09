# ポートって何？

---


### 役所の窓口としてのポートの例え
1. 東京都（IPアドレス）:   
    - 一つの大きな存在
    - どの窓口に行くかを指定しないと、何をしたいのか分からない。   
   
   
2. 窓口（ポート番号）:   
    - それぞれに役割が決まっている。
    - 例：   
   
        - 80番窓口（HTTP） → 住民票の発行（Webページを閲覧)   
   
        - 443番窓口（HTTPS） → 住民票の発行（セキュリティ強化版：暗号化通信）   
   
        - 22番窓口（SSH） → 職員専用窓口（サーバー管理者が操作）   
   
        - 3306番窓口（MySQL） → 資料室（データベースにアクセス）
3. ルール（セキュリティグループ）:   

    - 一般市民が全ての窓口を使えるわけではない。   

    - 一部の窓口（例えば22番）は職員専用で、市民には閉じている。
### 具体的な例   

**Webページを開く場合:**   
あなた（市民）が東京都（サーバー）にアクセス。
住民票がほしい → 窓口80番（HTTP）に行く。
窓口の担当者（Webサーバー）が対応してくれる。   

**サーバー管理者が作業する場合:**   
管理者（職員）が東京都（サーバー）にアクセス。
管理専用の22番窓口（SSH）を通して中に入る。
サーバーの設定変更や監視を行う。   

### 役所の例えでのセキュリティの重要性   

**全ての窓口を開放しない:**    
「全窓口開放（0.0.0.0/0）」だと、誰でもどの窓口でも自由に入れるので危険。
必要な窓口だけ開けておくべき。   
**職員専用窓口は厳重に管理:**   
SSH（22番）やデータベース（3306番）は一般市民が利用できないように、IPアドレス制限などでアクセスを絞る。
### 結論
サーバーは「東京都」、ポートは「役所の窓口」。
どの窓口がどのサービスに対応するかが明確で、必要な窓口だけ開放することで、安全で効率的な運用ができる。
