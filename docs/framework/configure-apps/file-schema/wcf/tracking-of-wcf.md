---
title: "WCF 的 &lt;tracking&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# WCF 的 &lt;tracking&gt;
代表定義工作流程服務之追蹤設定的組態區段。  
  
 如需工作流程追蹤及其組態的詳細資訊，請參閱[工作流程追蹤與追查](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)和[設定工作流程的追蹤](../../../../../docs/framework/windows-workflow-foundation//configuring-tracking-for-a-workflow.md)。  
  
## 語法  
  
```vb  
  
<system.serviceModel>  
  <tracking>    
     <participants>   
      <add name="String"   
           profileName="String"  
           type="String" />   
     </participants>   
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
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<participants\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|組態項目的集合，這些項目會定義訂閱追蹤記錄的參與者。  追蹤參與者包含處理來自追蹤記錄之裝載的邏輯 \(例如，他們可以選擇寫入檔案\)。|  
|[\<trackingProfile\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|篩選工作流程執行個體發出之追蹤記錄的追蹤設定檔。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|system.ServiceModel|所有工作流程組態項目的根項目。|  
  
## 備註  
 追蹤可提供您檢查工作流程執行的能力。  工作流程追蹤基礎結構會檢測工作流程，在執行期間發出記錄以反映重要事件。  例如，工作流程執行個體開始或完成時會發出追蹤記錄。  追蹤也可以擷取與工作流程變數相關聯的商務相關資料。  例如，如果工作流程代表訂單處理系統，則訂單識別碼可與追蹤記錄一併擷取。  一般而言，啟用 WF 追蹤有助於對工作流程的執行進行診斷或業務分析。  
  
## 請參閱  
 [System.ServiceModel.Activities.Tracking.Configuration.TrackingSection](assetId:///System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?qualifyHint=False&amp;autoUpgrade=True)   
 [工作流程追蹤與追查](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)