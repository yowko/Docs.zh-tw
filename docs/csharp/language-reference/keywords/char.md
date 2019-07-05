---
title: char 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 0b4f04a1ba6244373e36cc6a6188edabe33ec453
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424349"
---
# <a name="char-c-reference"></a>char (C# 參考)

`char` 關鍵字是用來宣告 .NET Framework 用來代表 Unicode 字元的 <xref:System.Char?displayProperty=nameWithType> 結構執行個體。 `Char` 物件的值是 16 位元數字 (序數) 值。

 Unicode 字元是用來代表世界各地的大部分書寫語言。

|類型|Range|大小|.NET 型別|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 到 U+FFFF|Unicode 16 位元字元|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>常值

`char` 類型的常數可以撰寫為字元常值、十六進位逸出序列或 Unicode 表示法。 您也可以轉型整數字元碼。 在下列範例中，四個 `char` 變數都會初始化成相同的字元 `X`：

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>轉換

`char` 可以隱含轉換為 [ushort](../builtin-types/integral-numeric-types.md)、[int](../builtin-types/integral-numeric-types.md)、[uint](../builtin-types/integral-numeric-types.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md)。 不過，沒有從其他類型到 `char` 類型的隱含轉換。

<xref:System.Char?displayProperty=nameWithType> 型別提供數種使用 `char` 值的靜態方法。

## <a name="c-language-specification"></a>C# 語言規格  

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[整數型別](~/_csharplang/spec/types.md#integral-types)。 語言規格是 C# 語法及用法的限定來源。

## <a name="see-also"></a>另請參閱

- <xref:System.Char>
- [C# 參考](../../../csharp/language-reference/index.md)
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)
- [整數型別](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [內建型別表](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)
- [字串](../../../csharp/programming-guide/strings/index.md)
