---
title: Null 條件運算子 (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: b83435b8448b53eca63aac0519e9eed2f7dfa9f3
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348761"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="0b99f-102">?.</span><span class="sxs-lookup"><span data-stu-id="0b99f-102">?.</span></span> <span data-ttu-id="0b99f-103">和嗎？（） null 條件運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b99f-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="0b99f-104">測試的左運算元為 null 的值 (`Nothing`) 之前執行成員存取 (`?.`) 或索引 (`?()`) 作業; 會傳回`Nothing`如果左運算元評估為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="0b99f-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="0b99f-105">請注意，在正常情況下傳回實值類型的運算式中，null 條件運算子傳回<xref:System.Nullable%601>。</span><span class="sxs-lookup"><span data-stu-id="0b99f-105">Note that in expressions that ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="0b99f-106">這些運算子可協助您撰寫較少的程式碼來處理 null 檢查，尤其是遞減至資料結構。</span><span class="sxs-lookup"><span data-stu-id="0b99f-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="0b99f-107">例如: </span><span class="sxs-lookup"><span data-stu-id="0b99f-107">For example:</span></span>

```vb
' Nothing if customers is Nothing  
Dim length As Integer? = customers?.Length  

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()   
```

<span data-ttu-id="0b99f-108">相較之下，這些運算式沒有 null 條件運算子的第一個替代程式碼是：</span><span class="sxs-lookup"><span data-stu-id="0b99f-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="0b99f-109">Null 條件運算子會執行最少運算。</span><span class="sxs-lookup"><span data-stu-id="0b99f-109">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="0b99f-110">如果在條件式成員存取和索引作業鏈結中的一項作業會傳回`Nothing`，其餘的鏈結的執行會停止。</span><span class="sxs-lookup"><span data-stu-id="0b99f-110">If one operation in a chain of conditional member access and index operations returns `Nothing`, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="0b99f-111">在下列範例中，`C(E)`如果不評估`A`， `B`，或`C`評估為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="0b99f-111">In the following example, `C(E)` isn't evaluated if `A`, `B`, or `C` evaluates to `Nothing`.</span></span>

```vb
A?.B?.C?(E);
```

<span data-ttu-id="0b99f-112">Null 條件成員存取的另一個用途是要以更少的程式碼以執行緒安全的方式叫用委派。</span><span class="sxs-lookup"><span data-stu-id="0b99f-112">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="0b99f-113">下列範例會定義兩種類型，`NewsBroadcaster`和`NewsReceiver`。</span><span class="sxs-lookup"><span data-stu-id="0b99f-113">The following example defines two types, a `NewsBroadcaster` and a `NewsReceiver`.</span></span> <span data-ttu-id="0b99f-114">新聞項目會傳送至由接收者`NewsBroadcaster.SendNews`委派。</span><span class="sxs-lookup"><span data-stu-id="0b99f-114">News items are sent to the receiver by the `NewsBroadcaster.SendNews` delegate.</span></span>

```vb
Public Module NewsBroadcaster
   Dim SendNews As Action(Of String) 

   Public Sub Main()
      Dim rec As New NewsReceiver()
      Dim rec2 As New NewsReceiver()
      SendNews?.Invoke("Just in: A newsworthy item...")
   End Sub

   Public Sub Register(client As Action(Of String))
      SendNews = SendNews.Combine({SendNews, client})
   End Sub
End Module

Public Class NewsReceiver
   Public Sub New()
      NewsBroadcaster.Register(AddressOf Me.DisplayNews)
   End Sub

   Public Sub DisplayNews(newsItem As String)
      Console.WriteLine(newsItem)
   End Sub
End Class
```

<span data-ttu-id="0b99f-115">如果在沒有項目`SendNews`引動過程清單`SendNews`委派擲回<xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="0b99f-115">If there are no elements in the `SendNews` invocation list, the `SendNews` delegate throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="0b99f-116">Null 條件運算子之前機器碼，類似下列確保委派引動過程清單不是`Nothing`:</span><span class="sxs-lookup"><span data-stu-id="0b99f-116">Before null conditional operators, code like the following ensured that the delegate invocation list was not `Nothing`:</span></span>

```vb  
SendNews = SendNews.Combine({SendNews, client})  
If SendNews IsNot Nothing Then 
   SendNews("Just in...")
End If
```

<span data-ttu-id="0b99f-117">新方法則更簡單：</span><span class="sxs-lookup"><span data-stu-id="0b99f-117">The new way is much simpler:</span></span>  

```vb
SendNews = SendNews.Combine({SendNews, client})  
SendNews?.Invoke("Just in...")
```

<span data-ttu-id="0b99f-118">新的方法可以保障執行緒安全，因為編譯器產生的程式碼只會評估 `SendNews` 一次，並將結果保留在暫存變數中。</span><span class="sxs-lookup"><span data-stu-id="0b99f-118">The new way is thread-safe because the compiler generates code to evaluate `SendNews` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="0b99f-119">由於沒有 Null 條件式委派引動過程語法 `SendNews?(String)`，因此您必須明確呼叫 `Invoke` 方法。</span><span class="sxs-lookup"><span data-stu-id="0b99f-119">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `SendNews?(String)`.</span></span>  

## <a name="see-also"></a><span data-ttu-id="0b99f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b99f-120">See also</span></span>

- [<span data-ttu-id="0b99f-121">運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b99f-121">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="0b99f-122">Visual Basic 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="0b99f-122">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="0b99f-123">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="0b99f-123">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
