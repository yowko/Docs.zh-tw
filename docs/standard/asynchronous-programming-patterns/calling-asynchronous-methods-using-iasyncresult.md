---
title: 使用 IAsyncResult 呼叫非同步方法
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23fa927dcdb91fb3905f1cbe845450751de91157
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46705471"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="5f481-102">使用 IAsyncResult 呼叫非同步方法</span><span class="sxs-lookup"><span data-stu-id="5f481-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="5f481-103">.NET Framework 和協力廠商類別程式庫中的型別提供的方法，可讓應用程式在主應用程式執行緒以外的執行緒中執行非同步作業時繼續執行。</span><span class="sxs-lookup"><span data-stu-id="5f481-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="5f481-104">下列各節說明並提供示範不同方式的程式碼範例，您可以呼叫使用 <xref:System.IAsyncResult> 設計模式的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="5f481-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
-   <span data-ttu-id="5f481-105">[以結束非同步作業的方式封鎖應用程式執行](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="5f481-105">[Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
-   <span data-ttu-id="5f481-106">[使用 AsyncWaitHandle 封鎖應用程式執行](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)。</span><span class="sxs-lookup"><span data-stu-id="5f481-106">[Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
-   <span data-ttu-id="5f481-107">[輪詢非同步作業的狀態](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="5f481-107">[Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
-   <span data-ttu-id="5f481-108">[使用 AsyncCallback 委派結束非同步作業](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="5f481-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f481-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f481-109">See also</span></span>

- [<span data-ttu-id="5f481-110">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="5f481-110">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [<span data-ttu-id="5f481-111">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="5f481-111">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
