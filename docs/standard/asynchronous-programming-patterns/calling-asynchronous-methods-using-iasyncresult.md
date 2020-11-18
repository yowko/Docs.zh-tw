---
title: 使用 IAsyncResult 呼叫非同步方法
ms.date: 03/30/2017
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 20aafd45c323a609b3cc7fb5a1a6378d43548fcb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830450"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="cbf2a-102">使用 IAsyncResult 呼叫非同步方法</span><span class="sxs-lookup"><span data-stu-id="cbf2a-102">Calling Asynchronous Methods Using IAsyncResult</span></span>

<span data-ttu-id="cbf2a-103">.NET 程式庫和協力廠商類別庫中的類型可以提供方法，讓應用程式在主應用程式執行緒以外的執行緒中執行非同步作業時，繼續執行。</span><span class="sxs-lookup"><span data-stu-id="cbf2a-103">Types in the .NET libraries and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="cbf2a-104">下列各節說明並提供示範不同方式的程式碼範例，您可以呼叫使用 <xref:System.IAsyncResult> 設計模式的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="cbf2a-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="cbf2a-105">藉[由結束非同步作業來封鎖應用程式執行](blocking-application-execution-by-ending-an-async-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="cbf2a-105">[Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="cbf2a-106">[使用 AsyncWaitHandle 封鎖應用程式執行](blocking-application-execution-using-an-asyncwaithandle.md)。</span><span class="sxs-lookup"><span data-stu-id="cbf2a-106">[Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="cbf2a-107">[輪詢非同步作業的狀態](polling-for-the-status-of-an-asynchronous-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="cbf2a-107">[Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="cbf2a-108">[使用 AsyncCallback 委派結束非同步作業](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="cbf2a-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbf2a-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="cbf2a-109">See also</span></span>

- [<span data-ttu-id="cbf2a-110">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="cbf2a-110">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="cbf2a-111">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="cbf2a-111">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
