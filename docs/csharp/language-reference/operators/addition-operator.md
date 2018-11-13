---
title: + 運算子 (C# 參考)
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 27ea47d698b20f112880750ec0bc931f1917f142
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "50192293"
---
# <a name="-operator-c-reference"></a>+ 運算子 (C# 參考)

`+` 運算子支援兩種形式：一元加號運算子或二元加法運算子。

## <a name="unary-plus-operator"></a>一元加號運算子

一元 `+` 運算子會傳回其運算元的值。 所有數值型別都支援。

## <a name="numeric-addition"></a>數值加法

針對數值型別，`+` 運算子會計算其運算元的和：

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

## <a name="string-concatenation"></a>字串串連

當其中一或兩個運算元的型別為 [string](../keywords/string.md) 時，`+` 運算子會串連其運算元的字串表示：

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

從 C# 6 開始，[字串插補](../tokens/interpolated.md)提供更便利的方式進行字串格式設定：

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>委派組合

針對 [delegate](../keywords/delegate.md) 型別，`+` 運算子會傳回新的委派執行個體，(當叫用時) 它會叫用第一個運算元，然後再叫用第二個運算元。 如果其中任一個運算元為 `null`，則 `+` 運算子會傳回另一個運算元的值 (也有可能是 `null`)。 下列範例顯示委派如何與 `+` 運算子結合：

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

如需委派型別的詳細資訊，請參閱[委派](../../programming-guide/delegates/index.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義的型別可以[多載](../keywords/operator.md)一元與二元 `+` 運算子。 多載二元 `+` 運算子時，[加法指派運算子](addition-assignment-operator.md) `+=` 也會隱含地多載。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[一元加號運算子](~/_csharplang/spec/expressions.md#unary-plus-operator)與[加法運算子](~/_csharplang/spec/expressions.md#addition-operator)小節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [字串內插補點](../tokens/interpolated.md)
- [如何：串連多個字串](../../how-to/concatenate-multiple-strings.md)
- [委派](../../programming-guide/delegates/index.md)
- [Checked 與 Unchecked](../keywords/checked-and-unchecked.md)
