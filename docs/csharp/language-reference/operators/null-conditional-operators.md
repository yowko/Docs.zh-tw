---
title: "Null 條件運算子 (C# 和 Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c95b4079cf4e71c0ef9cd436ec230337f512229a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="babc4-102">Null 條件運算子 (C# 和 Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="babc4-102">Null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="babc4-103">在執行成員存取 (`?.`) 或對 (`?[`) 作業編製索引之前，可用來測試是否為 Null。</span><span class="sxs-lookup"><span data-stu-id="babc4-103">Used to test for null before performing a member access (`?.`) or index (`?[`) operation.</span></span>  <span data-ttu-id="babc4-104">這些運算子可協助您撰寫較少的程式碼來處理 Null 檢查，特別是遞減至資料結構。</span><span class="sxs-lookup"><span data-stu-id="babc4-104">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
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
  
 <span data-ttu-id="babc4-105">最後一個範例示範使用最少運算的 Null 條件運算子。</span><span class="sxs-lookup"><span data-stu-id="babc4-105">The last example demonstrates that the null-condition operators are short-circuiting.</span></span>  <span data-ttu-id="babc4-106">如果條件式成員存取和索引作業鏈結中的一項作業傳回 Null，則鏈結的其餘部分會停止執行。</span><span class="sxs-lookup"><span data-stu-id="babc4-106">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="babc4-107">運算式中優先順序較低的其他作業會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="babc4-107">Other operations with lower precedence in the expression continue.</span></span>  <span data-ttu-id="babc4-108">例如，下列程式碼中的 `E` 會在第二行執行，而且 `??` 和 `==` 運算會執行。</span><span class="sxs-lookup"><span data-stu-id="babc4-108">For example, `E` in the following executes in the second line, and the `??` and `==` operations execute.</span></span>  <span data-ttu-id="babc4-109">在第一行，當左邊評估為非 Null 時，`??` 最少運算和 `E` 不會執行。</span><span class="sxs-lookup"><span data-stu-id="babc4-109">In the first line, the `??` short circuits and `E` does not execute when the left side evaluates to non-null.</span></span>
  
```csharp
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
```

```vb
A?.B?.C?(0) ?? E  
A?.B?.C?(0) == E  
```  
  
 <span data-ttu-id="babc4-110">Null 條件成員存取的另一個用法是，使用更少的程式碼以執行緒安全的方式叫用委派。</span><span class="sxs-lookup"><span data-stu-id="babc4-110">Another use for the null-condition member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="babc4-111">舊方法需要如下的程式碼：</span><span class="sxs-lookup"><span data-stu-id="babc4-111">The old way requires code like the following:</span></span>  
  
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
  
 <span data-ttu-id="babc4-112">新方法則更簡單：</span><span class="sxs-lookup"><span data-stu-id="babc4-112">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 <span data-ttu-id="babc4-113">新的方法可以保障執行緒安全，因為編譯器產生的程式碼只會評估 `PropertyChanged` 一次，並將結果保留在暫存變數中。</span><span class="sxs-lookup"><span data-stu-id="babc4-113">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span>  
  
 <span data-ttu-id="babc4-114">由於沒有 Null 條件式委派引動過程語法 `PropertyChanged?(e)`，因此您必須明確呼叫 `Invoke` 方法。</span><span class="sxs-lookup"><span data-stu-id="babc4-114">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  <span data-ttu-id="babc4-115">有太多模稜兩可剖析的情況可能會導致無法呼叫。</span><span class="sxs-lookup"><span data-stu-id="babc4-115">There were too many ambiguous parsing situations to allow it.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="babc4-116">語言規格</span><span class="sxs-lookup"><span data-stu-id="babc4-116">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="babc4-117">如需詳細資訊，請參閱 [Visual Basic 語言參考](../../../visual-basic/language-reference/index.md)。</span><span class="sxs-lookup"><span data-stu-id="babc4-117">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="babc4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="babc4-118">See Also</span></span>  
 [<span data-ttu-id="babc4-119">??（null 聯合運算子）</span><span class="sxs-lookup"><span data-stu-id="babc4-119">?? (null-coalescing operator)</span></span>](null-conditional-operator.md)  
 [<span data-ttu-id="babc4-120">C# 參考</span><span class="sxs-lookup"><span data-stu-id="babc4-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="babc4-121">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="babc4-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="babc4-122">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="babc4-122">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
 [<span data-ttu-id="babc4-123">Visual Basic 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="babc4-123">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
