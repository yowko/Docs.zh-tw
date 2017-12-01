---
title: "自動確認模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 668aec65-78d3-4636-9c7b-deed643a18f9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: affc9d1638148971dd9c57969c75166facfd545c
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="auto-confirm-pattern"></a>自動確認模式
這個範例包含三個狀況，其執行示範自訂 `AutoConfirmScope` 活動。 第一個範例顯示四個可補償活動的序列成功執行，其中第二個和第三個可補償活動以巢狀方式置於 `AutoConfirmScope` 中。 第二個範例顯示相同序列，但在第四個 <xref:System.Activities.Statements.CompensableActivity> 執行後發生例外狀況。 第三個狀況顯示相同序列，但在第二個  `AutoConfirmScope` 完成後於 <xref:System.Activities.Statements.CompensableActivity> 中發生例外狀況。  
  
 此範例示範在範圍成功完成時確認所有可補償子活動的自動確認模式。 此模式定義所有可補償子活動的存留期間，因為它們不再補償或確認。  
  
 範圍是由 <xref:System.Activities.Statements.TryCatch> 組成，其中 <xref:System.Activities.Statements.TryCatch.Try%2A> 為內部 <xref:System.Activities.Statements.CompensableActivity>。 使用者指定的 `AutoConfirmScope` 主體是內部 <xref:System.Activities.Statements.CompensableActivity> 的主體。 當這個內部 <xref:System.Activities.Statements.CompensableActivity> 完成時，它會產生 <xref:System.Activities.Statements.CompensationToken> 做為 out 引數。 `AutoConfirmScope` 使用 <xref:System.Activities.Statements.TryCatch.Finally%2A> 檢查語彙基元是否已產生，如果有的話，則會確認內部 <xref:System.Activities.Statements.CompensableActivity>。 內部 <xref:System.Activities.Statements.CompensableActivity> 會針對其主體中可能存在的任何可補償活動叫用預設補償。  
  
 第一個狀況顯示工作流程的成功執行，並示範當工作流程完成且第一個和第四個可補償活動確認時，第二個和第三個可補償活動已確認。 這產生三、二、四和一的確認順序。  
  
 第二個狀況在四個可補償活動完成之後顯示例外狀況。 因為可補償活動二和三已確認，它們不受影響，但一和四已補償。 這會產生確認三、確認二、補償四和補償一。  
  
 最終狀況顯示 `AutoConfirmScope` 的不成功執行。 在這個狀況中，在第二個 <xref:System.Activities.Statements.CompensableActivity> 完成之後發生例外狀況。 因為第三個和第四個可補償活動尚未執行，它們不受影響。 因為範圍未成功完成，所以第二個 <xref:System.Activities.Statements.CompensableActivity> 未確認。 這產生二和一的補償順序。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 AutoConfirmSample.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Compensation\AutoConfirm`