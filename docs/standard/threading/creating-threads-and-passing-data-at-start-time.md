---
title: 建立執行緒並在啟動時間傳遞資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96c0c898f103c058c370a0d108568056b1ff8196
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586574"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="6c5a6-102">建立執行緒並在啟動時間傳遞資料</span><span class="sxs-lookup"><span data-stu-id="6c5a6-102">Creating Threads and Passing Data at Start Time</span></span>
<span data-ttu-id="6c5a6-103">建立作業系統處理序時，作業系統會插入執行緒以在該處理序中執行程式碼，包括任何原始的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="6c5a6-104">從那時起，不一定要建立或終結任何作業系統執行緒，就能建立和終結應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="6c5a6-105">如果正在執行的程式碼為受控碼，則可藉由擷取類型 <xref:System.Threading.Thread> 的靜態 <xref:System.Threading.Thread.CurrentThread%2A> 屬性，來取得正在目前應用程式定義域中執行之執行緒的 <xref:System.Threading.Thread> 物件。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="6c5a6-106">本主題說明執行緒的建立，並討論將資料傳遞至執行緒程序的替代方案。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="6c5a6-107">建立執行緒</span><span class="sxs-lookup"><span data-stu-id="6c5a6-107">Creating a Thread</span></span>  
 <span data-ttu-id="6c5a6-108">建立新的 <xref:System.Threading.Thread> 物件，會建立新的受控執行緒。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="6c5a6-109"><xref:System.Threading.Thread> 類別具有採用 <xref:System.Threading.ThreadStart> 委派或 <xref:System.Threading.ParameterizedThreadStart> 委派的建構函式；委派會包裝當您呼叫 <xref:System.Threading.Thread.Start%2A> 方法時新執行緒所叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="6c5a6-110">呼叫 <xref:System.Threading.Thread.Start%2A> 超過一次，就會擲回 <xref:System.Threading.ThreadStateException>。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="6c5a6-111"><xref:System.Threading.Thread.Start%2A> 方法會立即傳回，通常會在實際啟動新的執行緒之前。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="6c5a6-112">您隨時都可使用 <xref:System.Threading.Thread.ThreadState%2A> 和 <xref:System.Threading.Thread.IsAlive%2A> 屬性來判斷執行緒的狀態，但不應使用這些屬性來進行執行緒活動的同步處理。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c5a6-113">一旦啟動執行緒之後，就不需要保留對 <xref:System.Threading.Thread> 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="6c5a6-114">執行緒會繼續執行，直到執行緒程序結束為止。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="6c5a6-115">下列程式碼範例會建立兩個新的執行緒，來呼叫另一個物件上的執行個體和靜態方法。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a><span data-ttu-id="6c5a6-116">將資料傳遞給執行緒以及從執行緒擷取資料</span><span class="sxs-lookup"><span data-stu-id="6c5a6-116">Passing Data to Threads and Retrieving Data from Threads</span></span>  
 <span data-ttu-id="6c5a6-117">在 .NET Framework 2.0 版中，<xref:System.Threading.ParameterizedThreadStart> 委派提供了一個簡易的方式，在您呼叫 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> 方法多載時，將包含資料的物件傳遞至執行緒。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="6c5a6-118">請參閱 <xref:System.Threading.ParameterizedThreadStart>，以取得程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="6c5a6-119">使用 <xref:System.Threading.ParameterizedThreadStart> 委派並非傳遞資料的類型安全方式，因為 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> 方法多載接受任何物件。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="6c5a6-120">替代方法是在協助程式類別中封裝執行緒程序和資料，並使用 <xref:System.Threading.ThreadStart> 委派來執行執行緒程序。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="6c5a6-121">接下來的兩個程式碼範例將示範這項技術。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-121">This technique is shown in the two code examples that follow.</span></span>  
  
 <span data-ttu-id="6c5a6-122">這兩個委派都沒有傳回值，因為沒有地方可從非同步呼叫傳回資料。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-122">Neither of these delegates has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="6c5a6-123">若要擷取執行緒方法的結果，您可以使用回呼方法，如第二個程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-123">To retrieve the results of a thread method, you can use a callback method, as demonstrated in the second code example.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a><span data-ttu-id="6c5a6-124">使用回呼方法擷取資料</span><span class="sxs-lookup"><span data-stu-id="6c5a6-124">Retrieving Data with Callback Methods</span></span>  
 <span data-ttu-id="6c5a6-125">下列範例示範從執行緒擷取資料的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="6c5a6-126">包含資料和執行緒方法之類別的建構函式也會接受代表回呼方法的委派；在執行緒方法結束之前，它會叫用回呼委派。</span><span class="sxs-lookup"><span data-stu-id="6c5a6-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6c5a6-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="6c5a6-127">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="6c5a6-128">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="6c5a6-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="6c5a6-129">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="6c5a6-129">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
