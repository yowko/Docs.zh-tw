---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 89297b3a7d64f4300a735d8512230d441836c634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152303"
---
# <a name="cancelrequestedqueries"></a>\<取消請求查詢>
代表查詢的集合，這個集合可用來追蹤由父活動取消子活動的要求。 追蹤參與者必須要具備這個查詢，才能訂閱取消要求記錄物件。  
  
 有關跟蹤設定檔查詢的詳細資訊，請參閱[跟蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤設定檔>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<工作流>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<取消請求查詢>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
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
|[\<取消請求查詢>](cancelrequestedquery.md)|查詢，可用來追蹤由父活動取消子活動的要求。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<工作流>](workflow.md)|包含**活動定義 Id**屬性標識的特定工作流的所有查詢的配置元素。|  
  
## <a name="see-also"></a>另請參閱

- [工作流程追蹤及追蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追蹤設定檔](../../../windows-workflow-foundation/tracking-profiles.md)
