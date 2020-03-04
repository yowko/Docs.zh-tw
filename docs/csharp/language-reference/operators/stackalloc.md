---
title: stackalloc 運算子 - C# 參考
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: b2188bc94db42ab6d581c339f046ed81eb42d297
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238997"
---
# <a name="stackalloc-operator-c-reference"></a>stackalloc 運算子 (C# 參考)

`stackalloc` 運算子會在堆疊上配置記憶體區塊。 在方法執行期間建立的堆疊配置的記憶體區塊，會在該方法傳回時自動被捨棄。 您無法明確釋放搭配 `stackalloc` 運算子配置的記憶體。 堆疊配置的記憶體區塊不受[垃圾收集](../../../standard/garbage-collection/index.md)，也不需要使用[`fixed` 語句](../keywords/fixed-statement.md)來釘選。

您可以將 `stackalloc` 運算子的結果指派至下列其中一個類型的變數：

- 從C# 7.2 開始，<xref:System.Span%601?displayProperty=nameWithType> 或 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>，如下列範例所示：

  [!code-csharp[stackalloc span](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  當您將堆疊配置的記憶體區塊指派至 [ 或 ](../keywords/unsafe.md) 變數時，您不需要使用 <xref:System.Span%601>unsafe<xref:System.ReadOnlySpan%601> 內容。

  當您處理那些類型時，您可以使用`stackalloc`條件式[或指派運算式中的 ](conditional-operator.md) 運算式，如下列範例所示：

  [!code-csharp[stackalloc expression](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  從C# 8.0 開始，只要允許 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 變數，您就可以在其他運算式內使用 `stackalloc` 運算式，如下列範例所示：

  [!code-csharp[stackalloc in nested expressions](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > 我們建議盡可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 類型來處理堆疊配置的記憶體。

- [指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)，如下列範例所示：

  [!code-csharp[stackalloc pointer](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  如先前的範例所示，您在使用指標類型時必須使用 `unsafe` 內容。

  在指標類型的情況下，您只能使用區域變數宣告中的 `stackalloc` 運算式來初始化變數。

新配置記憶體的內容尚未被定義。 從C# 7.3 開始，您可以使用陣列初始化運算式語法來定義新配置之記憶體的內容。 下列範例示範進行該操作的數種方法：

[!code-csharp[stackalloc initialization](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

在 expression `stackalloc T[E]`中，`T` 必須是[非受控型](../builtin-types/unmanaged-types.md)別，而且 `E` 必須是[int](../builtin-types/integral-numeric-types.md)類型的運算式。

## <a name="security"></a>安全性

使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。 如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[ C#語言規格](~/_csharplang/spec/introduction.md)的[堆疊配置](~/_csharplang/spec/unsafe-code.md#stack-allocation)一節和嵌套內容功能建議事項[中的允許 `stackalloc`](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) 。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [指標相關運算子](pointer-related-operators.md)
- [指標型別](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [記憶體與延伸相關類型](../../../standard/memory-and-spans/index.md)
