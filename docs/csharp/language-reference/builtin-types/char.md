---
title: 字元型態 - C# 參考
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: a07cae6e607bb6cda965240c669c655207632298
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739058"
---
# <a name="char-c-reference"></a>字元(C# 參考)

類型`char`關鍵字是表示 Unicode UTF-16 字<xref:System.Char?displayProperty=nameWithType>元的 .NET 結構類型的別名。

|類型|範圍|大小|.NET 類型|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 到 U+FFFF|16 位元|<xref:System.Char?displayProperty=nameWithType>|

`char`類型的預設值為`\0`,即 U+0000。

[字串](reference-types.md#the-string-type)型態將文字表示為值序列`char`。

## <a name="literals"></a>常值

可以使用以下條件指定`char`值:

- 字元文字。
- Unicode 轉義序列,`\u`後面 跟著字符代碼的四元號十六進位表示形式。
- 十六進位逸出序列,`\x`後跟字元代碼的十六進位表示形式。

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

如前面的範例所示,您還可以將字元代碼的值轉換為相應的`char`值。

> [!NOTE]
> 在 Unicode 轉義序列中,必須指定所有四個十六進位數位。 也就是說,`\u006A`是有效的轉義序列,`\u06A`而`\u6A`和無效。
>
> 在十六進位轉義序列的情況下,可以省略前導零。 也就是說,`\x006A``\x06A``\x6A`和 轉義序列是有效的,並且對應於同一個字元。

## <a name="conversions"></a>轉換

型`char`別隱式轉換為以下[的類型](integral-numeric-types.md)`ushort`: `int`、 `uint` `long``ulong`、 、 與 。 它還隱式可轉換為內置[浮點](floating-point-numeric-types.md)數值`float`類型`double`:`decimal`和 。 它顯式可轉換為`sbyte`、`byte``short`積分類型。

沒有從其他類型的隱式轉換到類型`char`。 但是,任何[積分](integral-numeric-types.md)或[浮點](floating-point-numeric-types.md)數位類型都顯式轉換`char`為 。

## <a name="c-language-specification"></a>C# 語言規格

有關詳細資訊,請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[「積分類型」](~/_csharplang/spec/types.md#integral-types)部分。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [值類型](value-types.md)
- [字串](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [.NET 中的字元編碼](../../../standard/base-types/character-encoding-introduction.md)
