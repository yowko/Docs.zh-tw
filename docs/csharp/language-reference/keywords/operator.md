---
title: operator 關鍵字 - C# 參考
ms.custom: seodec18
description: 了解如何多載內建 C# 運算子
ms.date: 08/27/2018
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: 47ce91c343092ac2f7555c1edf3418527776e131
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754769"
---
# <a name="operator-c-reference"></a>operator (C# 參考)

使用 `operator` 關鍵字多載內建運算子，或在類別或結構宣告中提供使用者定義的轉換。

若要在自訂類別或結構上多載運算子，您可以在對應類型中建立運算子宣告。 多載內建 C# 運算子的運算子宣告必須滿足下列規則：

- 它包含 `public` 和 `static` 修飾詞。
- 它包含 `operator X`，其中 `X` 是所要多載之運算子的名稱或符號。
- 一元運算子有一個參數，而二元運算子有兩個參數。 在各案例中，至少一個參數必須與宣告運算子的類別或結構擁有相同的類型。

如需如何定義轉換運算子的資訊，請參閱 [explicit](explicit.md) 和 [implicit](implicit.md) 關鍵字文章。

如需可多載的 C# 運算子概觀，請參閱[可多載的運算子](../../programming-guide/statements-expressions-operators/overloadable-operators.md)一文。

## <a name="example"></a>範例

下列範例定義 `Fraction` 類型，表示分數。 它會多載 `+` 和 `*` 運算子，以執行分數的加法和乘法，也提供將 `Fraction` 類型轉換成 `double` 類型的轉換運算子。

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [implicit](implicit.md)
- [explicit](explicit.md)
- [多載運算子](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [如何：在結構之間實作使用者定義的轉換](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
