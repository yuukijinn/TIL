# SQLインジェクション

---

## SQLインジェクションとは
SQL文中の穴埋めになっている部分に、悪意のある内容を入れることによって   
意図しない挙動をさせること

- データの漏洩
- データの改竄
- データの削除
- 認証回避

などを実現できる

---

### 仕組み

ログインフォームに脆弱性があると考える
```
SELECT * FROM uers WHERE username = `ユーザー入力` AND password = `ユーザー入力`
```

攻撃者が `ユーザー入力`の箇所に以下のような文字列を入力する

```
SELECT * FROM user WHERE username = `` OR `1` = `1` AND password `` OR `1` = `1`;
```
この場合、 `1=1`は常に真になるということから、攻撃者は認証を回避してログインできるようになる