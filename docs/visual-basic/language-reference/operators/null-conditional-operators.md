---
title: Null 條件運算子
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: bffbba859968e0a050397cd9e685c142f801798a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401468"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="50399-102">?.</span><span class="sxs-lookup"><span data-stu-id="50399-102">?.</span></span> <span data-ttu-id="50399-103">和?（） null 條件運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="50399-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="50399-104">`Nothing`在執行成員存取（）或索引（）作業之前，先測試左邊運算元的值是否為 null （）， `?.` `?()` `Nothing` 如果左運算元評估為， `Nothing` 則傳回。</span><span class="sxs-lookup"><span data-stu-id="50399-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="50399-105">請注意，在通常會傳回實數值型別的運算式中，null 條件運算子會傳回 <xref:System.Nullable%601> 。</span><span class="sxs-lookup"><span data-stu-id="50399-105">Note that in expressions that ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="50399-106">這些運算子可協助您撰寫較少的程式碼來處理 null 檢查，特別是當遞減至資料結構時。</span><span class="sxs-lookup"><span data-stu-id="50399-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="50399-107">例如：</span><span class="sxs-lookup"><span data-stu-id="50399-107">For example:</span></span>

```vb
' Nothing if customers is Nothing
Dim length As Integer? = customers?.Length

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()
```

<span data-ttu-id="50399-108">為了進行比較，這些運算式中第一個不含 null 條件運算子的替代程式碼為：</span><span class="sxs-lookup"><span data-stu-id="50399-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="50399-109">有時候，您需要在可能是 null 的物件上採取動作，這是根據該物件上的 Boolean 成員值（如 `IsAllowedFreeShipping` 下列範例中的布林屬性）：</span><span class="sxs-lookup"><span data-stu-id="50399-109">Sometimes you need to take an action on an object that may be null, based on the value of a Boolean member on that object (like the Boolean property `IsAllowedFreeShipping` in the following example):</span></span>

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
  ApplyFreeShippingToOrders(customer)
End If
```

<span data-ttu-id="50399-110">您可以使用 null 條件運算子來縮短您的程式碼，並避免手動檢查 null，如下所示：</span><span class="sxs-lookup"><span data-stu-id="50399-110">You can shorten your code and avoid manually checking for null by using the null-conditional operator as follows:</span></span>

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

<span data-ttu-id="50399-111">Null 條件運算子會執行最少運算。</span><span class="sxs-lookup"><span data-stu-id="50399-111">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="50399-112">如果條件式成員存取和索引作業鏈中的一項操作傳回，則會 `Nothing` 停止其餘的鏈執行。</span><span class="sxs-lookup"><span data-stu-id="50399-112">If one operation in a chain of conditional member access and index operations returns `Nothing`, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="50399-113">在下列範例中， `C(E)` 如果 `A` 、 `B` 或 `C` 評估為，則不會評估 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="50399-113">In the following example, `C(E)` isn't evaluated if `A`, `B`, or `C` evaluates to `Nothing`.</span></span>

```vb
A?.B?.C?(E)
```

<span data-ttu-id="50399-114">Null 條件式成員存取的另一個用法是以更少的程式碼，以安全線程的方式叫用委派。</span><span class="sxs-lookup"><span data-stu-id="50399-114">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="50399-115">下列範例會定義兩個類型： `NewsBroadcaster` 和 `NewsReceiver` 。</span><span class="sxs-lookup"><span data-stu-id="50399-115">The following example defines two types, a `NewsBroadcaster` and a `NewsReceiver`.</span></span> <span data-ttu-id="50399-116">由委派將新聞專案傳送給接收者 `NewsBroadcaster.SendNews` 。</span><span class="sxs-lookup"><span data-stu-id="50399-116">News items are sent to the receiver by the `NewsBroadcaster.SendNews` delegate.</span></span>

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

<span data-ttu-id="50399-117">如果調用清單中沒有任何元素，委派就會擲回 `SendNews` `SendNews` <xref:System.NullReferenceException> 。</span><span class="sxs-lookup"><span data-stu-id="50399-117">If there are no elements in the `SendNews` invocation list, the `SendNews` delegate throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="50399-118">在 null 條件運算子之前，如下所示的程式碼可確保委派調用清單不是 `Nothing` ：</span><span class="sxs-lookup"><span data-stu-id="50399-118">Before null conditional operators, code like the following ensured that the delegate invocation list was not `Nothing`:</span></span>

```vb
SendNews = SendNews.Combine({SendNews, client})
If SendNews IsNot Nothing Then
   SendNews("Just in...")
End If
```

<span data-ttu-id="50399-119">新方法則更簡單：</span><span class="sxs-lookup"><span data-stu-id="50399-119">The new way is much simpler:</span></span>

```vb
SendNews = SendNews.Combine({SendNews, client})
SendNews?.Invoke("Just in...")
```

<span data-ttu-id="50399-120">新的方法可以保障執行緒安全，因為編譯器產生的程式碼只會評估 `SendNews` 一次，並將結果保留在暫存變數中。</span><span class="sxs-lookup"><span data-stu-id="50399-120">The new way is thread-safe because the compiler generates code to evaluate `SendNews` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="50399-121">由於沒有 Null 條件式委派引動過程語法 `SendNews?(String)`，因此您必須明確呼叫 `Invoke` 方法。</span><span class="sxs-lookup"><span data-stu-id="50399-121">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `SendNews?(String)`.</span></span>

## <a name="see-also"></a><span data-ttu-id="50399-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50399-122">See also</span></span>

- [<span data-ttu-id="50399-123">運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50399-123">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="50399-124">Visual Basic 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="50399-124">Visual Basic Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="50399-125">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="50399-125">Visual Basic Language Reference</span></span>](../index.md)
