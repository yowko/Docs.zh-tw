---
title: HOW TO：以 WorkflowServiceHost 設定工作流程服務的未處理例外狀況行為
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 69c6b1ce11d735181390a0c67df2f8dbea4f906c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185317"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>HOW TO：以 WorkflowServiceHost 設定工作流程服務的未處理例外狀況行為
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> 是一項行為，可讓您指定裝載於 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 的工作流程內發生未處理的例外狀況時，所採取的動作。 本主題示範如何組態檔中設定此行為。  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>若要設定 WorkflowUnhandledExceptionBehavior  
  
1. 在<>`workflowUnhandledException``behavior``serviceBehaviors`元素中<>元素中添加<>元素，使用 該`action`屬性指定在未處理異常發生時要執行的操作，如以下示例所示。  
  
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
    > 上述組態範例會使用簡化的組態。 有關詳細資訊，請參閱[簡化配置](../../../../docs/framework/wcf/simplified-configuration.md)。  
  
     此行為可以在程式碼中設定，如下列範例所示。  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <>`action``workflowUnhandledException`元素的屬性可以設置為以下值之一：  
  
     **放棄**  
     不改變永續性執行個體的狀態，放棄記憶體中的執行個體 (亦即，回復到上一次的永續點)。  
  
     **abandonAndSuspend**  
     放棄記憶體中的執行個體，並更新要暫停的永續執行個體。  
  
     **取消**  
     呼叫執行個體的取消處理常式，然後完成記憶體中的執行個體，該記憶體可能也會將執行個體從執行個體庫中移除。  
  
     **終止**  
     完成記憶體中的執行個體並將其從執行個體庫中移除。  
  
     有關 的詳細資訊<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>，請參閱[工作流服務主機擴充性](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)。  
  
## <a name="see-also"></a>另請參閱

- [工作流程服務主機擴充性](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [工作流服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)
