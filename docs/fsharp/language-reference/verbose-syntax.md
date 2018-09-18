---
title: 詳細語法 (F#)
description: '了解 F # 程式設計語言中的詳細資訊和輕量型語法之間的差異。'
ms.date: 05/16/2016
ms.openlocfilehash: b4f2354738da4692cb444e5e7dd9531d80d26664
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "45972315"
---
# <a name="verbose-syntax"></a>詳細語法

有可供在 F # 語言中的許多建構的兩種形式的語法：*詳細語法*並*輕量型語法*。 詳細的語法不常用，但優點是較不容易縮排。 輕量型語法較短，並使用縮排來表示的開頭和結尾的建構，而非其他關鍵字喜歡`begin`， `end`， `in`，依此類推。 預設語法是輕量型語法。 未啟用輕量型語法時，本主題將描述適用於 F # 建構語法。 永遠啟用詳細語法，因此即使您啟用輕量型語法時，您仍然可以使用詳細語法適用於某些建構。 您可以使用連線，停用輕量型語法`#light "off"`指示詞。

## <a name="table-of-constructs"></a>資料表的建構

下表顯示 F # 語言建構的輕量級和詳細語法在內容中沒有兩個形式之間的差異。 下表中角括弧 (&lt;&gt;) 括住使用者提供的語法元素。 文件以取得每個語言建構，這些建構內所使用之語法的詳細資訊，請參閱。

<table>
<tr>
<th>語言建構</th>
<th>輕量型語法</th>
<th>詳細語法</th>
</tr>
<tr>
<td>
複合運算式
</td>
<td>

```xml
<expression1>
<expression2>
```
</td><td>

```
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>


巢狀`let`繫結

</td><td>
```
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```
let f x =
    let a = 1 in
    let b = 2 in
    x + a + b
```

</td>
</tr>
<tr><td>
程式碼區塊
</td><td>

```
(
    <expression1>
    <expression2>
)
```

</td><td>

```
begin
    <expression1>;
    <expression2>;
end
```
</td>
</tr>
<tr><td>
`for...do`
</td><td>

```
for counter = start to finish do
    ...
```

</td><td>

```
for counter = start to finish do
    ...
done
```

</td>
</tr>
<tr><td>
`while...do`
</td><td>

```
while <condition> do
    ...
```

</td><td>

```
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```
for var in start .. finish do
    ...
```

</td><td>

```
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```
do
    ...
```

</td><td>

```
do
    ...
in
```

</td>
</tr>
<tr><td>記錄
</td><td>

```
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```
type <record-name> =
    {
        <field-declarations>
    }
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>Class - 類別
</td><td>
```
type <class-name>(<params>) = ... ```

</td><td>

```
type <class-name>(<params>) =
    class
        ...
    end
```
</td>
</tr>
<tr><td>結構</td><td>

```
[<StructAttribute>]
type <structure-name> =
    ...
```
</td><td>

```
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td>已區分聯集</td><td>

```
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```
</td><td>

```
type <union-name> =
    | ...
    | ...
    ...
    with
        <value-or-member-definitions>
    end    
```

</td>
</tr>
<tr><td>interface</td><td>

```
type <interface-name> =
    ...
```
</td><td>

```
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td>物件運算式</td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
    end
    <interface-implementations>
}
```

</td>
</tr>
<tr><td>介面實作</td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>類型擴充功能</td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>name</td><td>

```
module <module-name> =
    ...
```

</td><td>

```
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [編譯器指示詞](compiler-directives.md)
- [程式碼格式化方針](code-formatting-guidelines.md)
