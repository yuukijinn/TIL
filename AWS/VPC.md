# VPC

---

### ルートテーブル

AWSルートテーブルと通信経路のまとめ
1. **ルートテーブルの基本**   
   - ルートテーブルは サブネットに関連付けられる 道順リスト。
   - サブネット内の全IPアドレスは、同じルートテーブル を参照する。
2. **行き先（経路）の意味**   
   - ルートテーブルが定める「行き先」は 通信の経路（手段） を意味する。
   - 実際に「何を、どこに送るか」は アプリケーションの機能 が決める。
3. **よく使う経路設定**   
   - 宛先	行き先	用途
   10.0.0.0/16	ローカル	VPC内の通信
   0.0.0.0/0	インターネットゲートウェイ (IGW)	インターネットへの通信
   pl-xxxxxxxx	S3 VPCエンドポイント	S3へのインターネット非経由通信
4. **S3アクセスについて**   
   - デフォルト: インターネット経由でS3にアクセスする。
     - ルートテーブル: 0.0.0.0/0 → IGW
   - VPCエンドポイント利用: インターネットを通らずAWS内でS3にアクセスする。
     - ルートテーブル: pl-xxxxxxxx → VPCエンドポイント
5. **ポイント**   
   - サブネットごとに1つのルートテーブル が関連付けられる。
   - IPアドレスごとに個別の経路を書くことは可能だが非現実的。
   - ルートテーブルに「VPC内部」「AWSサービス」「インターネット」の経路を書けば、必要な通信はカバーできる。
