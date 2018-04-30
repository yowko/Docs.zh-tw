---
title: 執行緒共用 (C#)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 98ae68c1-ace8-44b9-9317-8920ac9ef2b6
caps.latest.revision: 5
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 56fba1197fe81e60e27f300ec43879569d0a9d48
ms.sourcegitcommit: 68b60d38043e50104ccc90c76f8599b1ffe18346
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="thread-pooling-c"></a><span data-ttu-id="bd5a6-102">執行緒共用 (C#)</span><span class="sxs-lookup"><span data-stu-id="bd5a6-102">Thread Pooling (C#)</span></span>
<span data-ttu-id="bd5a6-103">「執行緒集區」是可用來在背景執行數項工作的執行緒集合。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="bd5a6-104">(如需背景資訊，請參閱[執行緒處理 (C#)](../../../../csharp/programming-guide/concepts/threading/index.md))。這可讓主要執行緒非同步地執行其他工作。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-104">(See [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="bd5a6-105">執行緒集區通常運用於伺服器應用程式中。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="bd5a6-106">每個傳入要求都會指派給執行緒集區中的執行緒，因此可以非同步處理，而不需要輸入主要執行緒或延遲處理後續要求。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="bd5a6-107">集區中的執行緒完成其工作之後，會回到可在其中重複使用它的等待中執行緒佇列。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="bd5a6-108">這項重複使用可讓應用程式避免建立每個工作之新執行緒的成本。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="bd5a6-109">執行緒集區一般會有最大數目的執行緒。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="bd5a6-110">如果所有執行緒都忙碌中，則會將其他工作放在佇列中，直到執行緒變成可用時可以服務這些工作為止。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="bd5a6-111">您可以實作自己的執行緒集區，但透過 <xref:System.Threading.ThreadPool> 類別較容易使用 .NET Framework 所提供的執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="bd5a6-112">使用執行緒集區，您可以使用您要執行之程序的委派來呼叫 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> 方法，而 C# 會建立執行緒並執行您的程序。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> method with a delegate for the procedure you want to run, and C# creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="bd5a6-113">執行緒共用範例</span><span class="sxs-lookup"><span data-stu-id="bd5a6-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="bd5a6-114">下列範例示範如何使用執行緒共用來啟動數個工作。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
```csharp  
public void DoWork()  
{  
    // Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(SomeLongTask));  
    // Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(AnotherLongTask));  
}  
  
private void SomeLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
  
private void AnotherLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
```  
  
 <span data-ttu-id="bd5a6-115">執行緒共用的其中一個優點是您可以將狀態物件中的引數傳遞給工作程序。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="bd5a6-116">如果您要呼叫的程序需要多個引數，則可以將結構或類別執行個體轉換為 `Object` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="bd5a6-117">執行緒集區參數和傳回值</span><span class="sxs-lookup"><span data-stu-id="bd5a6-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="bd5a6-118">從執行緒集區執行緒中傳回值並不直接。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="bd5a6-119">不允許從函式呼叫中傳回值的標準方式，因為 `Sub` 程序是唯一可放入執行緒集區佇列中的程序類型。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="bd5a6-120">其中一種您可以提供參數和傳回值的方式是將參數、傳回值和方法包裝到包裝函式類別，如[多執行緒程序的參數和傳回值 (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md) 中所述。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="bd5a6-121">提供參數和傳回值的較簡單方式是使用 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> 方法的選擇性 `ByVal` 狀態物件變數。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-121">An easier way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="bd5a6-122">如果您使用此變數來傳遞類別執行個體的參考，則執行個體的成員可以透過執行緒集區執行緒進行修改，並當作傳回值。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="bd5a6-123">一開始，可能不明顯，但您可以修改以傳值方式傳遞的變數所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="bd5a6-124">因為物件參考是以傳值方式傳遞，所以您可以執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="bd5a6-125">當您變更物件參考所參考的物件成員時，變更會套用至實際類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="bd5a6-126">結構無法用來傳回狀態物件內的值。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="bd5a6-127">因為結構是實值型別，所以非同步處理程序所進行的變更不會變更原始結構的成員。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="bd5a6-128">使用結構，以在不需要傳回值時提供參數。</span><span class="sxs-lookup"><span data-stu-id="bd5a6-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd5a6-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="bd5a6-129">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="bd5a6-130">如何：使用執行緒集區 (C#)</span><span class="sxs-lookup"><span data-stu-id="bd5a6-130">How to: Use a Thread Pool (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [<span data-ttu-id="bd5a6-131">執行緒 (C#)</span><span class="sxs-lookup"><span data-stu-id="bd5a6-131">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="bd5a6-132">多執行緒應用程式 (C#)</span><span class="sxs-lookup"><span data-stu-id="bd5a6-132">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="bd5a6-133">執行緒同步處理 (C#)</span><span class="sxs-lookup"><span data-stu-id="bd5a6-133">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)
