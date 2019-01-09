---
title: WCF 的 &lt;customTrackingQuery&gt;
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 234703e677f838dcdccdf857ba38b8729d25a488
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146377"
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a>WCF 的 &lt;customTrackingQuery&gt;

表示用來追蹤您在程式碼活動中定義的事件的查詢。 追蹤參與者必須要具備查詢，才能訂閱自訂追蹤記錄。

如需有關追蹤設定檔查詢的詳細資訊，請參閱[追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<追蹤 >  
\<設定檔 >  
\<trackingProfile>  
\<工作流程 >  
\<customTrackingQueries >  
\<customTrackingQuery >  
  
## <a name="syntax"></a>語法  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  

下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`activityName`|字串，可指定產生追蹤記錄的活動名稱。|  
|`name`|字串，可指定發出自訂追蹤記錄的名稱。|  
  
### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|  
|-------------|-----------------|  
|[\<customTrackingQueries>](customtrackingqueries-of-wcf.md)|代表查詢的集合，這個集合可用來追蹤程式碼活動中定義的事件。|
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [工作流程追蹤及追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追蹤設定檔](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
