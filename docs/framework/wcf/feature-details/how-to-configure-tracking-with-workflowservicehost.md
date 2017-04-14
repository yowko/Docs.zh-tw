---
title: "HOW TO：以 WorkflowServiceHost 設定追蹤 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# HOW TO：以 WorkflowServiceHost 設定追蹤
本主題說明如何設定裝載於 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 之 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 工作流程的追蹤。  此追蹤是透過 Web.config 檔案指定服務行為而設定的。  
  
### 在組態中設定追蹤  
  
1.  您可以使用組態檔中的 \<`behavior`\> 項目來加入 <xref:System.Activities.Tracking.EtwTrackingParticipant>，如下列範例所示。  
  
    ```  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>              
       </serviceBehaviors>  
    <behaviors>  
  
    ```  
  
    > [!NOTE]
    >  上述組態範例會使用簡化的組態。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [簡化的組態](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     上述組態範例會加入 <xref:System.Activities.Tracking.EtwTrackingParticipant> 並指定追蹤設定檔名稱。  追蹤設定檔是在 \<`tracking`\> 內的 \<`trackingProfile`\> 項目中建立的。  追蹤設定檔包含有追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。  下列範例示範如何建立追蹤設定檔。  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]追蹤設定檔的詳細資訊，請參閱[追蹤設定檔](../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]一般追蹤的詳細資訊，請參閱[工作流程追蹤與追查](../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)。  
  
### 在程式碼中設定追蹤  
  
1.  您可以使用程式碼中的 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> 行為來加入 <xref:System.Activities.Tracking.EtwTrackingParticipant>，如下列範例所示。  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     上述程式碼範例會加入 <xref:System.Activities.Tracking.EtwTrackingParticipant> 並指定追蹤設定檔名稱。  追蹤設定檔是在 \<`tracking`\> 項目內的 \<`trackingProfile`\> 項目中建立的，如上一節所示。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]追蹤設定檔的詳細資訊，請參閱[追蹤設定檔](../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]一般追蹤的詳細資訊，請參閱[工作流程追蹤與追查](../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)。  如需以程式設計方式設定追蹤的範例，請參閱[設定工作流程的追蹤](../../../../docs/framework/windows-workflow-foundation//configuring-tracking-for-a-workflow.md)。  
  
## 請參閱  
 [WCF 服務的簡化組態](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)   
 [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [追蹤設定檔](../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)