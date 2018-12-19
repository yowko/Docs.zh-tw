---
title: decimal 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
ms.openlocfilehash: f26d812d8f4da8fae73ebbaee15441cd88860d04
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239455"
---
# <a name="decimal-c-reference"></a>decimal (C# 參考)

`decimal` 關鍵字表示 128 位元的資料類型。 相較於其他浮點類型，`decimal` 類型的精確度較高且範圍較小，因此非常適合財務和金融計算。 下表顯示 `decimal` 類型的大概範圍和精確度。

|類型|大概範圍|精確度|.NET 型別|
|----------|-----------------------|---------------|-------------------------|
|`decimal`|±1.0 x 10<sup>-28</sup> 到 ±7.9228 x 10<sup>28</sup>|28-29 個有效數字|<xref:System.Decimal?displayProperty=nameWithType>|

`decimal` 的預設值為 0m。

## <a name="literals"></a>常值

如果要將數值實數常值視為 `decimal` 處理，請使用後置字元 m 或 M，例如：

```csharp
decimal myMoney = 300.5m;
```

如果沒有後置字元 m，會將數字視為 [double](../../../csharp/language-reference/keywords/double.md) 處理，因而產生編譯器錯誤。

## <a name="conversions"></a>轉換

整數類資料類型會隱含轉換成 `decimal`，而且結果會判斷值為 `decimal`。 因此，您可以使用整數常值來初始化 Decimal 變數，而不需要後置字元，如下所示：

```csharp
decimal myMoney = 300;
```

其他浮點類型和 `decimal` 類型之間沒有隱含轉換，因此，這兩種類型之間必須使用轉換進行轉換。 例如：

```csharp
decimal myMoney = 99.9m;
double x = (double)myMoney;
myMoney = (decimal)x;
```

您也可以在同一個運算式中混合使用 `decimal` 和數值整數類資料類型。 然而，未使用轉換就混合使用 `decimal` 與其他浮點類型會造成編譯錯誤。

如需隱含數值轉換的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。

如需明確數值轉換的詳細資訊，請參閱[明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)。

## <a name="formatting-decimal-output"></a>格式化 Decimal 輸出

您可以使用 `String.Format` 方法，或透過會呼叫 <xref:System.Console.Write%2A?displayProperty=nameWithType> 的 `String.Format()` 方法格式化結果。 貨幣格式是使用標準貨幣格式字串 "C" 或 "c" 所指定，如本文稍後的第二個範例所示。 如需 `String.Format` 方法的詳細資訊，請參閱 <xref:System.String.Format%2A?displayProperty=nameWithType>。

## <a name="example"></a>範例

下列範例會嘗試新增 [double](../../../csharp/language-reference/keywords/double.md) 和 `decimal` 變數，而造成編譯器錯誤。

```csharp
decimal dec = 0m;
double dub = 9;
// The following line causes an error that reads "Operator '+' cannot be applied to
// operands of type 'double' and 'decimal'"
Console.WriteLine(dec + dub);

// You can fix the error by using explicit casting of either operand.
Console.WriteLine(dec + (decimal)dub);
Console.WriteLine((double)dec + dub);
```

結果會是下列錯誤：

`Operator '+' cannot be applied to operands of type 'double' and 'decimal'`

在這個範例中，`decimal` 和 [int](../../../csharp/language-reference/keywords/int.md) 會在同一個運算式中混用。 結果會判斷值為 `decimal` 類型。

[!code-csharp[csrefKeywordsTypes#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#6)]

## <a name="example"></a>範例

在這個範例中，輸出是使用貨幣格式字串格式化。 您會發現，`x` 會捨入，因為小數位數超過 $0.99。 代表最大確切位數的變數 `y` 會以正確格式精確顯示。

[!code-csharp[csrefKeywordsTypes#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#7)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- <xref:System.Decimal>  
- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
- [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [內建型別表](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
- [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md)