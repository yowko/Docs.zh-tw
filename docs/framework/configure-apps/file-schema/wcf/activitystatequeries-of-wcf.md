---
title: WCF 的 &lt;activityStateQueries&gt;
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 6b21ad3f5487a924309b8bee6b9ac972f23bdc66
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701933"
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a>WCF 的 &lt;activityStateQueries&gt;

代表查詢的集合，可用來追蹤活動的生命週期之變更，這些活動將構成工作流程執行個體。 例如，您可能要追蹤的每次在 「 傳送電子郵件 」 活動完成的工作流程執行個體內。 追蹤參與者必須要具備這個查詢，才能訂閱活動狀態記錄物件。 可供訂閱的狀態可於 ActivityStates 中指定。

如需有關追蹤設定檔查詢的詳細資訊，請參閱 <<c0> [ 追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。

\<system.serviceModel>  
\<tracking>  
\<設定檔 >  
\<trackingProfile>  
\<workflow>  
\<activityStateQueries>  

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

|項目|描述|
|-------------|-----------------|
|[\<activityStateQuery>](activitystatequery-of-wcf.md)|用來追蹤活動中發生之錯誤處理的查詢。  每當 FaultHandler 處理錯誤時，都會發生這個事件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[\<workflow>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|包括特定工作流程之所有查詢的組態項目，這個工作流程可由 `activityDefinitionId` 屬性識別。|

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [工作流程追蹤及追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
