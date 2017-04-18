---
title: "HOW TO：以 WorkflowServiceHost 設定工作流程服務的未處理例外狀況行為 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# HOW TO：以 WorkflowServiceHost 設定工作流程服務的未處理例外狀況行為
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> 是一項行為，可讓您指定裝載於 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 的工作流程內發生未處理的例外狀況時，所採取的動作。本主題示範如何組態檔中設定此行為。  
  
### 若要設定 WorkflowUnhandledExceptionBehavior  
  
1.  在 \<`serviceBehaviors`\> 項目的 \<`behavior`\> 項目中，使用 `action` 屬性新增 \<`workflowUnhandledException`\> 項目，以指定當有無法處理的例外情況時要採取的動作，如下列範例所示。  
  
    ```  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    ```  
  
    > [!NOTE]
    >  上述組態範例會使用簡化的組態。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][簡化的組態](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     此行為可以在程式碼中設定，如下列範例所示。  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
  
    ```  
  
     \<`workflowUnhandledException`\> 項目的 `action` 屬性可設為下列其中一個值：  
  
     **abandon**  
     不改變永續性執行個體的狀態，放棄記憶體中的執行個體 \(亦即，回復到上一次的永續點\)。  
  
     **abandonAndSuspend**  
     放棄記憶體中的執行個體，並更新要暫停的永續執行個體。  
  
     **cancel**  
     呼叫執行個體的取消處理常式，然後完成記憶體中的執行個體，該記憶體可能也會將執行個體從執行個體庫中移除。  
  
     **terminate**  
     完成記憶體中的執行個體並將其從執行個體庫中移除。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> 的詳細資訊，請參閱[工作流程服務主機擴充性](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)。  
  
## 請參閱  
 [工作流程服務主機擴充性](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)   
 [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)