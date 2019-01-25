---
title: Null 條件運算子 (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: d30d452a7c140a0c56529386b14ef3a3512df490
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722149"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="3429e-102">?.</span><span class="sxs-lookup"><span data-stu-id="3429e-102">?.</span></span> <span data-ttu-id="3429e-103">和嗎？（） null 條件運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3429e-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="3429e-104">測試的左運算元為 null 的值 (`Nothing`) 之前執行成員存取 (`?.`) 或索引 (`?()`) 作業; 會傳回`Nothing`如果左運算元評估為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="3429e-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="3429e-105">請注意，在通常會傳回實值型別運算式中，null 條件運算子傳回<xref:System.Nullable%601>。</span><span class="sxs-lookup"><span data-stu-id="3429e-105">Note that, in the expressions that would ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="3429e-106">這些運算子可協助您撰寫較少的程式碼來處理 null 檢查，尤其是遞減至資料結構。</span><span class="sxs-lookup"><span data-stu-id="3429e-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="3429e-107">例如: </span><span class="sxs-lookup"><span data-stu-id="3429e-107">For example:</span></span>

```vb
Dim length As Integer? = customers?.Length  ' Nothing if customers is Nothing  
Dim first As Customer = customers?(0)  ' Nothing if customers is Nothing  
Dim count As Integer? = customers?(0)?.Orders?.Count()  ' Nothing if customers, the first customer, or Orders is Nothing  
```

<span data-ttu-id="3429e-108">相較之下，這些運算式沒有 null 條件運算子的第一個替代程式碼是：</span><span class="sxs-lookup"><span data-stu-id="3429e-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="3429e-109">Null 條件運算子會執行最少運算。</span><span class="sxs-lookup"><span data-stu-id="3429e-109">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="3429e-110">如果在條件式成員存取和索引作業鏈結中的一項作業會傳回 Nothing，就會停止執行在鏈結的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="3429e-110">If one operation in a chain of conditional member access and index operations returns Nothing, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="3429e-111">在下列範例中，c （e） 不會評估如果`A`， `B`，或`C`是否評估為 Nothing。</span><span class="sxs-lookup"><span data-stu-id="3429e-111">In the following example, C(E) isn't evaluated if `A`, `B`, or `C` evaluates to Nothing.</span></span>

```vb
A?.B?.C?(E);
```

<span data-ttu-id="3429e-112">Null 條件成員存取的另一個用途是要以更少的程式碼以執行緒安全的方式叫用委派。</span><span class="sxs-lookup"><span data-stu-id="3429e-112">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="3429e-113">舊方法需要如下的程式碼：</span><span class="sxs-lookup"><span data-stu-id="3429e-113">The old way requires code like the following:</span></span>  

```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```

<span data-ttu-id="3429e-114">新方法則更簡單：</span><span class="sxs-lookup"><span data-stu-id="3429e-114">The new way is much simpler:</span></span>  

```vb
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="3429e-115">新的方法可以保障執行緒安全，因為編譯器產生的程式碼只會評估 `PropertyChanged` 一次，並將結果保留在暫存變數中。</span><span class="sxs-lookup"><span data-stu-id="3429e-115">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="3429e-116">由於沒有 Null 條件式委派引動過程語法 `PropertyChanged?(e)`，因此您必須明確呼叫 `Invoke` 方法。</span><span class="sxs-lookup"><span data-stu-id="3429e-116">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3429e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3429e-117">See also</span></span>

- [<span data-ttu-id="3429e-118">運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3429e-118">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="3429e-119">Visual Basic 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="3429e-119">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="3429e-120">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="3429e-120">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
