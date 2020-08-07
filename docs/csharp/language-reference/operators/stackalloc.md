---
title: 'stackalloc 運算式-c # 參考'
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 4f20f3262b77cc2fe16480e53d13960e68d230b5
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916675"
---
# <a name="stackalloc-expression-c-reference"></a>stackalloc expression (c # 參考) 

運算式會配置 `stackalloc` 堆疊上的記憶體區塊。 在方法執行期間建立的堆疊配置的記憶體區塊，會在該方法傳回時自動被捨棄。 您無法明確釋放以所配置的記憶體 `stackalloc` 。 堆疊配置的記憶體區塊不受[垃圾收集](../../../standard/garbage-collection/index.md)，也不需要使用[ `fixed` 語句](../keywords/fixed-statement.md)來釘選。

您可以將運算式的結果指派 `stackalloc` 給下列其中一種類型的變數：

- 從 c # 7.2、 <xref:System.Span%601?displayProperty=nameWithType> 或開始， <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> 如下列範例所示：

  [!code-csharp[stackalloc span](snippets/shared/StackallocOperator.cs#AssignToSpan)]

  當您將堆疊配置的記憶體區塊指派至 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 變數時，您不需要使用 [unsafe](../keywords/unsafe.md) 內容。

  當您處理那些類型時，您可以使用[條件式](conditional-operator.md)或指派運算式中的 `stackalloc` 運算式，如下列範例所示：

  [!code-csharp[stackalloc expression](snippets/shared/StackallocOperator.cs#AsExpression)]

  從 c # 8.0 開始， `stackalloc` 只要允許或變數，您就可以在其他運算式內使用運算式 <xref:System.Span%601> <xref:System.ReadOnlySpan%601> ，如下列範例所示：

  [!code-csharp[stackalloc in nested expressions](snippets/shared/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > 我們建議盡可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 類型來處理堆疊配置的記憶體。

- [指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)，如下列範例所示：

  [!code-csharp[stackalloc pointer](snippets/shared/StackallocOperator.cs#AssignToPointer)]

  如先前的範例所示，您在使用指標類型時必須使用 `unsafe` 內容。

  在指標類型的情況下，您只能使用 `stackalloc` 區域變數宣告中的運算式來初始化變數。

堆疊上可用的記憶體數量有限。 如果您在堆疊上配置太多記憶體， <xref:System.StackOverflowException> 就會擲回。 若要避免這種情況，請遵循下列規則：

- 限制您配置的記憶體數量 `stackalloc` ：

  [!code-csharp[limit stackalloc](snippets/shared/StackallocOperator.cs#LimitStackalloc)]

  因為堆疊上可用的記憶體數量取決於執行程式碼的環境，所以當您定義實際的限制值時請保守。

- 避免 `stackalloc` 在迴圈內使用。 在迴圈外配置記憶體區塊，並在迴圈內重複使用它。

新配置記憶體的內容尚未被定義。 在使用之前，您應該先將它初始化。 例如，您可以使用 <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> 方法，將所有專案設定為類型的預設值 `T` 。

從 c # 7.3 開始，您可以使用陣列初始化運算式語法來定義新配置之記憶體的內容。 下列範例示範進行該操作的數種方法：

[!code-csharp[stackalloc initialization](snippets/shared/StackallocOperator.cs#StackallocInit)]

在 [運算式] 中 `stackalloc T[E]` ， `T` 必須是[非受控型](../builtin-types/unmanaged-types.md)別，而且 `E` 必須評估為非負[整數](../builtin-types/integral-numeric-types.md)值。

## <a name="security"></a>安全性

使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。 如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的[堆疊配置](~/_csharplang/spec/unsafe-code.md#stack-allocation)一節和在[nested 內容 `stackalloc` 中允許](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md)功能提案。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [指標相關運算子](pointer-related-operators.md)
- [指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [記憶體與延伸相關類型](../../../standard/memory-and-spans/index.md)
- [Stackalloc 的 Dos 和不應事項](https://vcsjones.dev/2020/02/24/stackalloc/)
