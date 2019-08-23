---
title: 作法：以 WorkflowServiceHost 設定追蹤
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 5781878270272f5ef894c68dc23b9433029e1d41
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968498"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>作法：以 WorkflowServiceHost 設定追蹤
本主題說明如何設定裝載於 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 之 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 工作流程的追蹤。 此追蹤是透過 Web.config 檔案指定服務行為而設定的。  
  
### <a name="configure-tracking-in-configuration"></a>在組態中設定追蹤  
  
1. 使用設定檔中的`behavior`< > 元素新增, 如下列範例所示。 <xref:System.Activities.Tracking.EtwTrackingParticipant>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>              
       </serviceBehaviors>  
    <behaviors>  
    ```  
  
    > [!NOTE]
    > 上述組態範例會使用簡化的組態。 如需詳細資訊, 請參閱[簡化](../../../../docs/framework/wcf/simplified-configuration.md)的設定。  
  
     上述組態範例會加入 <xref:System.Activities.Tracking.EtwTrackingParticipant> 並指定追蹤設定檔名稱。 追蹤設定檔是在 <`trackingProfile` `tracking`> 專案中的 < > 元素中建立。 追蹤設定檔包含有追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。 下列範例示範如何建立追蹤設定檔。  
  
    ```xml  
    <system.serviceModel>  
        <tracking>   
         <trackingProfile name="Sample Tracking Profile">  
            <workflow activityDefinitionId="*">  
               <workflowInstanceQueries>  
                 <workflowInstanceQuery>  
                    <states>  
                       <state name="Started"/>  
                       <state name="Completed"/>  
                    </states>  
                </workflowInstanceQuery>  
             </workflowInstanceQueries>  
           </workflow>  
         </trackingProfile>   
       </tracking>  
    </system.serviceModel>  
    ```  
  
     如需追蹤設定檔的詳細資訊, 請參閱[追蹤設定檔](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。  
  
     如需一般追蹤的詳細資訊, 請參閱[工作流程追蹤和追蹤](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)。  
  
### <a name="configure-tracking-in-code"></a>在程式碼中設定追蹤  
  
1. 您可以使用程式碼中的 <xref:System.Activities.Tracking.EtwTrackingParticipant> 行為來加入 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>，如下列範例所示。  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     上述程式碼範例會加入 <xref:System.Activities.Tracking.EtwTrackingParticipant> 並指定追蹤設定檔名稱。 追蹤設定檔會建立在 <`trackingProfile` `tracking`> 專案中的 < > 元素內, 如上一節所示。  
  
     如需追蹤設定檔的詳細資訊, 請參閱[追蹤設定檔](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。  
  
     如需一般追蹤的詳細資訊, 請參閱[工作流程追蹤和追蹤](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)。 如需以程式設計方式設定追蹤的範例, 請參閱設定[工作流程的追蹤](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。  
  
## <a name="see-also"></a>另請參閱

- [WCF 服務的簡化組態](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [追蹤設定檔](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
