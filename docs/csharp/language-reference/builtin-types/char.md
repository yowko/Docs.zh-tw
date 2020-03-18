---
title: 字元類型 - C# 引用
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: c4e29e6437edfe549b36a04a2050f63caa0d3d2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846518"
---
# <a name="char-c-reference"></a>字元（C# 參考）

類型`char`關鍵字是表示 Unicode UTF-16 字元的 .NET<xref:System.Char?displayProperty=nameWithType>結構類型的別名。

|類型|範圍|大小|.NET 類型|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 到 U+FFFF|16 位|<xref:System.Char?displayProperty=nameWithType>|

`char`類型的預設值為`\0`，即 U+0000。

[字串](reference-types.md#the-string-type)類型將文本表示為值序列`char`。

## <a name="literals"></a>常值

可以使用以下條件指定`char`值：

- 字元文本。
- Unicode 逸出序列，後面`\u`跟著字元代碼的四符號十六進位表示形式。
- 十六進位逸出序列，`\x`後跟字元代碼的十六進位表示形式。

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

如前面的示例所示，您還可以將字元代碼的值轉換為相應的`char`值。

> [!NOTE]
> 在 Unicode 逸出序列中，必須指定所有四個十六進位數位。 也就是說，`\u006A`是有效的逸出序列，而`\u06A`和`\u6A`無效。
>
> 在十六進位逸出序列的情況下，可以省略前置字元為零。 也就是說，`\x006A`和`\x06A``\x6A`逸出序列是有效的，並且對應于同一個字元。

## <a name="conversions"></a>轉換

類型`char`隱式可轉換為以下[積分](integral-numeric-types.md)`ushort`類型： 、 `int`、 `uint` `long`、`ulong`和 。 它還隱式可轉換為內置[浮點](floating-point-numeric-types.md)數數值型別：`float`和`double`。 `decimal` 它顯式可轉換為`sbyte`、`byte`和`short`積分類型。

沒有從其他類型的隱式轉換到類型`char`。 但是，任何[積分](integral-numeric-types.md)或[浮點](floating-point-numeric-types.md)數位類型都顯式轉換為`char`。

## <a name="c-language-specification"></a>C# 語言規格

有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的["積分類型"](~/_csharplang/spec/types.md#integral-types)部分。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [實值型別](value-types.md)
- [字串](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
