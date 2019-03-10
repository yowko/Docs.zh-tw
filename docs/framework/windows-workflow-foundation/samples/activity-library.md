---
title: 活動程式庫
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: b701d382c25644181b23f3c0f0cd8e019b8d37d1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709831"
---
# <a name="activity-library"></a><span data-ttu-id="28d4c-102">活動程式庫</span><span class="sxs-lookup"><span data-stu-id="28d4c-102">Activity Library</span></span>
<span data-ttu-id="28d4c-103">本節包含示範進階自訂活動中 Windows Workflow Foundation (WF) 範例。</span><span class="sxs-lookup"><span data-stu-id="28d4c-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28d4c-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="28d4c-104">In This Section</span></span>

 [<span data-ttu-id="28d4c-105">SendMail 自訂活動</span><span class="sxs-lookup"><span data-stu-id="28d4c-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="28d4c-106">示範如何建立衍生自 <xref:System.Activities.AsyncCodeActivity> 的自訂活動，以使用 SMTP 來傳送郵件，供工作流程應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="28d4c-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="28d4c-107">節流平行 ForEach</span><span class="sxs-lookup"><span data-stu-id="28d4c-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="28d4c-108">示範 `ThrottleParallelForEach` 活動與 <xref:System.Activities.Statements.ParallelForEach%601> 活動如何類似，唯一的例外是它允許設定並行因數來限制同時執行的分支數目。</span><span class="sxs-lookup"><span data-stu-id="28d4c-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="28d4c-109">資料庫存取活動</span><span class="sxs-lookup"><span data-stu-id="28d4c-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="28d4c-110">示範如何建立活動，可讓您存取資料庫以擷取或修改資訊以及使用[ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081)來存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="28d4c-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
 [<span data-ttu-id="28d4c-111">.NET Framework 4.5 中的外顯化原則活動</span><span class="sxs-lookup"><span data-stu-id="28d4c-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="28d4c-112">示範 ExternalizedPolicy4 活動如何讓執行中的現有 Windows Workflow Foundation [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5)<xref:System.Workflow.Activities.Rules.RuleSet>物件中的 Windows Workflow foundation [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) 直接使用規則引擎也就是WF 3.5 隨附。</span><span class="sxs-lookup"><span data-stu-id="28d4c-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span> 
  
 [<span data-ttu-id="28d4c-113">非泛型 ForEach</span><span class="sxs-lookup"><span data-stu-id="28d4c-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="28d4c-114">示範如何建立非泛型 <xref:System.Activities.Statements.ForEach%601> 活動版本。</span><span class="sxs-lookup"><span data-stu-id="28d4c-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="28d4c-115">非泛型 ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="28d4c-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="28d4c-116">示範如何建立非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 活動版本。</span><span class="sxs-lookup"><span data-stu-id="28d4c-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="28d4c-117">取得 WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="28d4c-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="28d4c-118">示範如何使用 `GetWorkflowInstanceId` 自訂活動傳回工作流程執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="28d4c-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
