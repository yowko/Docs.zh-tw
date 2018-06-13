---
title: '&lt;服務&gt;'
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 789fc52f628174ef61a9c7169cb0cae0f1ba8e31
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749227"
---
# <a name="ltservicesgt"></a>&lt;服務&gt;
服務定義於組態檔的 `services` 區段中。 各服務都有自己的 `service` 組態區段。  
  
 \<system.ServiceModel>  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<service>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|定義特定服務的服務合約、行為和端點。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|所有 Windows Communication Foundation (WCF) 組態項目的根項目。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.ServicesSection>
