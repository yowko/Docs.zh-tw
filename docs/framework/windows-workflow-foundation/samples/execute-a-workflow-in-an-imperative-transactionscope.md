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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 40a9e00659cad1dd2ab22b85f3ed15d958fd107b
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a>在命令性 TransactionScope 中執行工作流程
這個範例示範如何從命令式 C# 程式碼，在 <xref:System.Activities.WorkflowInvoker> 底下使用 <xref:System.Transactions.Transaction> 來執行工作流程。  
  
## <a name="sample-details"></a>範例詳細資料  
 在命令式 C# 程式碼中，<xref:System.Transactions.TransactionScope> 是用來封裝在相同交易下執行的一組工作。 <xref:System.Transactions.TransactionScope> 的運作方式是建立環境交易並初始化 <xref:System.Transactions.Transaction.Current%2A> 屬性，這個屬性可由執行於該執行緒的任何工作所存取。  
  
 若要在工作流程中取得對等行為，執行階段在執行每個活動之前必須執行初始化 <xref:System.Transactions.Transaction.Current%2A> 的額外工作，因為工作流程不會在活動之間維護執行緒相似性。 取得此執行階段支援之後，結果行為是，使用 <xref:System.Activities.WorkflowInvoker> 中的 <xref:System.Transactions.TransactionScope> 來執行工作流程時，所有活動一定會在 <xref:System.Transactions.TransactionScope> 所建立的環境交易內容中執行。  
  
 每個工作流程執行個體只能有一個環境交易；巢狀交易無法使用。 即使工作流程包含 <xref:System.Activities.Statements.TransactionScope> 活動，也不會建立新的內部交易， 而是重複使用工作流程外部建立的環境交易。  
  
 此範例開始新的 <xref:System.Transactions.TransactionScope>，列印交易識別碼，接著使用 <xref:System.Activities.WorkflowInvoker> 開始工作流程。 工作流程再次列印交易識別碼 (顯示這是相同交易)，接著執行 <xref:System.Activities.Statements.TransactionScope>，最後完成。 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 上的 <xref:System.Activities.WorkflowInvoker> 呼叫是同步的，因此原始執行緒會封鎖，直到工作流程完成為止。 一旦工作流程完成，交易也會完成，而且會處置資源。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 ImperativeTransactionSample.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按 F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`