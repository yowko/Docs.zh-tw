---
title: C# 類型的預設值 - C# 引用
description: 瞭解 C# 類型的預設值，如布林、字元、int、浮點、雙精度值等。
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 5e34d291ec15c738f3bc9409df321ede454b6710
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507252"
---
# <a name="default-values-of-c-types-c-reference"></a>C# 類型的預設值（C# 引用）

下列表格顯示 C# 型別的預設值：

|類型|預設值|
|---------|------------------|
|任何參考類型|`null`|
|任何[內建整數數值型別](integral-numeric-types.md)|0 (零)|
|任何[內建浮點數值型別](floating-point-numeric-types.md)|0 (零)|
|[Bool](bool.md)|`false`|
|[字元](char.md)|`'\0'` (U+0000)|
|[枚舉](enum.md)|這個值是由運算式 `(E)0` 所產生，其中 `E` 是列舉識別碼。|
|[struct](struct.md)|這個值是藉由將所有實值型別欄位設定為其預設值，並將所有參考型別欄位設定為 `null` 所產生。|
|任何[可為 Null 的值型別](nullable-value-types.md)|<xref:System.Nullable%601.HasValue%2A> 屬性是 `false` 且未定義 <xref:System.Nullable%601.Value%2A> 屬性的執行個體。 該預設值也稱為空數值型別的*空*值。|

使用[`default`運算子](../operators/default.md#default-operator)組建類型的預設值，如以下示例所示：

```csharp
int a = default(int);
```

從 C# 7.1 開始，可以使用[`default`文本](../operators/default.md#default-literal)初始化具有其類型的預設值的變數：

```csharp
int a = default;
```

針對值型別，隱含無參數建構函式也會產生型別的預設值，如下列範例所示：

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

在運行時，如果<xref:System.Type?displayProperty=nameWithType>實例表示數值型別，則可以使用<xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType>方法調用無參數建構函式以獲取類型的預設值。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [預設值](~/_csharplang/spec/variables.md#default-values)
- [預設建構函式](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [建構函式](../../programming-guide/classes-and-structs/constructors.md)
