---
title: float 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
ms.openlocfilehash: 98f89ba3d79f7679b69ce10fd875b3caf69c5257
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932906"
---
# <a name="float-c-reference"></a>float (C# 參考)

`float` 關鍵字表示儲存 32 位元浮點值的簡單類型。 下表顯示 `float` 類型的精確度和大概範圍。

|類型|大概範圍|精確度|.NET 型別|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|±1.5 x 10<sup>−45</sup> 到 ±3.4 x 10<sup>38</sup>|7 位數|<xref:System.Single?displayProperty=nameWithType>|  

## <a name="literals"></a>常值

根據預設，指派運算子右邊的實數常值會視為 [double](double.md)。 因此，若要初始化 float 變數，請使用後置字元 `f` 或 `F`，如下列範例所示：

```csharp
float x = 3.5F;
```

如果您在上述宣告中未使用此後置字元，由於您嘗試將 [double](double.md) 值儲存至 `float` 變數，因此會收到編譯錯誤。

## <a name="conversions"></a>轉換

您可以在一個運算式中混合使用數值整數型別和浮點類型。 在此情況下，整數型別會轉換成浮點類型。 運算式的評估會根據下列規則來執行：

- 如果其中一個浮點數型別是 [double](double.md)，則運算式會評估為 [double](double.md) 或 [bool](bool.md) (在關聯或相等比較中)。

- 若在運算式中沒有 [double](double.md) 型別，則運算式會評估為 `float` 或 [bool](bool.md) (在關聯或相等比較中)。

浮點運算式可以包含下列值的集合：

- 正零和負零

- 正無限大和負無限大

- 非數字值 (NaN)

- 非零值的有限集合

如需這些值的詳細資訊，請參閱 [IEEE](http://www.ieee.org) 網站上的 IEEE Standard for Binary Floating-Point Arithmetic。

## <a name="example"></a>範例

在下列範例中，會將一個 [int](int.md)、[short](short.md) 和 `float` 加入數學運算式，以產生 `float` 結果 (請記住，`float` 是 <xref:System.Single?displayProperty=nameWithType> 類型的別名。)請注意，運算式中沒有 [double](double.md)。

[!code-csharp[csrefKeywordsTypes#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#13)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- <xref:System.Single>  
- [C# 參考](../index.md)  
- [C# 程式設計指南](../../programming-guide/index.md)  
- [轉換和型別轉換](../../programming-guide/types/casting-and-type-conversions.md)  
- [C# 關鍵字](index.md)  
- [整數型別表](integral-types-table.md)  
- [內建型別表](built-in-types-table.md)  
- [隱含數值轉換表](implicit-numeric-conversions-table.md)  
- [明確數值轉換表](explicit-numeric-conversions-table.md)  