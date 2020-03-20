---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 763754b95a7f39c7f35e05df28589b69352168e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152420"
---
# <a name="activityscheduledqueries"></a>\<活動 計畫查詢>
代表查詢的集合，可用來追蹤已排程且由父活動執行的活動。 追蹤參與者必須要具備查詢，才能訂閱活動排程記錄。  
  
 有關跟蹤設定檔查詢的詳細資訊，請參閱[跟蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤設定檔>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<工作流>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<活動 計畫查詢>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<活動計劃查詢>](activityscheduledquery.md)|查詢，可用來追蹤已排程且由父活動執行的活動。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<工作流>](workflow.md)|包含**活動定義 Id**屬性標識的特定工作流的所有查詢的配置元素。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [工作流程追蹤及追蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)
