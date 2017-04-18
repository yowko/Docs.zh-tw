---
title: "&lt;arguments&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;arguments&gt;
表示與某個活動狀態查詢相關聯之引數的集合。  
  
 如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)。  
  
## 語法  
  
```vb  
  
<tracking>  
   <trackingProfile name="Name">  
       <workflow>  
          <activityStateQueries>  
             <activityStateQuery activityName="String" />  
                <arguments>  
                   <argument name="String"/>  
                </arguments>  
          </activityStateQueries>  
       </workflow>  
   </trackingProfile>  
</tracking>  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<argument\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|與活動狀態查詢相關聯的引數。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<activityStateQuery\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|代表組態項目，可用來追蹤由父活動取消子活動的要求。  追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。|  
  
## 備註  
 ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。  它可在存取追蹤記錄後期執行時，提供額外的內容。  您可以使用 [\<arguments\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)、[\<states\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) 以及 [\<states\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) 項目，從工作流程中的任何活動，擷取任何變數或引數。下列範例顯示發出活動的 `Closed` 追蹤記錄時，擷取變數和引數的活動狀態查詢。  變數和引數只能使用 ActivityStateRecord 擷取，因此可在追蹤設定檔中使用[\<activityStateQuery\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)訂閱 。  
  
```  
  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
  
```  
  
## 請參閱  
 [System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection](assetId:///System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?qualifyHint=False&amp;autoUpgrade=True)   
 [System.Activities.Tracking.ActivityStateQuery](assetId:///System.Activities.Tracking.ActivityStateQuery?qualifyHint=False&amp;autoUpgrade=True)   
 [工作流程追蹤與追查](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)