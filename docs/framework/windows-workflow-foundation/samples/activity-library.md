---
title: 活動程式庫
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 15260fc2ad96e1761a8a41ccc84b2c199e3d448a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283158"
---
# <a name="activity-library"></a><span data-ttu-id="571fd-102">活動程式庫</span><span class="sxs-lookup"><span data-stu-id="571fd-102">Activity Library</span></span>
<span data-ttu-id="571fd-103">本節包含的範例示範如何在 Windows Workflow Foundation （WF）中進行先進的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="571fd-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="571fd-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="571fd-104">In This Section</span></span>

 [<span data-ttu-id="571fd-105">SendMail 自訂活動</span><span class="sxs-lookup"><span data-stu-id="571fd-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="571fd-106">示範如何建立衍生自 <xref:System.Activities.AsyncCodeActivity> 的自訂活動，以使用 SMTP 來傳送郵件，供工作流程應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="571fd-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="571fd-107">節流平行 ForEach</span><span class="sxs-lookup"><span data-stu-id="571fd-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="571fd-108">示範 `ThrottleParallelForEach` 活動與 <xref:System.Activities.Statements.ParallelForEach%601> 活動如何類似，唯一的例外是它允許設定並行因數來限制同時執行的分支數目。</span><span class="sxs-lookup"><span data-stu-id="571fd-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="571fd-109">資料庫存取活動</span><span class="sxs-lookup"><span data-stu-id="571fd-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="571fd-110">示範如何建立活動，以允許存取資料庫來抓取或修改資訊，以及使用[ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081)來存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="571fd-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
 [<span data-ttu-id="571fd-111">.NET Framework 4.5 中的外顯化原則活動</span><span class="sxs-lookup"><span data-stu-id="571fd-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="571fd-112">示範 ExternalizedPolicy4 活動如何使用 WF 3.5 中隨附的規則引擎，直接在 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] （WF 4.5） Windows Workflow Foundation 中的 .NET Framework 3.5 （WF 3.5）中執行現有的 Windows Workflow Foundation <xref:System.Workflow.Activities.Rules.RuleSet> 物件。</span><span class="sxs-lookup"><span data-stu-id="571fd-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span> 
  
 [<span data-ttu-id="571fd-113">非泛型 ForEach</span><span class="sxs-lookup"><span data-stu-id="571fd-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="571fd-114">示範如何建立非泛型 <xref:System.Activities.Statements.ForEach%601> 活動版本。</span><span class="sxs-lookup"><span data-stu-id="571fd-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="571fd-115">非泛型 ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="571fd-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="571fd-116">示範如何建立非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 活動版本。</span><span class="sxs-lookup"><span data-stu-id="571fd-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="571fd-117">取得 WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="571fd-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="571fd-118">示範如何使用 `GetWorkflowInstanceId` 自訂活動傳回工作流程執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="571fd-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
