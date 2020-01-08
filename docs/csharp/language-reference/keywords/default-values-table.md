---
title: 預設值表 - C# 參考
ms.custom: seodec18
description: 了解 C# 型別的預設值是什麼。
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 3604316b75bb3a6a4de39991899a837f64e547d2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345491"
---
# <a name="default-values-table-c-reference"></a>預設值表 (C# 參考)

下列表格顯示 C# 型別的預設值：

|類型|預設值|
|---------|------------------|
|任何參考類型|`null`|
|任何[內建整數數值型別](../builtin-types/integral-numeric-types.md)|0 (零)|
|任何[內建浮點數值型別](../builtin-types/floating-point-numeric-types.md)|0 (零)|
|[bool](../builtin-types/bool.md)|`false`|
|[char](../builtin-types/char.md)|`'\0'` (U+0000)|
|[enum](../builtin-types/enum.md)|這個值是由運算式 `(E)0` 所產生，其中 `E` 是列舉識別碼。|
|[struct](struct.md)|這個值是藉由將所有實值型別欄位設定為其預設值，並將所有參考型別欄位設定為 `null` 所產生。|
|任何[可為 Null 的值型別](../builtin-types/nullable-value-types.md)|<xref:System.Nullable%601.HasValue%2A> 屬性是 `false` 且未定義 <xref:System.Nullable%601.Value%2A> 屬性的執行個體。 該預設值也稱為可為 null 的實數值型別的*null*值。|

使用[預設運算子](../operators/default.md)產生型別的預設值，如下列範例所示：

```csharp
int a = default(int);
```

從 C# 7.1 開始，您可以使用 [`default` 常值](../operators/default.md#default-literal)　來以型別的預設值初始化變數：

```csharp
int a = default;
```

針對值型別，隱含無參數建構函式也會產生型別的預設值，如下列範例所示：

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

在執行時間，如果 <xref:System.Type?displayProperty=nameWithType> 實例代表實值型別，您可以使用 <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> 方法來叫用無參數的函式，以取得型別的預設值。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [預設值](~/_csharplang/spec/variables.md#default-values)
- [預設建構函式](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [C# 關鍵字](index.md)
- [內建型別表](built-in-types-table.md)
- [建構函式](../../programming-guide/classes-and-structs/constructors.md)
