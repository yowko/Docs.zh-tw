---
title: stackalloc 運算子 - C# 參考
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9c9767e0c9945a9589d049fa7abba192cb928ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846244"
---
# <a name="stackalloc-operator-c-reference"></a>stackalloc 運算子 (C# 參考)

`stackalloc` 運算子會在堆疊上配置記憶體區塊。 在方法執行期間建立的堆疊配置的記憶體區塊，會在該方法傳回時自動被捨棄。 您無法明確釋放搭配 `stackalloc` 運算子配置的記憶體。 堆疊分配的區塊不受[垃圾回收](../../../standard/garbage-collection/index.md)，也不必用[`fixed`語句](../keywords/fixed-statement.md)固定。

您可以將 `stackalloc` 運算子的結果指派至下列其中一個類型的變數：

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

新配置記憶體的內容尚未被定義。 從 C# 7.3 開始，可以使用陣列初始化器語法來定義新分配的記憶體的內容。 下列範例示範進行該操作的數種方法：

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

在運算式`stackalloc T[E]`中`T`，必須是[非託管類型](../builtin-types/unmanaged-types.md)，並且必須`E`是[int](../builtin-types/integral-numeric-types.md)的運算式。

## <a name="security"></a>安全性

使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。 如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。

## <a name="c-language-specification"></a>C# 語言規格

有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[堆疊分配](~/_csharplang/spec/unsafe-code.md#stack-allocation)部分和[嵌套上下文中的`stackalloc`"許可](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md)"功能建議說明。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [指標相關運算子](pointer-related-operators.md)
- [指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [記憶體和跨距相關類型](../../../standard/memory-and-spans/index.md)
