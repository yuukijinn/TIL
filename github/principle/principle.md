# Gitの原理について

---

### そもそもなぜ原理を学ぶのか
未経験からエンジニアになって７ヶ月目になる。  
研修や実際の業務の中で常にgitと関わってきた。  
その中で常に思っていたのが **gitが一番難しい！！！** ということだった。  

`add`や`commit`,`push`など一連のコマンドはそういうものだというパターンで使用することはできたが、
「間違えてcommitしてしまった」シチュエーションで何もわからなかった。  

実務に携われば携わるほどそういったシチュエーションに遭遇し、その度に苦労した。  
このままではダメだと思い、コマンドを調べたが、単純な暗記では応用が効かないということを学んだ。  

そもそもgitというものがどういうものなのかということを学ぶことで、1つ1つのイメージを持てるようになり、理解に繋がるだろうと考えた。

### そもそもGitとは

---

Git→ **バージョン管理ツール** 

昔は何か共通のプロジェクトなどを複数人で管理していた。  
たとえば1/1時点でのファイルを *ファイルv.1* とする。  
これをaさんとbさんの2人でそれぞれ別の機能を付け加えるという作業をする。  

いざ完成だ！とaさんが作成したファイル(*ファイルv.1.a*)を、*ファイルv.1*に上書き保存する。  
次にbさんが作業を終えたときにそれを *ファイルv.1*に上書きしようとする。  
このときに問題が発生！！！  
そのまま単純にファイルを上書きするとaさんが行った作業が消えてしまう...  
これを回避するには、bさんが上書きする前に、
aさんが作成した分のファイルをダウンロードし、自分の作業したフォルダにも入れて上書きするという面倒なことをする必要があった。  

これをどうにかできるのが**バージョン管理システム**

オリジナルとなるものを、それぞれの人が変更履歴も含んだ状態で自身の手元にコピーし、
それをそれぞれが変更していくことで、オリジナルとの差分を管理できるようにした。

リポジトリなどの話に関しては、今回の仕組み以前の問題と考えるため今回は記述しない。

### 簡潔に

---

Gitは  

- **Gitオブジェクト**の集まり
- これが**有向非巡回グラフ**に付箋を貼るような形で管理される

### Gitオブジェクト

---

gitオブジェクトには4つの種類がある

- blobオブジェクト
- treeオブジェクト
- commitオブジェクト
- tagオブジェクト

### blobオブジェクト
