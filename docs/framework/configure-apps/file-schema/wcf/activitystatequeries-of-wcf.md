---
title: <activityStateQueries>WCF 的
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 249ac3d91f6251a943dd856e4122b8b54f691702
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850580"
---
# <a name="activitystatequeries-of-wcf"></a>\<WCF 的 Q s >

代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。 例如，您可能想要追蹤在工作流程實例中完成「傳送電子郵件」活動的每次。 追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。 可供訂閱的狀態可於 ActivityStates 中指定。

如需追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<設定檔 >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<工作流程 >** ](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Q s >**  
  
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

無。  

### <a name="child-elements"></a>子元素

|項目|說明|
|-------------|-----------------|
|[\<activityStateQuery>](activitystatequery-of-wcf.md)|用來追蹤活動中發生之錯誤處理的查詢。  每當 FaultHandler 處理錯誤時，都會發生這個事件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[\<workflow>](../windows-workflow-foundation/workflow.md)|包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。|

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [工作流程追蹤及追蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)
