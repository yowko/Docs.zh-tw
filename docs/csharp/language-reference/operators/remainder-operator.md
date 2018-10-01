---
title: '% 運算子 (C# 參考)'
ms.date: 09/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: 9cd2f7ad3856feb34667686979c942ecb21887c2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45645914"
---
# <a name="-operator-c-reference"></a>% 運算子 (C# 參考)

餘數運算子 `%` 會計算其第一個運算元除以第二個運算元之後的餘數。 使用者定義型別可以[多載](../keywords/operator.md) `%` 運算子。 當 `%` 多載時，[餘數指派運算子](remainder-assignment-operator.md) `%=`也會隱含多載。

所有數值類型皆支援餘數運算子。

## <a name="integer-remainder"></a>整數餘數
  
對整數運算元來說，`a % b` 的結果是 `a - (a / b) * b` 所產生的值。 非零餘數的正負號與第一個運算元的正負號相同，如下列範例所示：

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#1)]

## <a name="floating-point-remainder"></a>浮點數餘數

對於 [float](../keywords/float.md) 和 [double](../keywords/double.md) 運算元，有限 `x` 和 `y`的 `x % y` 結果是 `z` 值，像是

- 若 `z` 不是零，其正負號與 `x` 的正負號相同；
- `z` 的絕對值是由 `|x| - n * |y|` 產生的值，其中 `n` 為最大可能整數，小於或等於 `|x| / |y|`，而 `|x|`和 `|y|`則分別是 `x` 和 `y` 的絕對值。

如需在非有限運算元情況中 `%` 運算子的行為，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/index)的[餘數運算子](/dotnet/csharp/language-reference/language-specification/expressions#remainder-operator)一節。

> [!NOTE]
> 這項計算餘數的方法和用於整數運算元的方法類似，但不同於 IEEE 754。 如需符合 IEEE 754 的餘數運算，請使用 <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> 方法。

下列範例示範 `float` 和 `double` 運算元的餘數運算子行為：

[!code-csharp-interactive[float and double remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#2)]

請注意與浮點數類型有關的四捨五入錯誤。

針對 [decimal](../keywords/decimal.md) 運算元，餘數運算子 `%` 等於 <xref:System.Decimal?displayProperty=nameWithType> 類型的[餘數運算子](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>
- <xref:System.Math.DivRem%2A?displayProperty=nameWithType>
