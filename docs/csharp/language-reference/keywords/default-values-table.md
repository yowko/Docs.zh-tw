---
title: 預設值表 - C# 參考
ms.custom: seodec18
description: 了解 C# 型別的預設值是什麼。
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 23fba8269670156000cb68b3aa07ae7c770eada1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627737"
---
# <a name="default-values-table-c-reference"></a>預設值表 (C# 參考)

下列表格顯示 C# 型別的預設值：

|類型|預設值|
|---------|------------------|
|任何參考類型|`null`|
|任何[內建整數數值型別](../builtin-types/integral-numeric-types.md)|0 (零)|
|任何[內建浮點數值型別](../builtin-types/floating-point-numeric-types.md)|0 (零)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'` (U+0000)|
|[enum](enum.md)|這個值是由運算式 `(E)0` 所產生，其中 `E` 是列舉識別碼。|
|[struct](struct.md)|這個值是藉由將所有實值型別欄位設定為其預設值，並將所有參考型別欄位設定為 `null` 所產生。|
|任何[可為 Null 的值型別](../../programming-guide/nullable-types/index.md)|<xref:System.Nullable%601.HasValue%2A> 屬性是 `false` 且未定義 <xref:System.Nullable%601.Value%2A> 屬性的執行個體。 該預設值也稱為可為 Null 值型別的 *null* 值。|

使用[預設值運算式](../../programming-guide/statements-expressions-operators/default-value-expressions.md)以產生型別的預設值，如下列範例所示：

```csharp
int a = default(int);
```

從 C# 7.1 開始，您可以使用 [`default` 常值](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference)　來以型別的預設值初始化變數：

```csharp
int a = default;
```

針對值型別，隱含無參數建構函式也會產生型別的預設值，如下列範例所示：

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [預設值](~/_csharplang/spec/variables.md#default-values)
- [預設建構函式](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 關鍵字](index.md)
- [內建型別表](built-in-types-table.md)
- [建構函式](../../programming-guide/classes-and-structs/constructors.md)
