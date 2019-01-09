---
title: '&lt;extensions&gt; 區段'
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 92dd3c528290344d9537c51fccf7c13c74c1984a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145311"
---
# <a name="ltextensionsgt-section"></a>&lt;extensions&gt; 區段
這個組態區段包含延伸的集合，可讓使用者建立使用者定義的繫結程序、行為和其他方面的延伸。  
  
\<system.ServiceModel>  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
    </bindingExtensions>
    <behaviorExtensions>
    </behaviorExtensions>
    <bindingElementExtensions>
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<behaviorExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|這個區段包含指定行為延伸的子項目，可讓使用者自訂服務或端點行為。|  
|[\<bindingElementExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|這個區段會啟用電腦或應用程式組態檔中自訂繫結項目的使用。|  
|[\<bindingExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|這個區段包含指定繫結延伸的子項目，可讓使用者自訂繫結。|  
|[\<endpointExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|這個區段包含會註冊標準端點的子項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|system.ServiceModel|所有 WCF 組態項目的根項目。|
