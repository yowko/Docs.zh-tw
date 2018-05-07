---
title: 異動回復
ms.date: 03/30/2017
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
ms.openlocfilehash: 15333b159625f07449b0a93634a1a9a854614a57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-rollback"></a>異動回復
這個範例示範如何建立自訂 <xref:System.Activities.NativeActivity>，用來存取環境 <xref:System.Activities.RuntimeTransactionHandle> 以取得環境交易並明確回復此交易。  
  
## <a name="sample-details"></a>範例詳細資料  
 在工作流程中，當最外層的 <xref:System.Activities.Statements.TransactionScope> 或 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 完成時，交易就自動完成。  當未處理的例外狀況跨範圍界限傳播時，交易會隱含回復。 不過，有時候，明確回復交易而不需擲回例外狀況是合理的。 在此情況下，您可以使用自訂回復活動 (如本範例所述)，明確中止環境交易並提供選擇性的例外狀況原因。  
  
 `RollbackActivity` 是 <xref:System.Activities.NativeActivity>，因為它需要存取執行屬性以取得環境 <xref:System.Activities.RuntimeTransactionHandle>。 在 `Execute` 方法中，它會取得 <xref:System.Activities.RuntimeTransactionHandle> 並檢查是否為 `null`，表示使用活動時未搭配環境執行階段交易。 接著取得交易，再次檢查 `null` 是否存在。 可能有環境 <xref:System.Activities.RuntimeTransactionHandle>，但從未初始化執行階段交易。 最後，它會呼叫 <xref:System.Transactions.Transaction.Rollback%2A> 並指定使用者提供的例外狀況或泛型例外狀況，表示活動回復交易，藉以中止交易。  
  
 示範工作流程是由 <xref:System.Activities.Statements.TransactionScope> 所組成，其主體會在 `RollbackActivity` 執行前後列印交易狀態。 請注意，即使交易已經回復，<xref:System.Activities.Statements.TransactionScope> 也會執行完成，在主體完成之前不會中止工作流程。 工作流程之所以中止，是因為 <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> 屬性預設為 `true`。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入 TransactionRollback.sln 方案。  
  
2.  按下 CTRL+SHIFT+B 以建置方案。  
  
3.  按 CTRL+F5 執行應用程式。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a>另請參閱  
 [異動](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
