---
title: 取得 WorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: fbfaf52931345571e5125200fe467dcc098b9dc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513902"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="3f4c9-102">取得 WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="3f4c9-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="3f4c9-103">這個範例示範如何使用 `GetWorkflowInstanceId` 自訂活動傳回工作流程執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="3f4c9-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3f4c9-104">示範</span><span class="sxs-lookup"><span data-stu-id="3f4c9-104">Demonstrates</span></span>  
 <span data-ttu-id="3f4c9-105">自訂活動部署、如何存取工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f4c9-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="3f4c9-106">討論</span><span class="sxs-lookup"><span data-stu-id="3f4c9-106">Discussion</span></span>  
 <span data-ttu-id="3f4c9-107">取得執行中工作流程的執行個體識別碼，需要撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="3f4c9-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="3f4c9-108">如果您想要撰寫完整宣告的工作流程，需要可傳回工作流程執行個體識別碼的活動，以便在工作流程中參考活動以提供完整宣告的工作流程撰寫經驗。</span><span class="sxs-lookup"><span data-stu-id="3f4c9-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="3f4c9-109">許多案例需要存取執行個體識別碼：一些範例包含記錄或稽核用途，或透過提供執行個體識別碼給用戶端供未來關聯 (例如在 SendReply 活動中使用這個活動) 來執行應用程式層級相互關聯。</span><span class="sxs-lookup"><span data-stu-id="3f4c9-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="3f4c9-110">`GetWorkflowInstanceId` 是實作為 <xref:System.Activities.CodeActivity%601>，因為它必須傳回 <xref:System.Guid> 類型的值，而且必須存取 <xref:System.Activities.CodeActivityContext> 以取得工作流程的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="3f4c9-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="3f4c9-111">這是相當基本的實作。</span><span class="sxs-lookup"><span data-stu-id="3f4c9-111">Its implementation is fairly basic.</span></span>  
  
```  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
protected override Guid Execute(CodeActivityContext context)  
        {  
            return context.WorkflowInstanceId;  
        }  
}  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="3f4c9-112">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="3f4c9-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3f4c9-113">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="3f4c9-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3f4c9-114">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="3f4c9-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3f4c9-115">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="3f4c9-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
