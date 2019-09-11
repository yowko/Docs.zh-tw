---
title: <extensions> 區段
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855364"
---
# <a name="extensions-section"></a>\<> 的延伸模組區段
這個組態區段包含延伸的集合，可讓使用者建立使用者定義的繫結、行為和其他方面的延伸。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<延伸模組 >**  
  
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
|[\<behaviorExtensions>](behaviorextensions.md)|這個區段包含指定行為延伸的子項目，可讓使用者自訂服務或端點行為。|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|這個區段會啟用電腦或應用程式組態檔中自訂繫結項目的使用。|  
|[\<bindingExtensions>](bindingextensions.md)|這個區段包含指定繫結延伸的子項目，可讓使用者自訂繫結。|  
|[\<endpointExtensions>](endpointextensions.md)|這個區段包含會註冊標準端點的子項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|system.ServiceModel|所有 WCF 組態項目的根項目。|
