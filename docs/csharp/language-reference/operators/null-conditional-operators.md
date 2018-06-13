---
title: Null 條件運算子 (C# 和 Visual Basic)
ms.date: 04/03/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- null-conditional operators [C#]
- null-conditional operators [Visual Basic]
- ?. operator [C#]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 28cf2633d74f047a751ffdad11f1e1db8328cd6f
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457796"
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="ec91b-102">?.</span><span class="sxs-lookup"><span data-stu-id="ec91b-102">?.</span></span> <span data-ttu-id="ec91b-103">and ?[] Null 條件運算子 (C# 和 Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec91b-103">and ?[] null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="ec91b-104">在執行成員存取 (`?.`) 或索引 (`?[]`) 運算之前，測試左運算元的值是否為 null；如果左運算元評估為 `null`，則傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="ec91b-104">Tests the value of the left-hand operand for null before performing a member access (`?.`) or index (`?[]`) operation; returns `null` if the left-hand operand evaluates to `null`.</span></span> 

<span data-ttu-id="ec91b-105">這些運算子可協助您撰寫較少的程式碼來處理 Null 檢查，特別是遞減至資料結構。</span><span class="sxs-lookup"><span data-stu-id="ec91b-105">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 <span data-ttu-id="ec91b-106">Null 條件運算子會執行最少運算。</span><span class="sxs-lookup"><span data-stu-id="ec91b-106">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="ec91b-107">如果條件式成員存取和索引作業鏈結中的一項作業傳回 Null，則鏈結的其餘部分會停止執行。</span><span class="sxs-lookup"><span data-stu-id="ec91b-107">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="ec91b-108">在下列範例中，如果 `A`、`B` 或 `C` 的計算結果為 Null，則不會執行 `E`。</span><span class="sxs-lookup"><span data-stu-id="ec91b-108">In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.</span></span>
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 <span data-ttu-id="ec91b-109">Null 條件成員存取的另一個用法是，使用更少的程式碼以執行緒安全的方式叫用委派。</span><span class="sxs-lookup"><span data-stu-id="ec91b-109">Another use for the null-conditional member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="ec91b-110">舊方法需要如下的程式碼：</span><span class="sxs-lookup"><span data-stu-id="ec91b-110">The old way requires code like the following:</span></span>  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 <span data-ttu-id="ec91b-111">新方法則更簡單：</span><span class="sxs-lookup"><span data-stu-id="ec91b-111">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(…)  
```  

```vb
PropertyChanged?.Invoke(…)
```  
  
 <span data-ttu-id="ec91b-112">新的方法可以保障執行緒安全，因為編譯器產生的程式碼只會評估 `PropertyChanged` 一次，並將結果保留在暫存變數中。</span><span class="sxs-lookup"><span data-stu-id="ec91b-112">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="ec91b-113">由於沒有 Null 條件式委派引動過程語法 `PropertyChanged?(e)`，因此您必須明確呼叫 `Invoke` 方法。</span><span class="sxs-lookup"><span data-stu-id="ec91b-113">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="ec91b-114">語言規格</span><span class="sxs-lookup"><span data-stu-id="ec91b-114">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="ec91b-115">如需詳細資訊，請參閱 [Visual Basic 語言參考](../../../visual-basic/language-reference/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ec91b-115">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec91b-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="ec91b-116">See Also</span></span>  
 [<span data-ttu-id="ec91b-117">?? (Null 聯合運算子)</span><span class="sxs-lookup"><span data-stu-id="ec91b-117">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)  
 [<span data-ttu-id="ec91b-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ec91b-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ec91b-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ec91b-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ec91b-120">Visual Basic 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="ec91b-120">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
