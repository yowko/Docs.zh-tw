---
title: char 關鍵字- C#參考
ms.custom: seodec18
ms.date: 10/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1b9f8d1bb205a6cbfe521830a11bd8878ccde991
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771793"
---
# <a name="char-c-reference"></a>char （C#參考）

@No__t_0 類型關鍵字是代表 Unicode UTF-16 字元之 .NET <xref:System.Char?displayProperty=nameWithType> 結構類型的別名：

|輸入|Range|大小|.NET 型別|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 到 U+FFFF|16位|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>常值

`char` 類型的常數可以撰寫為字元常值、十六進位逸出序列或 Unicode 表示法。 您也可以將整數位符程式碼轉換成對應的 `char` 值。 在下列範例中，`char` 陣列的四個元素會使用相同的字元 `X` 進行初始化：

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>轉換

@No__t_0 類型可以隱含地轉換成下列[整數](../builtin-types/integral-numeric-types.md)類資料類型： `ushort`、`int`、`uint`、`long` 和 `ulong`。 它也可以隱含地轉換成內建的[浮點](../builtin-types/floating-point-numeric-types.md)數數值型別： `float`、`double` 和 `decimal`。 它可以明確轉換成 `sbyte`、`byte` 和 `short` 整數類資料類型。

沒有從其他類型到 `char` 類型的隱含轉換。 不過，任何[整數](../builtin-types/integral-numeric-types.md)或[浮點數](../builtin-types/floating-point-numeric-types.md)類型都可以明確地轉換成 `char`。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[ C#語言規格](~/_csharplang/spec/introduction.md)的[整數類資料類型](~/_csharplang/spec/types.md#integral-types)一節。

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [C# 關鍵字](./index.md)
- [內建型別表](./built-in-types-table.md)
- [字串](../../programming-guide/strings/index.md)
- <xref:System.Char?displayProperty=nameWithType>
