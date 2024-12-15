# enumについて

---

## switch文でのenum

switch文において、enumを使用できないという問題が発生

```
public enum ENUM {

AAA("00"),
BBB("10"),
CCC("20");

private final String code ;

ENUM (final String code) {
this.code = code;
}

public getCode() {
return code;
}
}
```

こういったenumにおいて、

```
String code = "20";

switch(code){
	case ENUM.AAA.getCode:
```

ってやったら、 `ENUM.AAA.getCode()`は定数にしてくれ！って言われた。

---

`switch`文で`String`型の値を評価しようとする場合、`case`には**コンパイル時に定数である必要がある**。

しかし、`ENUM.AAA.getCode()`は定数ではなく、メソッドの呼び出しの結果であるため、`case`に指定するとエラーになる。

### **原因**

- `case`ラベルに指定できるのは、コンパイル時に値が確定する定数のみ。
- `ENUM.AAA.getCode()`はコンパイル時に評価される定数ではなく、実行時に値が返されるため、`switch`文で直接使用できない。

---

### 直したver

```
public enum ENUM {

AAA("00"),
BBB("10"),
CCC("20");

private final String code ;

ENUM (final String code) {
this.code = code;
}

public getCode() {
return code;
}

public static ENUM convertEnum(String code) {
	for(ENUM enum: ENUM.values()) {
		if(Objects.equals(enum.getCode(),code)){
			return enum;
		}
	}
	return null;
}
```

```
String code = "20";

ENUM enumValue = ENUM.convertEnum(code);
if(enumValue != null) {
	switch(enumValue){
		case AAA:
		case BBB:
```

のような感じになる。

switchの引数と同じ型しかcaseに指定できないということから、 `ENUM.AAA` とせずとも、 `AAA` で十分。
switchの引数はnullを許容しないので、null回避の処理が必要。