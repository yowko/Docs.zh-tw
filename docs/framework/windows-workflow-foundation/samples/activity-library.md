---
title: 活動程式庫
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 7e8777d0068e6cca9c9324a6fd2668e6ff9e9da7
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123120"
---
# <a name="activity-library"></a><span data-ttu-id="3ea80-102">活動程式庫</span><span class="sxs-lookup"><span data-stu-id="3ea80-102">Activity Library</span></span>
<span data-ttu-id="3ea80-103">本節包含示範進階自訂活動中 Windows Workflow Foundation (WF) 範例。</span><span class="sxs-lookup"><span data-stu-id="3ea80-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3ea80-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="3ea80-104">In This Section</span></span>

 [<span data-ttu-id="3ea80-105">SendMail 自訂活動</span><span class="sxs-lookup"><span data-stu-id="3ea80-105">SendMail Custom Activity</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/sendmail-custom-activity.md)  
 <span data-ttu-id="3ea80-106">示範如何建立衍生自 <xref:System.Activities.AsyncCodeActivity> 的自訂活動，以使用 SMTP 來傳送郵件，供工作流程應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="3ea80-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="3ea80-107">節流平行 ForEach</span><span class="sxs-lookup"><span data-stu-id="3ea80-107">Throttled Parallel ForEach</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/throttled-parallel-foreach.md)  
 <span data-ttu-id="3ea80-108">示範 `ThrottleParallelForEach` 活動與 <xref:System.Activities.Statements.ParallelForEach%601> 活動如何類似，唯一的例外是它允許設定並行因數來限制同時執行的分支數目。</span><span class="sxs-lookup"><span data-stu-id="3ea80-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="3ea80-109">資料庫存取活動</span><span class="sxs-lookup"><span data-stu-id="3ea80-109">Database Access Activities</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md)  
 <span data-ttu-id="3ea80-110">示範如何建立活動，可讓您存取資料庫以擷取或修改資訊以及使用[ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081)來存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="3ea80-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
 [<span data-ttu-id="3ea80-111">.NET Framework 4.5 中的外顯化原則活動</span><span class="sxs-lookup"><span data-stu-id="3ea80-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="3ea80-112">示範 ExternalizedPolicy4 活動如何讓執行中的現有 Windows Workflow Foundation [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5)<xref:System.Workflow.Activities.Rules.RuleSet>物件中的 Windows Workflow foundation [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) 直接使用規則引擎也就是WF 3.5 隨附。</span><span class="sxs-lookup"><span data-stu-id="3ea80-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span> 
  
 [<span data-ttu-id="3ea80-113">非泛型 ForEach</span><span class="sxs-lookup"><span data-stu-id="3ea80-113">Non-Generic ForEach</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/non-generic-foreach.md)  
 <span data-ttu-id="3ea80-114">示範如何建立非泛型 <xref:System.Activities.Statements.ForEach%601> 活動版本。</span><span class="sxs-lookup"><span data-stu-id="3ea80-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="3ea80-115">非泛型 ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="3ea80-115">Non-Generic ParallelForEach</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/non-generic-parallelforeach.md)  
 <span data-ttu-id="3ea80-116">示範如何建立非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 活動版本。</span><span class="sxs-lookup"><span data-stu-id="3ea80-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="3ea80-117">取得 WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="3ea80-117">Get WorkflowInstanceId</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/get-workflowinstanceid.md)  
 <span data-ttu-id="3ea80-118">示範如何使用 `GetWorkflowInstanceId` 自訂活動傳回工作流程執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="3ea80-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
