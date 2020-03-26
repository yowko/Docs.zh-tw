---
title: 堆疊aoc運算式 - C# 引用
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 2e99ce8b1e44dfa040c1acac799a3a55b375bd91
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546597"
---
# <a name="stackalloc-expression-c-reference"></a>堆疊aoc運算式（C# 引用）

運算式`stackalloc`在堆疊上分配區塊。 在方法執行期間建立的堆疊配置的記憶體區塊，會在該方法傳回時自動被捨棄。 不能顯式釋放分配的`stackalloc`記憶體。 堆疊分配的區塊不受[垃圾回收](../../../standard/garbage-collection/index.md)，也不必用[`fixed`語句](../keywords/fixed-statement.md)固定。

可以將`stackalloc`運算式的結果分配給以下類型之一的變數：

- 從 C# 7.2 <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>或 開始，如以下示例所示：

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  當您將堆疊配置的記憶體區塊指派至 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 變數時，您不需要使用 [unsafe](../keywords/unsafe.md) 內容。

  當您處理那些類型時，您可以使用[條件式](conditional-operator.md)或指派運算式中的 `stackalloc` 運算式，如下列範例所示：

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  從 C# 8.0 開始，只要`stackalloc`允許 或<xref:System.Span%601><xref:System.ReadOnlySpan%601>變數，都可以在其他運算式中使用運算式，如下例所示：

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > 我們建議盡可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 類型來處理堆疊配置的記憶體。

- [指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)，如下列範例所示：

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  如先前的範例所示，您在使用指標類型時必須使用 `unsafe` 內容。

  在指標類型中，只能在區域變數聲明中使用`stackalloc`運算式來初始化變數。

堆疊上的可用記憶體量是有限的。 如果在堆疊上分配了過多的記憶體，則引發<xref:System.StackOverflowException>。 為此，請遵循以下規則：

- 限制使用 分配的`stackalloc`記憶體量：

  [!code-csharp[limit stackalloc](snippets/StackallocOperator.cs#LimitStackalloc)]

  由於堆疊上的可用記憶體量取決於執行代碼的環境，因此在定義實際限制值時要保守。

- 避免使用`stackalloc`內部迴圈。 將區塊分配到迴圈之外，並在迴圈中重用它。

新配置記憶體的內容尚未被定義。 應在使用前初始化它。 例如，可以使用將<xref:System.Span%601.Clear%2A?displayProperty=nameWithType>所有項都設置為 類型的`T`預設值的方法。

從 C# 7.3 開始，可以使用陣列初始化器語法來定義新分配的記憶體的內容。 下列範例示範進行該操作的數種方法：

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

在運算式`stackalloc T[E]`中`T`，必須是[非託管類型](../builtin-types/unmanaged-types.md)，並且必須`E`計算為非負[int](../builtin-types/integral-numeric-types.md)值。

## <a name="security"></a>安全性

使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。 如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。

## <a name="c-language-specification"></a>C# 語言規格

有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[堆疊分配](~/_csharplang/spec/unsafe-code.md#stack-allocation)部分和[嵌套上下文中的`stackalloc`"許可](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md)"功能建議說明。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [指標相關運算子](pointer-related-operators.md)
- [指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [記憶體與延伸相關類型](../../../standard/memory-and-spans/index.md)
- [堆疊的做和不做](https://vcsjones.dev/2020/02/24/stackalloc/)
