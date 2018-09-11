---
title: 非同步程式設計模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET Framework
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e399a512d2bee636aec35e008c0632ce9c5fa781
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44249032"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="ed616-102">非同步程式設計模式</span><span class="sxs-lookup"><span data-stu-id="ed616-102">Asynchronous Programming Patterns</span></span>

<span data-ttu-id="ed616-103">.NET Framework 提供三種模式來執行非同步作業：</span><span class="sxs-lookup"><span data-stu-id="ed616-103">The .NET Framework provides three patterns for performing asynchronous operations:</span></span>  
  
- <span data-ttu-id="ed616-104">**非同步程式設計模型 (APM)** 模式 (也稱為 <xref:System.IAsyncResult> 模式)，其中非同步作業需要 `Begin` 和 `End` 方法 (例如，適用於非同步寫入作業的 `BeginWrite` 和 `EndWrite`)。</span><span class="sxs-lookup"><span data-stu-id="ed616-104">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), where asynchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` for asynchronous write operations).</span></span> <span data-ttu-id="ed616-105">在新的程式開發時，不建議使用此模式。</span><span class="sxs-lookup"><span data-stu-id="ed616-105">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="ed616-106">如需詳細資訊，請參閱[非同步程式設計模型 (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)。</span><span class="sxs-lookup"><span data-stu-id="ed616-106">For more information, see [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).</span></span>  
  
- <span data-ttu-id="ed616-107">**事件架構非同步模式 (EAP)**，需要具有 `Async` 尾碼的方法，並且要求一或多個事件、事件處理常式的委派類型，以及 `EventArg` 衍生類型。</span><span class="sxs-lookup"><span data-stu-id="ed616-107">**Event-based Asynchronous Pattern (EAP)**, which requires a method that has the `Async` suffix, and also requires one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="ed616-108">在 .NET Framework 2.0 中採用了 EAP。</span><span class="sxs-lookup"><span data-stu-id="ed616-108">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="ed616-109">在新的程式開發時，不建議使用它。</span><span class="sxs-lookup"><span data-stu-id="ed616-109">It is no longer recommended for new development.</span></span> <span data-ttu-id="ed616-110">如需詳細資訊，請參閱[事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)。</span><span class="sxs-lookup"><span data-stu-id="ed616-110">For more information, see [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
- <span data-ttu-id="ed616-111">**工作架構非同步模式 (TAP)**，使用單一方法來代表非同步作業的起始與完成。</span><span class="sxs-lookup"><span data-stu-id="ed616-111">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="ed616-112">在 .NET Framework 4 中使用了 TAP，且此為在 .NET Framework 中進行非同步程式設計時的建議方法。</span><span class="sxs-lookup"><span data-stu-id="ed616-112">TAP was introduced in the .NET Framework 4 and is the recommended approach to asynchronous programming in the .NET Framework.</span></span> <span data-ttu-id="ed616-113">C# 中的 [async](~/docs/csharp/language-reference/keywords/async.md) 和 [await](~/docs/csharp/language-reference/keywords/await.md) 關鍵字，以及 Visual Basic 語言中的 [Async](~/docs/visual-basic/language-reference/modifiers/async.md) 和 [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) 運算子，新增 TAP 的語言支援。</span><span class="sxs-lookup"><span data-stu-id="ed616-113">The [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) keywords in C# and the [Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic Language add language support for TAP.</span></span> <span data-ttu-id="ed616-114">如需詳細資訊，請參閱[以工作為基礎的非同步模式 (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)</span><span class="sxs-lookup"><span data-stu-id="ed616-114">For more information, see [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>  
  
## <a name="comparing-patterns"></a><span data-ttu-id="ed616-115">比較模式</span><span class="sxs-lookup"><span data-stu-id="ed616-115">Comparing Patterns</span></span>  

<span data-ttu-id="ed616-116">若要快速比較三個模式如何建立非同步作業的模型，請考慮 `Read` 方法，它會將指定的資料量讀取到所提供的緩衝區，並且在指定的位移處開始：</span><span class="sxs-lookup"><span data-stu-id="ed616-116">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
<span data-ttu-id="ed616-117">此方法的 APM 對應項會公開 `BeginRead` 和 `EndRead` 方法：</span><span class="sxs-lookup"><span data-stu-id="ed616-117">The APM counterpart of this method would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  
  
<span data-ttu-id="ed616-118">EAP 對應項會公開下列類型和成員的集合：</span><span class="sxs-lookup"><span data-stu-id="ed616-118">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="ed616-119">TAP 對應項會公開下列單一 `ReadAsync` 方法：</span><span class="sxs-lookup"><span data-stu-id="ed616-119">The TAP counterpart would expose the following single `ReadAsync` method:</span></span>  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
<span data-ttu-id="ed616-120">如需 TAP、APM 和 EAP 的完整討論，請參閱下節中所提供的連結。</span><span class="sxs-lookup"><span data-stu-id="ed616-120">For a comprehensive discussion of TAP, APM, and EAP, see the links provided in the next section.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="ed616-121">相關主題</span><span class="sxs-lookup"><span data-stu-id="ed616-121">Related topics</span></span>

| <span data-ttu-id="ed616-122">標題</span><span class="sxs-lookup"><span data-stu-id="ed616-122">Title</span></span> | <span data-ttu-id="ed616-123">描述</span><span class="sxs-lookup"><span data-stu-id="ed616-123">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="ed616-124">非同步程式設計模型 (APM)</span><span class="sxs-lookup"><span data-stu-id="ed616-124">Asynchronous Programming Model (APM)</span></span>](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | <span data-ttu-id="ed616-125">描述使用 <xref:System.IAsyncResult> 介面以提供非同步行為的傳統模型。</span><span class="sxs-lookup"><span data-stu-id="ed616-125">Describes the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="ed616-126">在新的程式開發時，不建議使用此模型。</span><span class="sxs-lookup"><span data-stu-id="ed616-126">This model is no longer recommended for new development.</span></span> |
| [<span data-ttu-id="ed616-127">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="ed616-127">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | <span data-ttu-id="ed616-128">描述提供非同步行為的事件架構舊版模型。</span><span class="sxs-lookup"><span data-stu-id="ed616-128">Describes the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="ed616-129">在新的程式開發時，不建議使用此模型。</span><span class="sxs-lookup"><span data-stu-id="ed616-129">This model is no longer recommended for new development.</span></span> |
| [<span data-ttu-id="ed616-130">工作式非同步模式 (TAP)</span><span class="sxs-lookup"><span data-stu-id="ed616-130">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | <span data-ttu-id="ed616-131">說明新的非同步模式，其根據 <xref:System.Threading.Tasks> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ed616-131">Describes the new asynchronous pattern based on the <xref:System.Threading.Tasks> namespace.</span></span> <span data-ttu-id="ed616-132">這個模型是在 .NET Framework 4 和更新版本中進行非同步程式設計的建議方法。</span><span class="sxs-lookup"><span data-stu-id="ed616-132">This model is the recommended approach to asynchronous programming in the .NET Framework 4 and later versions.</span></span> |

## <a name="see-also"></a><span data-ttu-id="ed616-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed616-133">See also</span></span>

- [<span data-ttu-id="ed616-134">C# 中的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="ed616-134">Asynchronous programming in C#</span></span>](~/docs/csharp/async.md)   
- [<span data-ttu-id="ed616-135">F# 中的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="ed616-135">Async Programming in F#</span></span>](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
- [<span data-ttu-id="ed616-136">使用 Async 和 Await 進行非同步程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed616-136">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/concepts/async/index.md)
