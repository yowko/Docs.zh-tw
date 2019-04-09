---
title: ETW Events in the .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework ETW events
- ETW events in the .NET Framework
ms.assetid: d186276f-6afb-4dfd-bf3c-4251edc2c299
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa36399320a8c396a222619172264a32f3eb3505
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072723"
---
# <a name="etw-events-in-the-net-framework"></a><span data-ttu-id="7bf1b-102">ETW Events in the .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7bf1b-102">ETW Events in the .NET Framework</span></span>
<span data-ttu-id="7bf1b-103">Windows 事件追蹤 (ETW) 是 Windows 作業系統提供的高效能、低負擔、可擴充的追蹤系統。</span><span class="sxs-lookup"><span data-stu-id="7bf1b-103">Event tracing for Windows (ETW) is a high-performance, low-overhead, scalable tracing system provided by Windows operating systems.</span></span> <span data-ttu-id="7bf1b-104">它會補充由 .NET Framework 提供的程式碼剖析和偵錯支援，並可用於針對各種案例進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="7bf1b-104">It supplements the profiling and debugging support provided by the .NET Framework and can be used to troubleshoot a variety of scenarios.</span></span>  
  
 <span data-ttu-id="7bf1b-105">在 .NET Framework 中，Common Language Runtime (CLR)、[工作平行程式庫](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)和[平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md) 都提供 ETW 事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="7bf1b-105">In the .NET Framework, ETW event tracing is available for the common language runtime (CLR), the [Task Parallel Library](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md), and [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7bf1b-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="7bf1b-106">In This Section</span></span>  
 [<span data-ttu-id="7bf1b-107">工作平行程式庫和 PLINQ 中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="7bf1b-107">ETW Events in Task Parallel Library and PLINQ</span></span>](../../../docs/framework/performance/etw-events-in-task-parallel-library-and-plinq.md)  
 <span data-ttu-id="7bf1b-108">描述如何對平行應用程式程式碼進行程式碼剖析。</span><span class="sxs-lookup"><span data-stu-id="7bf1b-108">Describes how to profile parallel application code.</span></span>  
  
 [<span data-ttu-id="7bf1b-109">Common Language Runtime 中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="7bf1b-109">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)  
 <span data-ttu-id="7bf1b-110">描述 CLR ETW 事件如何補充 Common Language Runtime 所提供的分析和偵錯支援。</span><span class="sxs-lookup"><span data-stu-id="7bf1b-110">Describes how CLR ETW events supplement the profiling and debugging support provided by the common language runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf1b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bf1b-111">See also</span></span>

- [<span data-ttu-id="7bf1b-112">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="7bf1b-112">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
- [<span data-ttu-id="7bf1b-113">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="7bf1b-113">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [<span data-ttu-id="7bf1b-114">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="7bf1b-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
