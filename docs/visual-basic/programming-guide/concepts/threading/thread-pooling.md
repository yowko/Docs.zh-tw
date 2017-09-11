---
title: "執行緒集區 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: eea7c94dffe525bb36c677bf3414f25ed0210074
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="thread-pooling-visual-basic"></a><span data-ttu-id="3e9cb-102">執行緒集區 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e9cb-102">Thread Pooling (Visual Basic)</span></span>
<span data-ttu-id="3e9cb-103">A*執行緒集區*是可用來在背景中執行幾項工作的執行緒的集合。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="3e9cb-104">(請參閱[執行緒 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)背景資訊。)這會使主要執行緒可以執行其他工作以非同步的方式。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-104">(See [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="3e9cb-105">執行緒集區通常會運用在伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="3e9cb-106">每個傳入要求被指派給一個執行緒在執行緒集區，以便可以以非同步方式處理要求，而不用中斷主要執行緒或延遲處理的後續要求。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="3e9cb-107">當執行緒集區中的完成其工作時，它會回到佇列等待執行緒可重複使用。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="3e9cb-108">這種重新使用可讓應用程式，以避免建立新的執行緒，每個工作的成本。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="3e9cb-109">執行緒集區通常會有最大執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="3e9cb-110">所有執行緒都都在忙碌中，如果其他工作都被放在佇列中，直到執行緒可提供服務。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="3e9cb-111">您可以實作自己的執行緒集區，但很容易使用透過<xref:System.Threading.ThreadPool>類別</xref:System.Threading.ThreadPool>的.NET Framework 所提供的執行緒集區</span><span class="sxs-lookup"><span data-stu-id="3e9cb-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="3e9cb-112">執行緒集區，您就呼叫<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName>想要執行的程序的方法的委派和 Visual Basic 建立的執行緒，並執行您的程序。</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3e9cb-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName> method with a delegate for the procedure you want to run, and Visual Basic creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="3e9cb-113">執行緒集區範例</span><span class="sxs-lookup"><span data-stu-id="3e9cb-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="3e9cb-114">下列範例顯示如何使用執行緒集區啟動數個工作。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
```vb  
Public Sub DoWork()  
    ' Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf SomeLongTask))  
    ' Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf AnotherLongTask))  
End Sub  
Private Sub SomeLongTask(ByVal state As Object)  
    ' Insert code to perform a long task.  
End Sub  
Private Sub AnotherLongTask(ByVal state As Object)  
    ' Insert code to perform another long task.  
End Sub  
```  
  
 <span data-ttu-id="3e9cb-115">執行緒集區的其中一個優點是，您可以傳遞的狀態物件的引數給工作的程序。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="3e9cb-116">如果您要呼叫的程序需要多個引數，則可以轉換的結構或到類別的執行個體`Object`資料型別。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="3e9cb-117">執行緒集區參數和傳回值</span><span class="sxs-lookup"><span data-stu-id="3e9cb-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="3e9cb-118">傳回值，從執行緒集區執行緒並不簡單。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="3e9cb-119">不允許從函式呼叫傳回值的標準方式，因為`Sub`程序是唯一可以排入執行緒集區的程序的類型。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="3e9cb-120">其中一種您可以提供參數，並傳回值是藉由包裝參數，傳回的值與包裝函式中的方法類別中所述[參數和傳回值的多執行緒程序 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="3e9cb-121">提供的參數和傳回值解碼方法是使用選擇性`ByVal`狀態的物件變數<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>方法。</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span><span class="sxs-lookup"><span data-stu-id="3e9cb-121">An easer way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="3e9cb-122">如果您使用此變數傳遞類別的執行個體的參考時，可以修改執行緒集區執行緒之執行個體成員，並當做傳回值。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="3e9cb-123">一開始它可能不明顯，您可以修改傳值方式傳遞變數所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="3e9cb-124">您可以執行這項操作，因為物件參考傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="3e9cb-125">當您變更成員的物件參考所參考的物件時，所做的變更會套用至實際的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="3e9cb-126">結構無法用於傳回狀態物件內的值。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="3e9cb-127">由於結構是實值型別，對這個非同步處理序的變更，就不會變更原始結構的成員。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="3e9cb-128">使用提供的參數，不需要傳回值時的結構。</span><span class="sxs-lookup"><span data-stu-id="3e9cb-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9cb-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e9cb-129">See Also</span></span>  
 <span data-ttu-id="3e9cb-130"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span><span class="sxs-lookup"><span data-stu-id="3e9cb-130"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span></span>   
 <span data-ttu-id="3e9cb-131"><xref:System.Threading></xref:System.Threading></span><span class="sxs-lookup"><span data-stu-id="3e9cb-131"><xref:System.Threading></span></span>   
 <span data-ttu-id="3e9cb-132"><xref:System.Threading.ThreadPool></xref:System.Threading.ThreadPool></span><span class="sxs-lookup"><span data-stu-id="3e9cb-132"><xref:System.Threading.ThreadPool></span></span>   
<span data-ttu-id="3e9cb-133"> [如何︰ 使用執行緒集區 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md) </span><span class="sxs-lookup"><span data-stu-id="3e9cb-133"> [How to: Use a Thread Pool (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md) </span></span>  
<span data-ttu-id="3e9cb-134"> [執行緒處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span><span class="sxs-lookup"><span data-stu-id="3e9cb-134"> [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span></span>  
<span data-ttu-id="3e9cb-135"> [多執行緒應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span><span class="sxs-lookup"><span data-stu-id="3e9cb-135"> [Multithreaded Applications (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span></span>  
<span data-ttu-id="3e9cb-136"> [執行緒同步處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)</span><span class="sxs-lookup"><span data-stu-id="3e9cb-136"> [Thread Synchronization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)</span></span>
