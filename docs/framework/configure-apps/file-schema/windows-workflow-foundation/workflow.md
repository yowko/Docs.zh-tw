---
title: "&lt;workflow&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;workflow&gt;
包括特定工作流程之所有查詢的組態項目，這個工作流程可由 **activityDefinitionId** 屬性識別。  
  
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
|activityDefinitionId|指定工作流程之活動定義識別碼的字串，該工作流程正在進行追蹤。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<activityScheduledQueries\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledqueries.md)|代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。  追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。|  
|[\<activityStateQueries\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequeries.md)|代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。  例如，您可能想要追蹤在工作流程執行個體中完成的每一次「傳送電子郵件」活動。  追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。  可供訂閱的狀態可於 ActivityStates 中指定。|  
|[\<bookmarkResumptionQueries\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|代表查詢的集合，這個集合可用來追蹤工作流程執行個體中的書籤繼續。  追蹤參與者必須要具備查詢，才能訂閱書籤繼續記錄。|  
|[\<cancelRequestedQueries\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedqueries.md)|代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。  追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。|  
|[\<customTrackingQueries\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingqueries.md)|代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。  追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。|  
|[\<faultPropagationQueries\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|代表查詢的集合，這些查詢可用來追蹤活動內發生之錯誤的處理。 每當 FaultHandler 處理錯誤時，都會發生這個事件。  您應該使用這種查詢來追蹤活動中發生的錯誤處理。  追蹤參與者必須要具備查詢，才能訂閱錯誤傳播記錄。|  
|[\<workflowInstanceQueries\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|代表組態項目的集合，可用來追蹤工作流程執行個體生命週期的變更，例如已開始或已完成的事件。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<trackingProfile\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|代表組態區段，這個區段用於建立訂閱追蹤參與者中的工作流程追蹤記錄。  追蹤設定檔包含追蹤查詢，這些查詢允許追蹤參與者訂閱工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。  追蹤設定檔區段中定義的查詢會定義訂閱所傳回的事件類型。|  
  
## 備註  
 追蹤設定檔包含有追蹤查詢，這些查詢允許追蹤參與者訂閱特定工作流程執行個體狀態在執行時期變更時所發出的工作流程事件。  這個設定項目會識別正在追蹤的工作流程執行個體。  
  
 根據您的監控需求，您可以撰寫初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。  反之，您也可以建立非常精確的設定檔，取得充分的結果事件，以便在日後重新建構詳細的執行流程。  
  
 追蹤設定檔會結構化成追蹤記錄的宣告式訂閱，可讓您查詢特定追蹤記錄的工作流程執行階段。  您可以使用多種查詢型別訂閱不同類別的追蹤記錄。  如需查詢的完整清單，請參閱這個主題的子項目清單，以及[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)。  
  
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
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>   
 <xref:System.Activities.Tracking.TrackingProfile>   
 [工作流程追蹤與追查](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)