---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 4dc425fa97eaf99664f0d9bbbbc851c462cbf373
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274959"
---
# <a name="services"></a>\<services>
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
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<service>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|定義特定服務的服務合約、行為和端點。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|所有 Windows Communication Foundation (WCF) 組態項目的根項目。|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Configuration.ServicesSection>
