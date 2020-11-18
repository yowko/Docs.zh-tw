---
title: 非同步程式設計模式
description: 深入瞭解以工作為基礎的非同步模式 (將) 、以事件為基礎的非同步模式 (EAP) ，& .NET 中的 APM (非同步程式設計模型。
ms.date: 10/16/2018
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: bc0e37c060ab6375f943b4b50053e3046c05a556
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830333"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="8b564-103">非同步程式設計模式</span><span class="sxs-lookup"><span data-stu-id="8b564-103">Asynchronous programming patterns</span></span>

<span data-ttu-id="8b564-104">.NET 提供三種模式來執行非同步作業：</span><span class="sxs-lookup"><span data-stu-id="8b564-104">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="8b564-105">以工作為 **基礎的非同步模式 (點)**，它會使用單一方法來代表非同步作業的起始和完成。</span><span class="sxs-lookup"><span data-stu-id="8b564-105">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="8b564-106">點一下是在 .NET Framework 4 中引進。</span><span class="sxs-lookup"><span data-stu-id="8b564-106">TAP was introduced in .NET Framework 4.</span></span> <span data-ttu-id="8b564-107">**它是在 .NET 中進行非同步程式設計的建議方法。**</span><span class="sxs-lookup"><span data-stu-id="8b564-107">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="8b564-108">C# 中的 [async](../../csharp/language-reference/keywords/async.md) 與 [await](../../csharp/language-reference/operators/await.md) 關鍵字，以及 Visual Basic 中的 [Async](../../visual-basic/language-reference/modifiers/async.md) 與 [Await](../../visual-basic/language-reference/operators/await-operator.md) 運算子，都加入對 TAP 的語言支援。</span><span class="sxs-lookup"><span data-stu-id="8b564-108">The [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) keywords in C# and the [Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="8b564-109">如需詳細資訊，請參閱[以工作為基礎的非同步模式 (TAP)](task-based-asynchronous-pattern-tap.md)</span><span class="sxs-lookup"><span data-stu-id="8b564-109">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="8b564-110">**事件架構非同步模式 (EAP)**，這是用於提供非同步行為的事件架構傳統模型。</span><span class="sxs-lookup"><span data-stu-id="8b564-110">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="8b564-111">它需要一個具有 `Async` 尾碼的方法、一或多個事件，事件處理常式委派類型，以及 `EventArg` 衍生類型。</span><span class="sxs-lookup"><span data-stu-id="8b564-111">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="8b564-112">EAP 是在 .NET Framework 2.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="8b564-112">EAP was introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="8b564-113">在新的程式開發時，不再建議使用它。</span><span class="sxs-lookup"><span data-stu-id="8b564-113">It's no longer recommended for new development.</span></span> <span data-ttu-id="8b564-114">如需詳細資訊，請參閱[事件架構非同步模式 (EAP)](event-based-asynchronous-pattern-eap.md)。</span><span class="sxs-lookup"><span data-stu-id="8b564-114">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="8b564-115">**非同步程式設計模型 (APM)** 模式 (亦稱為 <xref:System.IAsyncResult> 模式)，它是使用 <xref:System.IAsyncResult> 介面來提供非同步行為的傳統模型。</span><span class="sxs-lookup"><span data-stu-id="8b564-115">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="8b564-116">在此模式中，同步作業需要 `Begin` 與 `End` 方法 (例如，`BeginWrite` 與 `EndWrite` 來實作非同步寫入作業)。</span><span class="sxs-lookup"><span data-stu-id="8b564-116">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="8b564-117">在新的程式開發時，不建議使用此模式。</span><span class="sxs-lookup"><span data-stu-id="8b564-117">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="8b564-118">如需詳細資訊，請參閱[非同步程式設計模型 (APM)](asynchronous-programming-model-apm.md)。</span><span class="sxs-lookup"><span data-stu-id="8b564-118">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="8b564-119">模式的比較</span><span class="sxs-lookup"><span data-stu-id="8b564-119">Comparison of patterns</span></span>

<span data-ttu-id="8b564-120">若要快速比較三個模式如何建立非同步作業的模型，請考慮 `Read` 方法，它會將指定的資料量讀取到所提供的緩衝區，並且在指定的位移處開始：</span><span class="sxs-lookup"><span data-stu-id="8b564-120">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="8b564-121">此方法的 TAP 對應項會公開下列單一 `ReadAsync` 方法：</span><span class="sxs-lookup"><span data-stu-id="8b564-121">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="8b564-122">EAP 對應項會公開下列類型和成員的集合：</span><span class="sxs-lookup"><span data-stu-id="8b564-122">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="8b564-123">APM 對應項會公開 `BeginRead` 與 `EndRead` 方法：</span><span class="sxs-lookup"><span data-stu-id="8b564-123">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="8b564-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="8b564-124">See also</span></span>

- [<span data-ttu-id="8b564-125">深入了解非同步</span><span class="sxs-lookup"><span data-stu-id="8b564-125">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="8b564-126">C# 中的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="8b564-126">Asynchronous programming in C#</span></span>](../../csharp/async.md)
- [<span data-ttu-id="8b564-127">F# 中的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="8b564-127">Async Programming in F#</span></span>](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="8b564-128">使用 Async 和 Await 進行非同步程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b564-128">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
