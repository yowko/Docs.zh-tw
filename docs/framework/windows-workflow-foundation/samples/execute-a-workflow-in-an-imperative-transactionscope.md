---
title: "在命令性 TransactionScope 中執行工作流程"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 530a590931a1cb3994406e5605f8da2853ceddaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a><span data-ttu-id="f20d0-102">在命令性 TransactionScope 中執行工作流程</span><span class="sxs-lookup"><span data-stu-id="f20d0-102">Execute a Workflow in an Imperative TransactionScope</span></span>
<span data-ttu-id="f20d0-103">這個範例示範如何從命令式 C# 程式碼，在 <xref:System.Activities.WorkflowInvoker> 底下使用 <xref:System.Transactions.Transaction> 來執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="f20d0-103">This sample shows how to execute a workflow using <xref:System.Activities.WorkflowInvoker> under a <xref:System.Transactions.Transaction> from imperative C# code.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="f20d0-104">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="f20d0-104">Sample Details</span></span>  
 <span data-ttu-id="f20d0-105">在命令式 C# 程式碼中，<xref:System.Transactions.TransactionScope> 是用來封裝在相同交易下執行的一組工作。</span><span class="sxs-lookup"><span data-stu-id="f20d0-105">In imperative C# code, the <xref:System.Transactions.TransactionScope> is used to encapsulate a set of work that executes under the same transaction.</span></span> <span data-ttu-id="f20d0-106"><xref:System.Transactions.TransactionScope> 的運作方式是建立環境交易並初始化 <xref:System.Transactions.Transaction.Current%2A> 屬性，這個屬性可由執行於該執行緒的任何工作所存取。</span><span class="sxs-lookup"><span data-stu-id="f20d0-106">The <xref:System.Transactions.TransactionScope> works by creating an ambient transaction and initializing the <xref:System.Transactions.Transaction.Current%2A> property, which can then be accessed by any work being executed on that thread.</span></span>  
  
 <span data-ttu-id="f20d0-107">若要在工作流程中取得對等行為，執行階段在執行每個活動之前必須執行初始化 <xref:System.Transactions.Transaction.Current%2A> 的額外工作，因為工作流程不會在活動之間維護執行緒相似性。</span><span class="sxs-lookup"><span data-stu-id="f20d0-107">To get equivalent behavior in workflow, the runtime has to do the extra work of initializing <xref:System.Transactions.Transaction.Current%2A> before executing each activity because a workflow does not maintain thread affinity between activities.</span></span> <span data-ttu-id="f20d0-108">取得此執行階段支援之後，結果行為是，使用 <xref:System.Activities.WorkflowInvoker> 中的 <xref:System.Transactions.TransactionScope> 來執行工作流程時，所有活動一定會在 <xref:System.Transactions.TransactionScope> 所建立的環境交易內容中執行。</span><span class="sxs-lookup"><span data-stu-id="f20d0-108">With this runtime support, the resulting behavior is that when executing a workflow with <xref:System.Activities.WorkflowInvoker> inside a <xref:System.Transactions.TransactionScope>, all activities are guaranteed to run under the context of the ambient transaction created by the <xref:System.Transactions.TransactionScope>.</span></span>  
  
 <span data-ttu-id="f20d0-109">每個工作流程執行個體只能有一個環境交易；巢狀交易無法使用。</span><span class="sxs-lookup"><span data-stu-id="f20d0-109">A workflow can have only a single ambient transaction for each workflow instance; nested transactions are not available.</span></span> <span data-ttu-id="f20d0-110">即使工作流程包含 <xref:System.Activities.Statements.TransactionScope> 活動，也不會建立新的內部交易，</span><span class="sxs-lookup"><span data-stu-id="f20d0-110">Even if the workflow contains a <xref:System.Activities.Statements.TransactionScope> activity, this does not create a new inner transaction.</span></span> <span data-ttu-id="f20d0-111">而是重複使用工作流程外部建立的環境交易。</span><span class="sxs-lookup"><span data-stu-id="f20d0-111">Instead, this reuses the ambient transaction that was created outside the workflow.</span></span>  
  
 <span data-ttu-id="f20d0-112">此範例開始新的 <xref:System.Transactions.TransactionScope>，列印交易識別碼，接著使用 <xref:System.Activities.WorkflowInvoker> 開始工作流程。</span><span class="sxs-lookup"><span data-stu-id="f20d0-112">The sample begins a new <xref:System.Transactions.TransactionScope>, prints the transaction ID and begins a workflow using <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="f20d0-113">工作流程再次列印交易識別碼 (顯示這是相同交易)，接著執行 <xref:System.Activities.Statements.TransactionScope>，最後完成。</span><span class="sxs-lookup"><span data-stu-id="f20d0-113">The workflow prints the transaction ID again, showing that it is the same transaction, then runs a <xref:System.Activities.Statements.TransactionScope>, then completes.</span></span> <span data-ttu-id="f20d0-114"><xref:System.Activities.WorkflowInvoker.Invoke%2A> 上的 <xref:System.Activities.WorkflowInvoker> 呼叫是同步的，因此原始執行緒會封鎖，直到工作流程完成為止。</span><span class="sxs-lookup"><span data-stu-id="f20d0-114">The <xref:System.Activities.WorkflowInvoker.Invoke%2A> call on <xref:System.Activities.WorkflowInvoker> is synchronous so the original thread blocks until the workflow completes.</span></span> <span data-ttu-id="f20d0-115">一旦工作流程完成，交易也會完成，而且會處置資源。</span><span class="sxs-lookup"><span data-stu-id="f20d0-115">Once the workflow is complete, the transaction is completed and resources disposed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f20d0-116">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="f20d0-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="f20d0-117">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 ImperativeTransactionSample.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="f20d0-117">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ImperativeTransactionSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f20d0-118">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="f20d0-118">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f20d0-119">若要執行此方案，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="f20d0-119">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f20d0-120">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="f20d0-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f20d0-121">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="f20d0-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f20d0-122">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="f20d0-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f20d0-123">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="f20d0-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`