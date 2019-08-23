---
title: 作法：以 WorkflowServiceHost 設定工作流程的未處理例外狀況行為
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: aec2fd80e10ae1959b29c0883d51c4045517d792
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957264"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>作法：以 WorkflowServiceHost 設定工作流程的未處理例外狀況行為
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> 是一項行為，可讓您指定裝載於 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 的工作流程內發生未處理的例外狀況時，所採取的動作。 本主題示範如何組態檔中設定此行為。  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>若要設定 WorkflowUnhandledExceptionBehavior  
  
1. `workflowUnhandledException`在 <`behavior` `action` > 專案內的 < > 專案中加入 < > 專案, 使用屬性指定未處理的例外狀況發生時所採取的動作, 如下列範例所示。`serviceBehaviors`  
  
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
    > 上述組態範例會使用簡化的組態。 如需詳細資訊, 請參閱[簡化](../../../../docs/framework/wcf/simplified-configuration.md)的設定。  
  
     此行為可以在程式碼中設定，如下列範例所示。  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action` <`workflowUnhandledException`> 元素的屬性可以設定為下列其中一個值:  
  
     **放棄**  
     不改變永續性執行個體的狀態，放棄記憶體中的執行個體 (亦即，回復到上一次的永續點)。  
  
     **abandonAndSuspend**  
     放棄記憶體中的執行個體，並更新要暫停的永續執行個體。  
  
     **取消**  
     呼叫執行個體的取消處理常式，然後完成記憶體中的執行個體，該記憶體可能也會將執行個體從執行個體庫中移除。  
  
     **terminate**  
     完成記憶體中的執行個體並將其從執行個體庫中移除。  
  
     如需的詳細<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>資訊, 請參閱[工作流程服務主機](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)擴充性。  
  
## <a name="see-also"></a>另請參閱

- [工作流程服務主機擴充性](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)
