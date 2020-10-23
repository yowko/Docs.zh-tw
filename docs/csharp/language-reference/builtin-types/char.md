---
description: 瞭解 C 中的內建字元類型#
title: 'char 型別-c # 參考'
ms.date: 05/11/2020
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1cb40759b81a1fcedcf5962b57d79cf3a64df561
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471872"
---
# <a name="char-c-reference"></a>char (c # 參考) 

`char`Type 關鍵字是 <xref:System.Char?displayProperty=nameWithType> 代表 Unicode utf-16 字元之 .net 結構類型的別名。

|類型|範圍|大小|.NET 類型|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 到 U+FFFF|16位|<xref:System.Char?displayProperty=nameWithType>|

型別的預設值 `char` 為 `\0` ，也就是 U + 0000。

此 `char` 類型支援 [比較](../operators/comparison-operators.md)、 [相等](../operators/equality-operators.md)、 [遞增](../operators/arithmetic-operators.md#increment-operator-)和 [遞減](../operators/arithmetic-operators.md#decrement-operator---) 運算子。 此外，針對 `char` 運算元， [算術](../operators/arithmetic-operators.md) 和 [位邏輯](../operators/bitwise-and-shift-operators.md) 運算子會對對應的字元碼執行運算，並產生型別的結果 `int` 。

[字串](reference-types.md#the-string-type)類型將文字表示為一系列的 `char` 值。

## <a name="literals"></a>常值

您可以 `char` 使用下列內容指定值：

- 字元常值。
- Unicode escape 序列， `\u` 後面接著字元碼的四符號十六進位標記法。
- 十六進位的 escape 序列， `\x` 後面接著字元碼的十六進位標記法。

[!code-csharp-interactive[char literals](snippets/shared/CharType.cs#Literals)]

如先前的範例所示，您也可以將字元碼的值轉換成對應的 `char` 值。

> [!NOTE]
> 在 Unicode escape 序列的案例中，您必須指定全部四個十六進位數位。 也就是 `\u006A` 有效的 escape 序列，雖然 `\u06A` 和無效 `\u6A` 。
>
> 在十六進位 escape 序列的情況下，您可以省略前置零。 也就是說， `\x006A` 、 `\x06A` 和 `\x6A` escape 序列是有效的，而且會對應到相同的字元。

## <a name="conversions"></a>轉換

`char`類型可隱含轉換成下列[整數](integral-numeric-types.md)類資料類型： `ushort` 、 `int` 、 `uint` 、 `long` 和 `ulong` 。 它也可以隱含地轉換成內建的 [浮點數](floating-point-numeric-types.md) 類型： `float` 、 `double` 和 `decimal` 。 它可以明確地轉換為 `sbyte` 、 `byte` 和 `short` 整數類資料類型。

沒有從其他類型到類型的隱含轉換 `char` 。 不過，任何 [整數](integral-numeric-types.md) 或 [浮點數](floating-point-numeric-types.md) 型別都可以明確地轉換成 `char` 。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的[整數類資料類型](~/_csharplang/spec/types.md#integral-types)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [值類型](value-types.md)
- [字串](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [.NET 中的字元編碼](../../../standard/base-types/character-encoding-introduction.md)
