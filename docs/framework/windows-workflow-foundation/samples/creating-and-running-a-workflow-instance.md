---
title: 建立與執行工作流程執行個體
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: 571d41194ebc98be81646fb5bfdab060225015ca
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44705488"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="fa81f-102">建立與執行工作流程執行個體</span><span class="sxs-lookup"><span data-stu-id="fa81f-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="fa81f-103">這個範例示範如何執行工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="fa81f-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="fa81f-104">範例中會示範如何以同步和非同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="fa81f-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="fa81f-105">示範</span><span class="sxs-lookup"><span data-stu-id="fa81f-105">Demonstrates</span></span>  
 <span data-ttu-id="fa81f-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="fa81f-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="fa81f-107">討論</span><span class="sxs-lookup"><span data-stu-id="fa81f-107">Discussion</span></span>  
 <span data-ttu-id="fa81f-108">範例的第一個部分會使用 <xref:System.Activities.WorkflowInvoker.Invoke%2A>。</span><span class="sxs-lookup"><span data-stu-id="fa81f-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="fa81f-109">這是執行工作流程的最基本方式。</span><span class="sxs-lookup"><span data-stu-id="fa81f-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="fa81f-110">使用 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 執行的工作流程會以同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="fa81f-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="fa81f-111">範例的第二部分使用 <xref:System.Activities.WorkflowApplication> 類別。</span><span class="sxs-lookup"><span data-stu-id="fa81f-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="fa81f-112"><xref:System.Activities.WorkflowApplication> 可讓您更充分掌控每一個執行個體，包括與執行中工作流程進行互動以及透過非同步方式執行工作流程的能力。</span><span class="sxs-lookup"><span data-stu-id="fa81f-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fa81f-113">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="fa81f-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fa81f-114">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="fa81f-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fa81f-115">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="fa81f-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fa81f-116">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="fa81f-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="fa81f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa81f-117">See Also</span></span>  
 [<span data-ttu-id="fa81f-118">使用 WorkflowInvoker 與 WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="fa81f-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
