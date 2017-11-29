---
title: "&lt;activityStateQuery&gt; 的 &lt;states&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4ee98263f43d9557d0ee81484ff8550f0e927ca6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltstatesgt-of-ltactivitystatequerygt"></a>&lt;activityStateQuery&gt; 的 &lt;states&gt;
組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。  
  
 如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。  
  
\<system.serviceModel >  
\<追蹤 >  
\<trackingProfile >  
\<工作流程 >  
\<activityStateQueries >  
\<activityStateQuery >  
\<狀態 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/state-of-states.md)|組態項目，其中包含追蹤記錄應發出之已訂閱活動的狀態。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|代表組態項目，可用來追蹤由父活動取消子活動的要求。 追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。|  
  
## <a name="remarks"></a>備註  
 ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。 它可在存取追蹤記錄後期執行時，提供額外的內容。 您可以使用[\<引數 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)和[\<狀態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)擷取任何變數或引數的項目從工作流程中的任何活動。下列範例示範了擷取變數及引數的活動狀態查詢時活動的`Closed`就會發出追蹤記錄。 變數和引數可以只能使用 activitystaterecord 擷取，因此訂閱在追蹤設定檔中使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。  
  
```xml  
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
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>      
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [工作流程追蹤及追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
