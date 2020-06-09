---
title: HOW TO：以 WorkflowServiceHost 設定工作流程服務的未處理例外狀況行為
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 3881d1af21dcc0c211c6738162360e522648d949
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593590"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>HOW TO：以 WorkflowServiceHost 設定工作流程服務的未處理例外狀況行為
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> 是一項行為，可讓您指定裝載於 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 的工作流程內發生未處理的例外狀況時，所採取的動作。 本主題示範如何組態檔中設定此行為。  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>若要設定 WorkflowUnhandledExceptionBehavior  
  
1. `workflowUnhandledException`在 <> 專案內的 <> 專案中加入 <> 專案 `behavior` `serviceBehaviors` ，使用 `action` 屬性指定未處理的例外狀況發生時所採取的動作，如下列範例所示。  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > 上述組態範例會使用簡化的組態。 如需詳細資訊，請參閱[簡化](../simplified-configuration.md)的設定。  
  
     此行為可以在程式碼中設定，如下列範例所示。  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action`<> 元素的屬性 `workflowUnhandledException` 可以設定為下列其中一個值：  
  
     **放棄**  
     不改變永續性執行個體的狀態，放棄記憶體中的執行個體 (亦即，回復到上一次的永續點)。  
  
     **abandonAndSuspend**  
     放棄記憶體中的執行個體，並更新要暫停的永續執行個體。  
  
     **cancel**  
     呼叫執行個體的取消處理常式，然後完成記憶體中的執行個體，該記憶體可能也會將執行個體從執行個體庫中移除。  
  
     **終止**  
     完成記憶體中的執行個體並將其從執行個體庫中移除。  
  
     如需的詳細資訊 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> ，請參閱[工作流程服務主機](workflow-service-host-extensibility.md)擴充性。  
  
## <a name="see-also"></a>請參閱

- [工作流程服務主機擴充性](workflow-service-host-extensibility.md)
- [工作流程服務](workflow-services.md)
