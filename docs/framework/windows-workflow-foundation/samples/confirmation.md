---
title: "組態 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8637aeaf-ac9e-49b8-93f4-da15dee45277
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 組態
這個範例示範四個有關 <xref:System.Activities.Statements.CompensableActivity> 和確認用法的一般案例。範例中會執行四個工作流程以示範確認。這個範例有宣告式和命令式版本。  
  
## 確認可補償的活動  
 第一個工作流程示範如何確認可補償的活動，它是由兩個 <xref:System.Activities.Statements.CompensableActivity> 執行個體的序列所組成。在第二個 <xref:System.Activities.Statements.CompensableActivity> 完成之後，確認活動會確認第一個活動。當工作流程順利完成時，所有尚未確認或未補償的 <xref:System.Activities.Statements.CompensableActivity> 執行個體都會依預設順序進行自動確認。如果沒有確認，則會先確認第二個 <xref:System.Activities.Statements.CompensableActivity>。  
  
## 明確補償  
 第二個案例示範在明確補償 <xref:System.Activities.Statements.CompensableActivity> 時，對預設確認所造成的影響。工作流程是由兩個 <xref:System.Activities.Statements.CompensableActivity> 活動的序列所組成，在第二個完成之後會明確補償第一個。因此當工作流程完成時，只確認第二個 <xref:System.Activities.Statements.CompensableActivity>。  
  
## 控制巢狀 CompensableActivity 活動的確認順序  
 第三個案例示範如何控制巢狀 <xref:System.Activities.Statements.CompensableActivity> 的確認順序。此案例包含 <xref:System.Activities.Statements.CompensableActivity> 做為工作流程的根活動。根 <xref:System.Activities.Statements.CompensableActivity> 的主體是三個 <xref:System.Activities.Statements.CompensableActivity> 的序列。根 <xref:System.Activities.Statements.CompensableActivity> 的 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 是序列，指定先確認第一個再確認第二個巢狀 <xref:System.Activities.Statements.CompensableActivity>。當工作流程完成時，會確認根 <xref:System.Activities.Statements.CompensableActivity>，接著由根活動依序確認第一個、第二個和第三個巢狀 <xref:System.Activities.Statements.CompensableActivity>。因此，預設確認順序基本上是反向。由於根 <xref:System.Activities.Statements.CompensableActivity> 中 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 未明確確認第三個 <xref:System.Activities.Statements.CompensableActivity>，因此依據預設順序確認它。但因為它是唯一未確認的 <xref:System.Activities.Statements.CompensableActivity>，這就表示它是已確認的。  
  
## 變數範圍  
 第四個案例示範當 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>、<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 或<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 處理常式執行時，即使活動已完成或工作流程已完成，對 <xref:System.Activities.Statements.CompensableActivity>定義之變數或其中一個變數父系的存留期仍在範圍中。工作流程包含兩個 <xref:System.Activities.Statements.CompensableActivity> 的序列。在第一個的主體中，`mySum` 變數設為 5 與 10 的總和，並列印結果。在第二個 <xref:System.Activities.Statements.CompensableActivity> 的主體中，此變數設為現有總和與 7 的總和，並列印結果。對第一個 <xref:System.Activities.Statements.CompensableActivity> 定義自訂確認處理常式，該處理常式會列印總和、減去 7，並再次列印總和。透過檢查列印總和，很清楚的知道，變數不只是在兩個 <xref:System.Activities.Statements.CompensableActivity> 的主體範圍中，也是在 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 的範圍中。  
  
#### 若要執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入方案。  
  
2.  執行 ConfirmationSample.exe 應用程式。  
  
3.  觀察下列輸出：  
  
 **Explicit confirmation:Start of workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: Confirmation HandlerEnd of workflowCompensableActivity2: Confirmation HandlerExplicit compensation:Start of workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: Compensation HandlerEnd of workflowCompensableActivity2: Confirmation HandlerCustom confirmation handler:Start of workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity3: BodyEnd of workflowCompensableActivity1: Confirmation HandlerCompensableActivity2: Confirmation HandlerCompensableActivity3: Confirmation HandlerVariable access in a confirmation handler:Start of workflowCompensableActivity1: BodyCompensableActivity1: The sum is: 15CompensableActivity2: BodyCompensableActivity2: Adding 7 to the sumCompensableActivity2: The sum is now: 22End of workflowCompensableActivity2: Confirmation HandlerCompensableActivity1: Confirmation HandlerCompensableActivity2: The sum is: 22CompensableActivity2: After subtracting 12 the sum is now: 10Press ENTER to exit.**  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\Confirmation`  
  
## 請參閱