---
title: "取得 WorkflowInstanceId | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 取得 WorkflowInstanceId
這個範例示範如何使用 `GetWorkflowInstanceId` 自訂活動傳回工作流程執行個體識別碼。  
  
## 示範  
 自訂活動部署、如何存取工作流程執行個體。  
  
## 討論  
 取得執行中工作流程的執行個體識別碼，需要撰寫程式碼。如果您想要撰寫完整宣告的工作流程，需要可傳回工作流程執行個體識別碼的活動，以便在工作流程中參考活動以提供完整宣告的工作流程撰寫經驗。許多案例需要存取執行個體識別碼：一些範例包含記錄或稽核用途，或透過提供執行個體識別碼給用戶端供未來關聯 \(例如在 SendReply 活動中使用這個活動\) 來執行應用程式層級相互關聯。  
  
 `GetWorkflowInstanceId` 是實作為 <xref:System.Activities.CodeActivity%601>，因為它必須傳回 <xref:System.Guid> 類型的值，而且必須存取 <xref:System.Activities.CodeActivityContext> 以取得工作流程的執行個體識別碼。這是相當基本的實作。  
  
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
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`