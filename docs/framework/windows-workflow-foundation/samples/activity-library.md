---
title: 活動程式庫
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 1a0c289315d7181645573098916788f18493abb8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245691"
---
# <a name="activity-library"></a><span data-ttu-id="f44a5-102">活動程式庫</span><span class="sxs-lookup"><span data-stu-id="f44a5-102">Activity Library</span></span>

<span data-ttu-id="f44a5-103">本節包含的範例會示範 Windows Workflow Foundation (WF) 中的先進自訂活動。</span><span class="sxs-lookup"><span data-stu-id="f44a5-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f44a5-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="f44a5-104">In This Section</span></span>

 [<span data-ttu-id="f44a5-105">SendMail 自訂活動</span><span class="sxs-lookup"><span data-stu-id="f44a5-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="f44a5-106">示範如何建立衍生自 <xref:System.Activities.AsyncCodeActivity> 的自訂活動，以使用 SMTP 來傳送郵件，供工作流程應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="f44a5-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="f44a5-107">流速控制平行 ForEach</span><span class="sxs-lookup"><span data-stu-id="f44a5-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="f44a5-108">示範 `ThrottleParallelForEach` 活動與 <xref:System.Activities.Statements.ParallelForEach%601> 活動如何類似，唯一的例外是它允許設定並行因數來限制同時執行的分支數目。</span><span class="sxs-lookup"><span data-stu-id="f44a5-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="f44a5-109">資料庫存取活動</span><span class="sxs-lookup"><span data-stu-id="f44a5-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="f44a5-110">示範如何建立允許存取資料庫以取得或修改資訊，以及使用 [ADO.NET](../../data/adonet/index.md) 存取資料庫的活動。</span><span class="sxs-lookup"><span data-stu-id="f44a5-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>  
  
 [<span data-ttu-id="f44a5-111">.NET Framework 4.5 中的外顯化原則活動</span><span class="sxs-lookup"><span data-stu-id="f44a5-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="f44a5-112">示範 ExternalizedPolicy4 活動如何 <xref:System.Workflow.Activities.Rules.RuleSet> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 使用 wf 3.5 中隨附的規則引擎，直接在 Windows Workflow Foundation wf 4.5 () 中的 .NET Framework 3.5 (WF 3.5) 物件中執行現有的 Windows Workflow Foundation。</span><span class="sxs-lookup"><span data-stu-id="f44a5-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span>
  
 [<span data-ttu-id="f44a5-113">非泛型 ForEach</span><span class="sxs-lookup"><span data-stu-id="f44a5-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="f44a5-114">示範如何建立非泛型 <xref:System.Activities.Statements.ForEach%601> 活動版本。</span><span class="sxs-lookup"><span data-stu-id="f44a5-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="f44a5-115">非泛型 ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="f44a5-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="f44a5-116">示範如何建立非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 活動版本。</span><span class="sxs-lookup"><span data-stu-id="f44a5-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="f44a5-117">取得 WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="f44a5-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="f44a5-118">示範如何使用 `GetWorkflowInstanceId` 自訂活動傳回工作流程執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="f44a5-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
