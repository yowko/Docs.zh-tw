---
title: <routing> 的 <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 73a610056f94efe144705968eaf97c8314c1ae0d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934190"
---
# <a name="routing-of-servicebehavior"></a>\<serviceBehavior > 的\<路由 >
提供於執行階段存取路由服務的功能，可用來動態修改路由組態。  
  
 \<system.ServiceModel>  
\<行為 >  
\<serviceBehaviors>  
\<行為 >  
\<路由 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|filterTable|字串，指定路由表的名稱，該路由表包含將由路由服務評估的篩選條件。 這個值必須符合`name` [filterTables > 區段中 filterTable > 元素的屬性。 \< ](filtertables.md) [ \< ](filtertable.md)|  
|routeOnHeaderOnly|布林值，指定篩選器會檢查訊息本文和標頭，或者只檢查標頭。 預設為 `true`。|  
|soapProcessingEnabled|布林值，指定是否應進行 SOAP 處理。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|指定行為項目。|  
  
## <a name="remarks"></a>備註  
 加入至服務的行為組態時，這個組態項目會啟用服務的路由。 您可以指定這個項目中的服務使用實際的路由表。  
  
 使用這個組態區段時，您可以在部署模式變更時即時變更路由設定。 在執行階段中，您可以使用新的路由設定註冊自己的路由擴充，而路由服務會開始將更新後的組態資訊用於新的訊息及工作階段，同時又可以在訊息/工作階段啟動時使用現有的任何規則結束進行中的訊息/工作階段。  這樣您就可以在執行階段期間進行具工作階段安全且回收頻率較低的路由服務重新設定。  
