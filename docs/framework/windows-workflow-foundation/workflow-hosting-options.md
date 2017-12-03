---
title: "工作流程裝載選項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72c9c2078f694a1739a7f33689a0d8275d786937
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-hosting-options"></a><span data-ttu-id="60d70-102">工作流程裝載選項</span><span class="sxs-lookup"><span data-stu-id="60d70-102">Workflow Hosting Options</span></span>
<span data-ttu-id="60d70-103">大部分的 [!INCLUDE[wf](../../../includes/wf-md.md)] 範例是使用裝載於主控台應用程式中的工作流程，但這並不是真實世界工作流程中的實際情況。</span><span class="sxs-lookup"><span data-stu-id="60d70-103">Most of the [!INCLUDE[wf](../../../includes/wf-md.md)] samples use workflows that are hosted in a console application, but this isn't a realistic scenario for real-world workflows.</span></span> <span data-ttu-id="60d70-104">實際商務應用程式中的工作流程會裝載在持續性程序中，可能是開發人員撰寫的 Windows 服務，或是像 [!INCLUDE[iisver](../../../includes/iisver-md.md)] 或 AppFabric 之類的伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="60d70-104">Workflows in actual business applications will be hosted in persistent processes- either a Windows service authored by the developer, or a server application such as [!INCLUDE[iisver](../../../includes/iisver-md.md)] or AppFabric.</span></span> <span data-ttu-id="60d70-105">這些方法之間差異如下。</span><span class="sxs-lookup"><span data-stu-id="60d70-105">The differences between these approaches are as follows.</span></span>  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a><span data-ttu-id="60d70-106">在具有 Windows AppFabric 的 IIS 中裝載工作流程</span><span class="sxs-lookup"><span data-stu-id="60d70-106">Hosting workflows in IIS with Windows AppFabric</span></span>  
 <span data-ttu-id="60d70-107">使用具有 AppFabric 的 IIS 是工作流程的慣用主機。</span><span class="sxs-lookup"><span data-stu-id="60d70-107">Using IIS with AppFabric is the preferred host for workflows.</span></span> <span data-ttu-id="60d70-108">使用 AppFabric 的工作流程主應用程式是 Windows 啟用服務，它會單獨由 IIS 中移除對 HTTP 的相依性。</span><span class="sxs-lookup"><span data-stu-id="60d70-108">The host application for workflows using AppFabric is Windows Activation Service, which removes the dependency on HTTP over IIS alone.</span></span>  
  
## <a name="hosting-workflows-in-iis-alone"></a><span data-ttu-id="60d70-109">只在 IIS 中裝載工作流程</span><span class="sxs-lookup"><span data-stu-id="60d70-109">Hosting workflows in IIS alone</span></span>  
 <span data-ttu-id="60d70-110">不建議單獨使用 [!INCLUDE[iisver](../../../includes/iisver-md.md)]，因為 AppFabric 有管理和監視工具，可協助維護執行中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="60d70-110">Using [!INCLUDE[iisver](../../../includes/iisver-md.md)] alone is not recommended, as there are management and monitoring tools available with AppFabric that facilitate maintenance of running applications.</span></span> <span data-ttu-id="60d70-111">如果有移至 AppFabric 的相關基礎結構顧慮，則工作流程應該只裝載在 [!INCLUDE[iisver](../../../includes/iisver-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="60d70-111">Workflows should only be hosted in [!INCLUDE[iisver](../../../includes/iisver-md.md)] alone if there are infrastructure concerns with moving to AppFabric.</span></span>  
  
> [!WARNING]
>  [!INCLUDE[iisver](../../../includes/iisver-md.md)]<span data-ttu-id="60d70-112"> 會因為各種理由定期回收應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="60d70-112"> recycles application pools periodically for various reasons.</span></span> <span data-ttu-id="60d70-113">回收應用程式集區時，IIS 會停止接受訊息至舊集區，並產生新的應用程式集區以接受新的要求。</span><span class="sxs-lookup"><span data-stu-id="60d70-113">When an application pool is recycled, IIS stops accepting messages to the old pool, and instantiates a new application pool to accept new requests.</span></span> <span data-ttu-id="60d70-114">如果工作流程在傳送回應之後繼續運作，[!INCLUDE[iisver](../../../includes/iisver-md.md)] 不會感知已執行的工作，且可能會回收進行裝載的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="60d70-114">If a workflow continues working after sending a response, [!INCLUDE[iisver](../../../includes/iisver-md.md)] will not be aware of the work being done, and may recycle the hosting application pool.</span></span> <span data-ttu-id="60d70-115">如果發生這種情況，將會中止工作流程，並追蹤服務會記錄[1004-WorkflowInstanceAborted](../../../docs/framework/windows-workflow-foundation/1004-workflowinstanceaborted.md)空白的 [原因] 欄位的訊息。</span><span class="sxs-lookup"><span data-stu-id="60d70-115">If this happens, the workflow will abort, and tracking services will record a [1004 - WorkflowInstanceAborted](../../../docs/framework/windows-workflow-foundation/1004-workflowinstanceaborted.md) message with an empty Reason field.</span></span>  
>   
>  <span data-ttu-id="60d70-116">如果使用持續性，主機必須從上次的保存點，明確地將中止的執行個體重新啟動。</span><span class="sxs-lookup"><span data-stu-id="60d70-116">If persistence is used, the host must explicitly restart aborted instances from the last persistence point.</span></span>  
>   
>  <span data-ttu-id="60d70-117">如果使用 AppFabric，工作流程管理服務最後會從上次的成功保存點 (如果使用持續性) 繼續工作流程。</span><span class="sxs-lookup"><span data-stu-id="60d70-117">If AppFabric is used, the workflow management service will eventually resume the workflow from the last successful persistence point if persistence is used.</span></span> <span data-ttu-id="60d70-118">如果沒有使用持續性，而且工作流程不是以「要求/回應」模式執行作業，資料將會在工作流程中止時遺失。</span><span class="sxs-lookup"><span data-stu-id="60d70-118">If no persistence is used, and the workflow performs operations outside a Request/Response pattern, data will be lost when the workflow aborts.</span></span>  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a><span data-ttu-id="60d70-119">在自訂 Windows 服務中裝載工作流程</span><span class="sxs-lookup"><span data-stu-id="60d70-119">Hosting a workflow in a custom Windows Service</span></span>  
 <span data-ttu-id="60d70-120">建立自訂工作流程服務來裝載工作流程，需要開發人員重複許多由 AppFabric 提供的全新功能，不過在自訂功能方面較有彈性。</span><span class="sxs-lookup"><span data-stu-id="60d70-120">Creating a custom workflow service to host the workflow will require the developer to duplicate a lot of the functionality provided out-of-box by AppFabric, but will allow for more flexibility with custom functionality.</span></span> <span data-ttu-id="60d70-121">唯有確定 AppFabric 不是選項時，才能考慮此選項。</span><span class="sxs-lookup"><span data-stu-id="60d70-121">This option should only be considered if AppFabric proves to not be an option.</span></span>
