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
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80eb4c3bb98acdd1f83dbf5bcf57b2f7b295742b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-threads-and-threading"></a><span data-ttu-id="5312f-102">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="5312f-102">Using Threads and Threading</span></span>
<span data-ttu-id="5312f-103">本節中的主題討論的建立和管理的 managed 的執行緒、 如何將資料傳遞至 managed 執行緒，並取得結果，以及如何終結執行緒和處理<xref:System.Threading.ThreadAbortException>。</span><span class="sxs-lookup"><span data-stu-id="5312f-103">The topics in this section discuss the creation and management of managed threads, how to pass data to managed threads and get results back, and how to destroy threads and handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5312f-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="5312f-104">In This Section</span></span>  
 [<span data-ttu-id="5312f-105">建立執行緒並在啟動時間傳遞資料</span><span class="sxs-lookup"><span data-stu-id="5312f-105">Creating Threads and Passing Data at Start Time</span></span>](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 <span data-ttu-id="5312f-106">討論並示範如何建立 managed 執行緒，包括如何將資料傳遞給新執行緒，以及如何取得資料。</span><span class="sxs-lookup"><span data-stu-id="5312f-106">Discusses and demonstrates the creation of managed threads, including how to pass data to new threads and how to get data back.</span></span>  
  
 [<span data-ttu-id="5312f-107">暫止和繼續執行緒</span><span class="sxs-lookup"><span data-stu-id="5312f-107">Pausing and Resuming Threads</span></span>](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 <span data-ttu-id="5312f-108">討論暫停和繼續 managed 的執行緒的後果。</span><span class="sxs-lookup"><span data-stu-id="5312f-108">Discusses the ramifications of pausing and resuming managed threads.</span></span>  
  
 [<span data-ttu-id="5312f-109">終結執行緒</span><span class="sxs-lookup"><span data-stu-id="5312f-109">Destroying Threads</span></span>](../../../docs/standard/threading/destroying-threads.md)  
 <span data-ttu-id="5312f-110">討論的終結 managed 的執行緒，以及如何處理後果<xref:System.Threading.ThreadAbortException>。</span><span class="sxs-lookup"><span data-stu-id="5312f-110">Discusses the ramifications of destroying managed threads, and how to handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 [<span data-ttu-id="5312f-111">排程執行緒</span><span class="sxs-lookup"><span data-stu-id="5312f-111">Scheduling Threads</span></span>](../../../docs/standard/threading/scheduling-threads.md)  
 <span data-ttu-id="5312f-112">討論執行緒的優先順序，以及它們如何影響執行緒排程。</span><span class="sxs-lookup"><span data-stu-id="5312f-112">Discusses thread priorities and how they affect thread scheduling.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5312f-113">參考資料</span><span class="sxs-lookup"><span data-stu-id="5312f-113">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="5312f-114">提供參考文件<xref:System.Threading.Thread>類別，其代表 managed 的執行緒，還是來自 unmanaged 程式碼中的受管理的應用程式所建立。</span><span class="sxs-lookup"><span data-stu-id="5312f-114">Provides reference documentation for the <xref:System.Threading.Thread> class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.Threading.ThreadStart>  
 <span data-ttu-id="5312f-115">提供參考文件<xref:System.Threading.ThreadStart>委派，表示無參數的執行緒程序。</span><span class="sxs-lookup"><span data-stu-id="5312f-115">Provides reference documentation for the <xref:System.Threading.ThreadStart> delegate that represents parameterless thread procedures.</span></span>  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 <span data-ttu-id="5312f-116">提供簡單的方法，將資料傳遞給執行緒的程序，雖然沒有強型別。</span><span class="sxs-lookup"><span data-stu-id="5312f-116">Provides an easy way to pass data to a thread procedure, although without strong typing.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5312f-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="5312f-117">Related Sections</span></span>  
 [<span data-ttu-id="5312f-118">執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="5312f-118">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="5312f-119">提供 managed 執行緒的簡介。</span><span class="sxs-lookup"><span data-stu-id="5312f-119">Provides an introduction to managed threading.</span></span>
