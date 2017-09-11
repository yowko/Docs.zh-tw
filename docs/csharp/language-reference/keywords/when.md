---
title: "when (C# 參考)"
ms.date: 2017-03-07
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- when_CSharpKeyword
- when
dev_langs:
- CSharp
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 9ad2eff6eb527f00ce23f463e811aa748def62d0
ms.openlocfilehash: c391c6de51d41577d61278f43d58fade5b7c139f
ms.contentlocale: zh-tw
ms.lasthandoff: 08/11/2017

---
 # <a name="when-c-reference"></a><span data-ttu-id="699e4-102">when (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="699e4-102">when (C# Reference)</span></span>

<span data-ttu-id="699e4-103">您可以使用 `when` 內容關鍵字，在兩個內容中指定篩選條件︰</span><span class="sxs-lookup"><span data-stu-id="699e4-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="699e4-104">在 [try/catch](try-catch.md) 或 [try/catch/finally](try-catch-finally.md) 區塊的 `catch` 陳述式中。</span><span class="sxs-lookup"><span data-stu-id="699e4-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="699e4-105">在 [switch](switch.md) 陳述式的 `case` 標籤中。</span><span class="sxs-lookup"><span data-stu-id="699e4-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="699e4-106">`catch` 陳述式中的 `when`</span><span class="sxs-lookup"><span data-stu-id="699e4-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="699e4-107">從 C# 6 開始，`When` 可以用於 `catch` 陳述式中，來指定必須符合才能執行特定例外狀況的處理常式的條件。</span><span class="sxs-lookup"><span data-stu-id="699e4-107">Starting with C# 6, `When` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="699e4-108">它的語法為：</span><span class="sxs-lookup"><span data-stu-id="699e4-108">Its syntax is:</span></span>

```csharp
catch ExceptionType [e] when (expr)
```
<span data-ttu-id="699e4-109">其中，*expr* 是可評估為布林值的運算式。</span><span class="sxs-lookup"><span data-stu-id="699e4-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="699e4-110">如果它傳回 `true`，則會執行例外狀況處理常式；如果 `false` 則否。</span><span class="sxs-lookup"><span data-stu-id="699e4-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span> 

<span data-ttu-id="699e4-111">下列範例使用 `when` 關鍵字，根據例外狀況訊息的文字，有條件地執行 @System.Net.HttpRequestException 的處理常式。</span><span class="sxs-lookup"><span data-stu-id="699e4-111">The following example uses the `when` keyword to conditionally execute handlers for an @System.Net.HttpRequestException depending on the text of the exception message.</span></span>

 <span data-ttu-id="699e4-112">[!code-cs[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]</span><span class="sxs-lookup"><span data-stu-id="699e4-112">[!code-cs[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]</span></span>  
  
## <a name="when-in-a-switch-statement"></a><span data-ttu-id="699e4-113">`switch` 陳述式中的 `when`</span><span class="sxs-lookup"><span data-stu-id="699e4-113">`when` in a `switch` statement</span></span>

<span data-ttu-id="699e4-114">從 7 開始，`case` 標籤不再需要互斥，而且 `case` 標籤在 `switch` 陳述式中的出現順序可以判斷要執行的 switch 區塊。</span><span class="sxs-lookup"><span data-stu-id="699e4-114">Starting with 7, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="699e4-115">`when` 關鍵字可以用來指定篩選條件，使其相關聯的 case 標籤只有在篩選條件也是為 true 時才為 true。</span><span class="sxs-lookup"><span data-stu-id="699e4-115">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="699e4-116">它的語法為：</span><span class="sxs-lookup"><span data-stu-id="699e4-116">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```
<span data-ttu-id="699e4-117">其中，*expr* 是與比對運算式進行比較的常數模式或類型模式，而 *when-condition* 是任何布林運算式。</span><span class="sxs-lookup"><span data-stu-id="699e4-117">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span> 

<span data-ttu-id="699e4-118">下列範例使用 `when` 關鍵字來測試是否有具有零區域的 `Shape` 物件，以及測試是否有具有大於零的區域的各種 `Shape` 物件。</span><span class="sxs-lookup"><span data-stu-id="699e4-118">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span> 

 <span data-ttu-id="699e4-119">[!code-cs[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="699e4-119">[!code-cs[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="699e4-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="699e4-120">See also</span></span> 
  [<span data-ttu-id="699e4-121">switch 陳述式</span><span class="sxs-lookup"><span data-stu-id="699e4-121">switch statement</span></span>](switch.md)  
  [<span data-ttu-id="699e4-122">try/catch 陳述式</span><span class="sxs-lookup"><span data-stu-id="699e4-122">try/catch statement</span></span>](try-catch.md)  
  [<span data-ttu-id="699e4-123">try/catch/finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="699e4-123">try/catch/finally statement</span></span>](try-catch-finally.md) 


