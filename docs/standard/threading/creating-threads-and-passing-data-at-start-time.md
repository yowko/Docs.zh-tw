---
title: "建立執行緒並在啟動時間傳遞資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61808dc804cc627ab368a5250414dfcc5f54c87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="57896-102">建立執行緒並在啟動時間傳遞資料</span><span class="sxs-lookup"><span data-stu-id="57896-102">Creating Threads and Passing Data at Start Time</span></span>
<span data-ttu-id="57896-103">建立作業系統處理序時，作業系統會插入該處理程序，包括任何原始的應用程式定義域中執行程式碼的執行緒。</span><span class="sxs-lookup"><span data-stu-id="57896-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="57896-104">從該點上，應用程式定義域可以建立和終結不一定要建立或終結任何作業系統執行緒。</span><span class="sxs-lookup"><span data-stu-id="57896-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="57896-105">如果正在執行的程式碼為 managed 程式碼，則<xref:System.Threading.Thread>物件目前的應用程式定義域中的執行緒執行，可取得擷取靜態<xref:System.Threading.Thread.CurrentThread%2A>型別的屬性<xref:System.Threading.Thread>。</span><span class="sxs-lookup"><span data-stu-id="57896-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="57896-106">本主題說明執行緒的建立，並討論將資料傳遞給執行緒的程序的替代方案。</span><span class="sxs-lookup"><span data-stu-id="57896-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="57896-107">建立執行緒</span><span class="sxs-lookup"><span data-stu-id="57896-107">Creating a Thread</span></span>  
 <span data-ttu-id="57896-108">建立新<xref:System.Threading.Thread>物件會建立新的 managed 的執行緒。</span><span class="sxs-lookup"><span data-stu-id="57896-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="57896-109"><xref:System.Threading.Thread>類別具有建構函式採用<xref:System.Threading.ThreadStart>委派或<xref:System.Threading.ParameterizedThreadStart>委派; 委派將包裝的方法，當您呼叫新的執行緒所叫用<xref:System.Threading.Thread.Start%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="57896-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="57896-110">呼叫<xref:System.Threading.Thread.Start%2A>超過一次會造成<xref:System.Threading.ThreadStateException>擲回。</span><span class="sxs-lookup"><span data-stu-id="57896-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="57896-111"><xref:System.Threading.Thread.Start%2A>方法會傳回立即，通常具有實際上會啟動新的執行緒之前。</span><span class="sxs-lookup"><span data-stu-id="57896-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="57896-112">您可以使用<xref:System.Threading.Thread.ThreadState%2A>和<xref:System.Threading.Thread.IsAlive%2A>屬性來判斷任何時刻，執行緒的狀態，但這些屬性應永遠不會用於同步處理執行緒活動。</span><span class="sxs-lookup"><span data-stu-id="57896-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57896-113">一旦在執行緒啟動時，不需要保留的參考<xref:System.Threading.Thread>物件。</span><span class="sxs-lookup"><span data-stu-id="57896-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="57896-114">執行緒會繼續執行，直到執行緒程序的結尾。</span><span class="sxs-lookup"><span data-stu-id="57896-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="57896-115">下列程式碼範例會建立兩個新的執行緒來呼叫另一個物件的執行個體和靜態方法。</span><span class="sxs-lookup"><span data-stu-id="57896-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a><span data-ttu-id="57896-116">將資料傳遞給執行緒和執行緒中擷取資料</span><span class="sxs-lookup"><span data-stu-id="57896-116">Passing Data to Threads and Retrieving Data from Threads</span></span>  
 <span data-ttu-id="57896-117">在.NET Framework 2.0 版中，<xref:System.Threading.ParameterizedThreadStart>委派提供了簡易的方式傳遞物件，其中包含資料的執行緒，當您呼叫<xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>方法多載。</span><span class="sxs-lookup"><span data-stu-id="57896-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="57896-118">請參閱 <xref:System.Threading.ParameterizedThreadStart>，以取得程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="57896-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="57896-119">使用<xref:System.Threading.ParameterizedThreadStart>委派不以類型安全的方式來傳遞資料，因為<xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>方法多載會接受任何物件。</span><span class="sxs-lookup"><span data-stu-id="57896-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="57896-120">封裝執行緒的程序和協助程式類別中的資料，並使用替代方法是<xref:System.Threading.ThreadStart>委派來執行執行緒的程序。</span><span class="sxs-lookup"><span data-stu-id="57896-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="57896-121">接下來的兩個程式碼範例會顯示這項技術。</span><span class="sxs-lookup"><span data-stu-id="57896-121">This technique is shown in the two code examples that follow.</span></span>  
  
 <span data-ttu-id="57896-122">這兩種情況委派具有傳回值，因為沒有非同步呼叫傳回的資料位置。</span><span class="sxs-lookup"><span data-stu-id="57896-122">Neither of these delegates has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="57896-123">若要擷取執行緒方法的結果，您可以使用回呼方法，在第二個程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="57896-123">To retrieve the results of a thread method, you can use a callback method, as demonstrated in the second code example.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a><span data-ttu-id="57896-124">回呼方法以擷取資料</span><span class="sxs-lookup"><span data-stu-id="57896-124">Retrieving Data with Callback Methods</span></span>  
 <span data-ttu-id="57896-125">下列範例示範從執行緒中擷取資料的回撥方法。</span><span class="sxs-lookup"><span data-stu-id="57896-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="57896-126">包含資料和執行緒方法的類別的建構函式也接受委派代表的回呼方法。結束執行緒方法之前，它會叫用的回呼委派。</span><span class="sxs-lookup"><span data-stu-id="57896-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="57896-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57896-127">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="57896-128">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="57896-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="57896-129">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="57896-129">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
