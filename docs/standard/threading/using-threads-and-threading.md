---
title: "使用執行緒和執行緒處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5bed13950a29cfa787ef8c9eb2608c6d74dfd49f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="using-threads-and-threading"></a><span data-ttu-id="5e881-102">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="5e881-102">Using Threads and Threading</span></span>
<span data-ttu-id="5e881-103">本節中的主題將討論受控執行緒的建立和管理、如何將資料傳遞至受控執行緒並取得結果，以及如何終結執行緒和處理 <xref:System.Threading.ThreadAbortException>。</span><span class="sxs-lookup"><span data-stu-id="5e881-103">The topics in this section discuss the creation and management of managed threads, how to pass data to managed threads and get results back, and how to destroy threads and handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5e881-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="5e881-104">In This Section</span></span>  
 [<span data-ttu-id="5e881-105">建立執行緒並在啟動時間傳遞資料</span><span class="sxs-lookup"><span data-stu-id="5e881-105">Creating Threads and Passing Data at Start Time</span></span>](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 <span data-ttu-id="5e881-106">討論並示範受控執行緒的建立，包括如何將資料傳遞給至新的執行緒，以及如何取得資料。</span><span class="sxs-lookup"><span data-stu-id="5e881-106">Discusses and demonstrates the creation of managed threads, including how to pass data to new threads and how to get data back.</span></span>  
  
 [<span data-ttu-id="5e881-107">暫止和繼續執行緒</span><span class="sxs-lookup"><span data-stu-id="5e881-107">Pausing and Resuming Threads</span></span>](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 <span data-ttu-id="5e881-108">討論暫停和繼續受控執行緒的後果。</span><span class="sxs-lookup"><span data-stu-id="5e881-108">Discusses the ramifications of pausing and resuming managed threads.</span></span>  
  
 [<span data-ttu-id="5e881-109">終結執行緒</span><span class="sxs-lookup"><span data-stu-id="5e881-109">Destroying Threads</span></span>](../../../docs/standard/threading/destroying-threads.md)  
 <span data-ttu-id="5e881-110">討論終結受控執行緒的後果，以及如何處理 <xref:System.Threading.ThreadAbortException>。</span><span class="sxs-lookup"><span data-stu-id="5e881-110">Discusses the ramifications of destroying managed threads, and how to handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 [<span data-ttu-id="5e881-111">排程執行緒</span><span class="sxs-lookup"><span data-stu-id="5e881-111">Scheduling Threads</span></span>](../../../docs/standard/threading/scheduling-threads.md)  
 <span data-ttu-id="5e881-112">討論執行緒的優先順序，以及它們如何影響執行緒排程。</span><span class="sxs-lookup"><span data-stu-id="5e881-112">Discusses thread priorities and how they affect thread scheduling.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5e881-113">參考資料</span><span class="sxs-lookup"><span data-stu-id="5e881-113">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="5e881-114">提供 <xref:System.Threading.Thread> 類別的參考文件，不論這個類別來自非受控碼或在受控應用程式中所建立，都代表受控執行緒。</span><span class="sxs-lookup"><span data-stu-id="5e881-114">Provides reference documentation for the <xref:System.Threading.Thread> class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.Threading.ThreadStart>  
 <span data-ttu-id="5e881-115">提供 <xref:System.Threading.ThreadStart> 委派的參考文件，這個委派代表無參數的執行緒程序。</span><span class="sxs-lookup"><span data-stu-id="5e881-115">Provides reference documentation for the <xref:System.Threading.ThreadStart> delegate that represents parameterless thread procedures.</span></span>  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 <span data-ttu-id="5e881-116">儘管沒有強式類型，還是會提供一個簡單的方法來將資料傳遞給執行緒程序。</span><span class="sxs-lookup"><span data-stu-id="5e881-116">Provides an easy way to pass data to a thread procedure, although without strong typing.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5e881-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="5e881-117">Related Sections</span></span>  
 [<span data-ttu-id="5e881-118">執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="5e881-118">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="5e881-119">提供受控執行緒的簡介。</span><span class="sxs-lookup"><span data-stu-id="5e881-119">Provides an introduction to managed threading.</span></span>
