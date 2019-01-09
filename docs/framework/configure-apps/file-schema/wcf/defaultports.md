---
title: '&lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 7ddfddaa13778ce98bd93b6d8029438377fc7e94
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145181"
---
# <a name="ltdefaultportsgt"></a>&lt;defaultPorts&gt;
預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。  
  
\<system.ServiceModel>  
\<行為 >  
\<serviceBehaviors>  
\<行為 >  
\<useRequestHeadersForMetadataAddress >  
\<a d d >  
  
## <a name="syntax"></a>語法  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<新增 > 的\<a d d >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|預設通訊端點，用戶端應用程式會接聽這個端點。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress >](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|預設連接埠清單。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
