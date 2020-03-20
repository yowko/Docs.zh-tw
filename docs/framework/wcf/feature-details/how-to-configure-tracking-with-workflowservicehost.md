---
title: HOW TO：以 WorkflowServiceHost 設定追蹤
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 962dfda9fc5780cc3ac7211464bb3a9be8b7fa90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185062"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>HOW TO：以 WorkflowServiceHost 設定追蹤
本主題說明如何設定裝載於 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 之 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 工作流程的追蹤。 此追蹤是透過 Web.config 檔案指定服務行為而設定的。  
  
### <a name="configure-tracking-in-configuration"></a>在組態中設定追蹤  
  
1. 在<xref:System.Activities.Tracking.EtwTrackingParticipant>設定檔中添加使用`behavior`<>元素，如以下示例所示。  
  
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
    > 上述組態範例會使用簡化的組態。 有關詳細資訊，請參閱[簡化配置](../../../../docs/framework/wcf/simplified-configuration.md)。  
  
     上述組態範例會加入 <xref:System.Activities.Tracking.EtwTrackingParticipant> 並指定追蹤設定檔名稱。 跟蹤設定檔在<>`trackingProfile``tracking`元素中<>元素中創建。 追蹤設定檔包含有追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。 下列範例示範如何建立追蹤設定檔。  
  
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
  
     有關跟蹤設定檔的詳細資訊，請參閱[跟蹤設定檔](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。  
  
     有關跟蹤的詳細資訊，請參閱[工作流跟蹤和跟蹤](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)。  
  
### <a name="configure-tracking-in-code"></a>在程式碼中設定追蹤  
  
1. 您可以使用程式碼中的 <xref:System.Activities.Tracking.EtwTrackingParticipant> 行為來加入 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>，如下列範例所示。  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     上述程式碼範例會加入 <xref:System.Activities.Tracking.EtwTrackingParticipant> 並指定追蹤設定檔名稱。 跟蹤設定檔在<>`trackingProfile``tracking`元素<>元素中創建，如上一節所示。  
  
     有關跟蹤設定檔的詳細資訊，請參閱[跟蹤設定檔](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。  
  
     有關跟蹤的詳細資訊，請參閱[工作流跟蹤和跟蹤](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)。 有關以程式設計方式配置跟蹤的示例，請參閱[配置工作流跟蹤](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。  
  
## <a name="see-also"></a>另請參閱

- [WCF 服務的簡化組態](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [工作流服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [追蹤設定檔](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
