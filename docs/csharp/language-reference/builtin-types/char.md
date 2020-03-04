---
title: char 類型- C#參考
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: a5aca12e4037d517c3bcfb403c990605a052d48f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239842"
---
# <a name="char-c-reference"></a>char （C#參考）

`char` 類型關鍵字是代表 Unicode UTF-16 字元之 .NET <xref:System.Char?displayProperty=nameWithType> 結構類型的別名。

|類型|範圍|大小|.NET 類型|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 到 U+FFFF|16位|<xref:System.Char?displayProperty=nameWithType>|

`char` 類型的預設值為 `\0`，也就是 U + 0000。

[字串](reference-types.md#the-string-type)類型以 `char` 值序列的形式來表示文字。

## <a name="literals"></a>常值

您可以使用指定 `char` 值：

- 字元常值。
- Unicode 逸出序列，`\u` 後面接著字元碼的四符號十六進位標記法。
- 十六進位的逸出序列，`\x` 後面接著字元碼的十六進位標記法。

[!code-csharp-interactive[char literals](~/samples/snippets/csharp/language-reference/builtin-types/CharType.cs#Literals)]

如上述範例所示，您也可以將字元碼的值轉換成對應的 `char` 值。

> [!NOTE]
> 在 Unicode 逸出序列的情況下，您必須指定全部四個十六進位數位。 也就是說，`\u006A` 是有效的逸出序列，而 `\u06A` 和 `\u6A` 則無效。
>
> 在十六進位 escape 序列的情況下，您可以省略前置的零。 也就是說，`\x006A`、`\x06A`和 `\x6A` 的逸出序列都是有效的，而且會對應至相同的字元。

## <a name="conversions"></a>轉換

`char` 類型可以隱含地轉換成下列[整數](integral-numeric-types.md)類資料類型： `ushort`、`int`、`uint`、`long`和 `ulong`。 它也可以隱含地轉換成內建的[浮點](floating-point-numeric-types.md)數數值型別： `float`、`double`和 `decimal`。 它可以明確轉換成 `sbyte`、`byte`和 `short` 整數類資料類型。

沒有從其他類型到 `char` 類型的隱含轉換。 不過，任何[整數](integral-numeric-types.md)或[浮點數](floating-point-numeric-types.md)類型都可以明確地轉換成 `char`。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[ C#語言規格](~/_csharplang/spec/introduction.md)的[整數類資料類型](~/_csharplang/spec/types.md#integral-types)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [值類型](value-types.md)
- [字串](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
