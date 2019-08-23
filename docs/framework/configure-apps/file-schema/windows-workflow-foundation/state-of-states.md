---
title: <state> 的 <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 7c7326b2fd5ae39ca4c0f39fac05444802fa3d49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947487"
---
# <a name="state-of-states"></a>\<狀態 > \<>
組態項目，其中包含應該發出追蹤記錄之已訂閱活動的狀態。  
  
 如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。  
  
\<system.serviceModel>  
\<追蹤 >  
\<trackingProfile>  
\<工作流程 >  
\<activityStateQueries>  
\<activityStateQuery>  
\<狀態 >  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|NAME|可指定追蹤記錄應發出之已訂閱活動狀態的字串。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<states>](states-of-activitystatequery.md)|組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。|  
  
## <a name="remarks"></a>備註  
 ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。 它可在存取追蹤記錄後期執行時，提供額外的內容。 您可以使用[ \<引數 >](arguments.md)、 [ \<狀態 >](states.md)和[ \<狀態 >](states.md)元素, 從工作流程中的任何活動中解壓縮任何變數或引數。 下列範例示範活動狀態查詢，此查詢會在發出活動的 `Closed` 追蹤記錄時擷取變數及引數。 只能使用 ActivityStateRecord 來解壓縮變數和引數, 因此會使用[ \<activityStateQuery >](activitystatequery.md)在追蹤設定檔內訂閱。  
  
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

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [工作流程追蹤及追蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)
