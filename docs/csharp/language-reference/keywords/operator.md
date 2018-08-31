---
title: operator 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: c3bfada235993670bf158fe9803a09707b2b3251
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929868"
---
# <a name="operator-c-reference"></a>operator (C# 參考)

使用 `operator` 關鍵字多載內建運算子，或在類別或結構宣告中提供使用者定義的轉換。

## <a name="example"></a>範例

以下是極簡化的分數類別。 它會多載 `+` 和 `*` 運算子，以執行分數的加法和乘法，也提供將 `Fraction` 類型轉換成 `double` 類型的轉換運算子。

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [implicit](implicit.md)
- [explicit](explicit.md)
- [如何：在結構之間實作使用者定義的轉換](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
