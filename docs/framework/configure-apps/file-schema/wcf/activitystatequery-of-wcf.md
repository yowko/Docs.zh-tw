---
title: <activityStateQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: ce7505896b9c5bb605bb0f67d735cb324f4fd493
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926903"
---
# <a name="activitystatequery-of-wcf"></a>\<WCF 的 activityStateQuery >

代表查詢，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。 例如, 您可能想要追蹤在工作流程實例中完成「傳送電子郵件」活動的每次。 追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。 可供訂閱的狀態可於 ActivityStates 中指定。  
  
如需追蹤設定檔查詢的詳細資訊, 請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。

\<system.serviceModel> \<tracking>  
\<profiles> \<trackingProfile>  
\<工作流程 >  
\<activityStateQueries>  
\<activityStateQuery>  
  
## <a name="syntax"></a>語法  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  

下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|activityName|字串，這個字串會指定活動的名稱，以篩選 <xref:System.Activities.Tracking.ActivityStateRecord> 執行個體。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<引數 >](../windows-workflow-foundation/arguments.md)|與此活動查詢相關聯之引數的集合。|  
|[\<states>](../windows-workflow-foundation/states.md)|組態元素的集合，其中包含應該發出追蹤記錄之已訂閱活動的狀態。|  
|[\<states>](../windows-workflow-foundation/states.md)|與此活動查詢相關聯之變數的集合。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](../windows-workflow-foundation/faultpropagationquery.md)|代表組態項目的清單，這個清單可用來追蹤由父活動取消子活動的要求。 追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。|  
  
## <a name="remarks"></a>備註

ActivityStateQuery 的一項獨特功能，就是可在追蹤工作流程的執行時擷取資料。 它可在存取追蹤記錄後期執行時，提供額外的內容。 您可以使用[ \<引數 >](../windows-workflow-foundation/arguments.md)、 [ \<狀態 >](../windows-workflow-foundation/states.md)和[ \<狀態 >](../windows-workflow-foundation/states.md)元素, 從工作流程中的任何活動中解壓縮任何變數或引數。下列範例顯示活動狀態查詢, 它會在發出活動的`Closed`追蹤記錄時, 解壓縮變數和引數。 只能使用 ActivityStateRecord 來解壓縮變數和引數, 因此會使用[ \<activityStateQuery >](../windows-workflow-foundation/activitystatequery.md)在追蹤設定檔內訂閱。  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed" />
  </states>
  <variables>
    <variable name="FromAddress" />
  </variables>
  <arguments>
    <argument name="Result" />
  </arguments>
</activityStateQuery>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [工作流程追蹤及追蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)
