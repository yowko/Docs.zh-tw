---
title: 活動程式庫
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: fae2a94b5e5e776625aa7f26700980640b66afd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142897"
---
# <a name="activity-library"></a><span data-ttu-id="3e320-102">活動程式庫</span><span class="sxs-lookup"><span data-stu-id="3e320-102">Activity Library</span></span>
<span data-ttu-id="3e320-103">本節包含演示 Windows 工作流基礎 （WF） 中高級自訂活動的示例。</span><span class="sxs-lookup"><span data-stu-id="3e320-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e320-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="3e320-104">In This Section</span></span>

 [<span data-ttu-id="3e320-105">SendMail 自訂活動</span><span class="sxs-lookup"><span data-stu-id="3e320-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="3e320-106">示範如何建立衍生自 <xref:System.Activities.AsyncCodeActivity> 的自訂活動，以使用 SMTP 來傳送郵件，供工作流程應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="3e320-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="3e320-107">節流平行 ForEach</span><span class="sxs-lookup"><span data-stu-id="3e320-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="3e320-108">示範 `ThrottleParallelForEach` 活動與 <xref:System.Activities.Statements.ParallelForEach%601> 活動如何類似，唯一的例外是它允許設定並行因數來限制同時執行的分支數目。</span><span class="sxs-lookup"><span data-stu-id="3e320-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="3e320-109">資料庫存取活動</span><span class="sxs-lookup"><span data-stu-id="3e320-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="3e320-110">演示如何創建允許訪問資料庫以檢索或修改資訊並使用[ADO.NET](../../data/adonet/index.md)訪問資料庫的活動。</span><span class="sxs-lookup"><span data-stu-id="3e320-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>  
  
 [<span data-ttu-id="3e320-111">.NET Framework 4.5 中的外顯化原則活動</span><span class="sxs-lookup"><span data-stu-id="3e320-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="3e320-112">演示外化策略4活動如何允許使用 WF 3.5 中隨附的規則引擎直接在 （WF 4.5） 中的 Windows 工作流基礎 （WF <xref:System.Workflow.Activities.Rules.RuleSet> 4.5） 中的[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]Windows 工作流基礎中執行現有的 Windows 工作流基礎。</span><span class="sxs-lookup"><span data-stu-id="3e320-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span>
  
 [<span data-ttu-id="3e320-113">非泛型 ForEach</span><span class="sxs-lookup"><span data-stu-id="3e320-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="3e320-114">示範如何建立非泛型 <xref:System.Activities.Statements.ForEach%601> 活動版本。</span><span class="sxs-lookup"><span data-stu-id="3e320-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="3e320-115">非泛型 ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="3e320-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="3e320-116">示範如何建立非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 活動版本。</span><span class="sxs-lookup"><span data-stu-id="3e320-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="3e320-117">取得 WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="3e320-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="3e320-118">示範如何使用 `GetWorkflowInstanceId` 自訂活動傳回工作流程執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="3e320-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
