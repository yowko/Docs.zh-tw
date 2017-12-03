---
title: "HOW TO：以 WorkflowServiceHost 設定追蹤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42b5621275b9d27983619d18990e3d8e22c4e9db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>HOW TO：以 WorkflowServiceHost 設定追蹤
本主題說明如何設定裝載於 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 之 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 工作流程的追蹤。 此追蹤是透過 Web.config 檔案指定服務行為而設定的。  
  
### <a name="configure-tracking-in-configuration"></a>在組態中設定追蹤  
  
1.  您可以使用組態檔中的 <<xref:System.Activities.Tracking.EtwTrackingParticipant>> 項目來加入 `behavior`，如下列範例所示。  
  
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
    >  上述組態範例會使用簡化的組態。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][簡化組態](../../../../docs/framework/wcf/simplified-configuration.md)。  
  
     上述組態範例會加入 <xref:System.Activities.Tracking.EtwTrackingParticipant> 並指定追蹤設定檔名稱。 追蹤設定檔是在 <`trackingProfile`> 內的 <`tracking`> 項目中建立的。 追蹤設定檔包含有追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。 下列範例示範如何建立追蹤設定檔。  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]追蹤設定檔，請參閱[追蹤設定檔](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]追蹤在一般情況下，請參閱[工作流程追蹤](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)。  
  
### <a name="configure-tracking-in-code"></a>在程式碼中設定追蹤  
  
1.  您可以使用程式碼中的 <xref:System.Activities.Tracking.EtwTrackingParticipant> 行為來加入 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>，如下列範例所示。  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     上述程式碼範例會加入 <xref:System.Activities.Tracking.EtwTrackingParticipant> 並指定追蹤設定檔名稱。 追蹤設定檔是在 <`trackingProfile`> 項目內的 <`tracking`> 項目中建立的，如上一節所示。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]追蹤設定檔，請參閱[追蹤設定檔](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]追蹤在一般情況下，請參閱[工作流程追蹤](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)。 如需設定追蹤以程式設計方式的範例，請參閱[流程設定追蹤](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。  
  
## <a name="see-also"></a>另請參閱  
 [WCF 服務的簡化的組態](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)  
 [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [追蹤設定檔](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
