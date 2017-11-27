---
title: "基本 TransactionScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e22b76a-76de-43b4-9be7-7a86ed3d5a44
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d4f9d9e966a0a6d8fa48d195b17438b3d78b32a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="basic-transactionscope"></a>基本 TransactionScope
這個範例包含四個案例，會示範如何巢狀處理 <xref:System.Activities.Statements.TransactionScope> 執行個體。 第一個案例會示範巢狀處理協力廠商活動，作者對於這個活動的結構並不清楚。 第二和第三個案例示範如何採用逾時，最後一個案例則示範 <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> 設定。  
  
## <a name="nesting-of-transactionscopeactivity"></a>巢狀處理 TransactionScopeActivity  
 第一個案例的工作流程是由兩個 <xref:System.Activities.Statements.WriteLine> 活動和一個 <xref:System.Activities.Statements.TransactionScope> 的序列所組成。 <xref:System.Activities.Statements.TransactionScope> 的主體為另外兩個 <xref:System.Activities.Statements.WriteLine> 活動、一個列印交易本機識別碼的自訂活動，以及協力廠商活動的序列。 協力廠商活動 `TransactionScopeTest` 包含 <xref:System.Activities.Statements.TransactionScope>，雖然工作流程作者對此不得而知。 這個案例會示範 <xref:System.Activities.Statements.TransactionScope> 活動可以進行巢狀處理。  
  
## <a name="time-outs"></a>逾時  
 第二個案例的工作流程與第一個案例幾乎完全相同。 `TransactionScopeTest` 已取代為 <xref:System.Activities.Statements.TransactionScope>。 <xref:System.Activities.Statements.TransactionScope> 的主體為五秒鐘延遲，而交易的逾時設為兩秒。 外部 <xref:System.Activities.Statements.TransactionScope> 的逾時設為 10 秒。 請注意，系統會採用範圍內最小的逾時，且交易會逾時。  
  
 第三個案例的工作流程與第二個案例幾乎完全相同。 延遲活動已從內部 <xref:System.Activities.Statements.TransactionScope> 的主體移至它在本身為外部 <xref:System.Activities.Statements.TransactionScope> 主體之序列中的正後方。 交易仍然會逾時，不過這是因為內部 <xref:System.Activities.Statements.TransactionScope> 的兩秒逾時不再適用。 交易會在超過外部 <xref:System.Activities.Statements.TransactionScope> 逾時的第 10 秒逾時。  
  
## <a name="aborting-on-transaction-failure"></a>交易失敗時中止  
 這個工作流程與案例三類似，不過逾時已被 <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> 屬性取代。 請注意，所有內部子系的旗標 (如果已設定) 都必須符合外部 <xref:System.Activities.Statements.TransactionScope>。 在這個案例中，這些旗標並不相符，因此會在工作流程開啟時擲回例外狀況。  
  
#### <a name="to-run-the-sample"></a>若要執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 BasicTransactionScopeSample.sln 方案。  
  
2.  若要建置此方案，請按 CTRL + SHIFT + B 或選取**建置方案**從**建置**功能表。  
  
3.  成功建置後，按 F5 或選取**開始偵錯**從**偵錯**功能表。 或者您可以按 CTRL + F5 或選取**啟動但不偵錯**從**偵錯**執行，而不偵錯 功能表。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\BasicTransactionScope`  
  
## <a name="see-also"></a>另請參閱
