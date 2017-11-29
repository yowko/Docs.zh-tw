---
title: "異動回復"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 654f0e46dc5ec5d40588f8571e8f31d04184bc4d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-rollback"></a><span data-ttu-id="38f39-102">異動回復</span><span class="sxs-lookup"><span data-stu-id="38f39-102">Transaction Rollback</span></span>
<span data-ttu-id="38f39-103">這個範例示範如何建立自訂 <xref:System.Activities.NativeActivity>，用來存取環境 <xref:System.Activities.RuntimeTransactionHandle> 以取得環境交易並明確回復此交易。</span><span class="sxs-lookup"><span data-stu-id="38f39-103">This sample shows how to create a custom <xref:System.Activities.NativeActivity> that accesses the ambient <xref:System.Activities.RuntimeTransactionHandle> to get the ambient transaction and explicitly roll it back.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="38f39-104">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="38f39-104">Sample Details</span></span>  
 <span data-ttu-id="38f39-105">在工作流程中，當最外層的 <xref:System.Activities.Statements.TransactionScope> 或 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 完成時，交易就自動完成。</span><span class="sxs-lookup"><span data-stu-id="38f39-105">In workflow, a transaction is automatically completed when the outermost <xref:System.Activities.Statements.TransactionScope> or <xref:System.ServiceModel.Activities.TransactedReceiveScope> completes.</span></span>  <span data-ttu-id="38f39-106">當未處理的例外狀況跨範圍界限傳播時，交易會隱含回復。</span><span class="sxs-lookup"><span data-stu-id="38f39-106">A transaction implicitly rolls back when an unhandled exception propagates across the scope boundary.</span></span> <span data-ttu-id="38f39-107">不過，有時候，明確回復交易而不需擲回例外狀況是合理的。</span><span class="sxs-lookup"><span data-stu-id="38f39-107">However, there may be times when it makes sense to explicitly roll back a transaction without having to throw an exception.</span></span> <span data-ttu-id="38f39-108">在此情況下，您可以使用自訂回復活動 (如本範例所述)，明確中止環境交易並提供選擇性的例外狀況原因。</span><span class="sxs-lookup"><span data-stu-id="38f39-108">In this case, you can use the custom rollback activity like the one in this sample to explicitly abort the ambient transaction and provide an optional exception reason.</span></span>  
  
 <span data-ttu-id="38f39-109">`RollbackActivity` 是 <xref:System.Activities.NativeActivity>，因為它需要存取執行屬性以取得環境 <xref:System.Activities.RuntimeTransactionHandle>。</span><span class="sxs-lookup"><span data-stu-id="38f39-109">The `RollbackActivity` is a <xref:System.Activities.NativeActivity> as it requires access to the execution properties to get the ambient <xref:System.Activities.RuntimeTransactionHandle>.</span></span> <span data-ttu-id="38f39-110">在 `Execute` 方法中，它會取得 <xref:System.Activities.RuntimeTransactionHandle> 並檢查是否為 `null`，表示使用活動時未搭配環境執行階段交易。</span><span class="sxs-lookup"><span data-stu-id="38f39-110">In the `Execute` method, it obtains the <xref:System.Activities.RuntimeTransactionHandle> and checks whether it is `null`, which indicates that the activity was used without an ambient run-time transaction.</span></span> <span data-ttu-id="38f39-111">接著取得交易，再次檢查 `null` 是否存在。</span><span class="sxs-lookup"><span data-stu-id="38f39-111">It then obtains the transaction, again checking whether `null` is present.</span></span> <span data-ttu-id="38f39-112">可能有環境 <xref:System.Activities.RuntimeTransactionHandle>，但從未初始化執行階段交易。</span><span class="sxs-lookup"><span data-stu-id="38f39-112">It is possible to have an ambient <xref:System.Activities.RuntimeTransactionHandle> without ever initializing a run-time transaction.</span></span> <span data-ttu-id="38f39-113">最後，它會呼叫 <xref:System.Transactions.Transaction.Rollback%2A> 並指定使用者提供的例外狀況或泛型例外狀況，表示活動回復交易，藉以中止交易。</span><span class="sxs-lookup"><span data-stu-id="38f39-113">Finally it aborts the transaction by calling <xref:System.Transactions.Transaction.Rollback%2A> and specifying either a user-provided exception or a generic exception that states that the activity rolled back the transaction.</span></span>  
  
 <span data-ttu-id="38f39-114">示範工作流程是由 <xref:System.Activities.Statements.TransactionScope> 所組成，其主體會在 `RollbackActivity` 執行前後列印交易狀態。</span><span class="sxs-lookup"><span data-stu-id="38f39-114">The demonstration workflow consists of a <xref:System.Activities.Statements.TransactionScope> whose body prints the transaction status before and after the `RollbackActivity` executes.</span></span> <span data-ttu-id="38f39-115">請注意，即使交易已經回復，<xref:System.Activities.Statements.TransactionScope> 也會執行完成，在主體完成之前不會中止工作流程。</span><span class="sxs-lookup"><span data-stu-id="38f39-115">Note that even though the transaction has been rolled back, the <xref:System.Activities.Statements.TransactionScope> executes to completion and does not abort the workflow until the body completes.</span></span> <span data-ttu-id="38f39-116">工作流程之所以中止，是因為 <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> 屬性預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="38f39-116">The workflow is aborted because the <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> property defaults to `true`.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="38f39-117">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="38f39-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="38f39-118">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入 TransactionRollback.sln 方案。</span><span class="sxs-lookup"><span data-stu-id="38f39-118">Load the TransactionRollback.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="38f39-119">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="38f39-119">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="38f39-120">按 CTRL+F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="38f39-120">Press CTRL+F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="38f39-121">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="38f39-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="38f39-122">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="38f39-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="38f39-123">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="38f39-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="38f39-124">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="38f39-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a><span data-ttu-id="38f39-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38f39-125">See Also</span></span>  
 [<span data-ttu-id="38f39-126">異動</span><span class="sxs-lookup"><span data-stu-id="38f39-126">Transactions</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
