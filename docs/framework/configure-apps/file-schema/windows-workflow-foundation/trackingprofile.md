---
title: "&lt;trackingProfile&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;trackingProfile&gt;
代表組態區段，這個區段用於建立訂閱追蹤參與者中的工作流程追蹤記錄。  追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。  追蹤設定檔區段中定義的查詢會定義訂閱所傳回的事件類型。  
  
 如需在工作流程追蹤和其設定的詳細資訊，請參閱[工作流程追蹤與追查](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)和[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)。  
  
## 語法  
  
```vb  
  
<system.serviceModel>  
  <tracking>    
    <trackingProfile name="String">  
      <workflow activityDefinitionId="String">  
          <activityScheduledQueries>  
             <activityScheduledQuery activityName="String"  
                 childActivityName="String"/>  
          </activityScheduledQueries>  
             <activityStateQuery activityName="String" />  
                <arguments>  
                   <argument name="String"/>  
                </arguments>  
                <states>  
                   <state name="String"/>  
                </states>  
                <variables>  
                   <variable name="String"/>  
                </variables>  
          </activityStateQueries>  
          <bookmarkResumptionQueries>  
             <bookmarkResumptionQuery name="String" />  
          </bookmarkResumptionQueries>  
          <cancelRequestQueries>  
             <cancelRequestQuery activityName="String"  
                 childActivityName="String"/>  
          </cancelRequestQueries>  
          <customTrackingQueries>  
             <customTrackingQuery activityName="String"  
                 name="String"/>  
          </customTrackingQueries>  
          <faultPropagationQueries>  
             <faultPropagationQuery activityName="String"  
                 faultHandlerActivityName="String"/>  
          </faultPropagationQueries>  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                 <state name="String"/>  
              </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.serviceModel>  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|指定追蹤設定檔名稱的字串。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<participants\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|包括特定工作流程之所有查詢的組態項目，這個工作流程可由 **activityDefinitionId** 屬性識別。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<tracking\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|代表定義工作流程服務之追蹤設定的組態區段。|  
  
## 備註  
 追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。  根據您的監控需求，您可以撰寫初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。  反之，您也可以建立非常精確的設定檔，取得充分的結果事件，以便在日後重新建構詳細的執行流程。  
  
 追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。  您可以使用多種查詢型別訂閱不同類別的 TrackingRecord 物件。  如需查詢的完整清單，請參閱 [\<participants\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) 和[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)..  
  
 下列範例顯示設定檔中的追蹤設定檔，可允許追蹤參與者訂閱 `Started`和 `Completed`工作流程事件。  
  
```  
  
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
   </profiles>  
  </tracking>  
</system.serviceModel>  
  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>   
 <xref:System.Activities.Tracking.TrackingProfile>   
 [工作流程追蹤與追查](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)