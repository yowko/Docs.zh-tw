---
title: stackalloc 運算子 - C# 參考
ms.custom: seodec18
ms.date: 06/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: f211acaa8c47ab42a1f7f06cff6c35570cd22b75
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433833"
---
# <a name="stackalloc-operator-c-reference"></a>stackalloc 運算子 (C# 參考)

`stackalloc` 運算子會在堆疊上配置記憶體區塊。 在方法執行期間建立的堆疊配置的記憶體區塊，會在該方法傳回時自動被捨棄。 您無法明確釋放搭配 `stackalloc` 運算子配置的記憶體。 堆疊配置的記憶體區塊不會被[記憶體回收](../../../standard/garbage-collection/index.md)，且不需要以 [`fixed` 陳述式](../keywords/fixed-statement.md)固定。

在運算式 `stackalloc T[E]` 中，`T` 必須是 [ unmanaged 型別](../builtin-types/unmanaged-types.md)，且 `E` 必須是 `int` 型別的運算式。

您可以將 `stackalloc` 運算子的結果指派至下列其中一個類型的變數：

- <xref:System.Span%601?displayProperty=nameWithType> 或 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> (從 C# 7.2 開始)，如下列範例所示：

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  當您將堆疊配置的記憶體區塊指派至 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 變數時，您不需要使用 [unsafe](../keywords/unsafe.md) 內容。

  當您處理那些類型時，您可以使用[條件式](conditional-operator.md)或指派運算式中的 `stackalloc` 運算式，如下列範例所示：

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  > [!NOTE]
  > 我們建議盡可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 類型來處理堆疊配置的記憶體。

- [指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)，如下列範例所示：

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  如先前的範例所示，您在使用指標類型時必須使用 `unsafe` 內容。

新配置記憶體的內容尚未被定義。 從 C# 7.3 開始，您可以使用陣列初始設定式語法來定義新配置記憶體的內容。 下列範例示範進行該操作的數種方法：

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a>安全性

使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。 如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[堆疊配置](~/_csharplang/spec/unsafe-code.md#stack-allocation)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [指標相關運算子](pointer-related-operators.md)
- [指標型別](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [記憶體與延伸相關類型](../../../standard/memory-and-spans/index.md)
