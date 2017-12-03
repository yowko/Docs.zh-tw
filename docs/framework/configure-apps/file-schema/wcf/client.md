---
title: "&lt;用戶端&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 260408bd168246b67830637ca53e78b78758b849
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientgt"></a>&lt;用戶端&gt;
`client` 項目會定義用戶端可連線的端點清單。  
  
 \<系統。ServiceModel >  
\<用戶端 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>  
    <client>  
        <endpoint>  
        </endpoint>  
                <metadata>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[\<端點 >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|包含端點項目的清單，其中的端點項目指定這個用戶端可連線的端點。|  
|[\<中繼資料 >](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|包含處理中繼資料的設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|所有 Windows Communication Foundation (WCF) 組態項目的根項目。|  
  
## <a name="remarks"></a>備註  
 `client` 區段會定義用戶端可連線的端點清單。 在用戶端區段中定義的每個端點會定義它自己的繫結、行為和合約。 它是以 `name` 和 `contract` 屬性的組合唯一識別的。 用戶端程式碼指定 `name` 以連線至用戶端所實作服務的端點。 如果省略 `name` 屬性，則端點會做為它所實作合約的預設端點。  
  
 此外，本區段也會指定處理中繼資料的設定。  
  
## <a name="example"></a>範例  
  
```xml  
<client>  
    <endpoint address="/HelloWorld/"  
              bindingConfiguration="usingDefaults"  
              name="MyBinding"  
              binding="customBinding"  
              contract="HelloWorld">  
    <addressProperties actingAs="http://www.microsoft.com/TestActor"  
             identityData="BasicReadWrite" identityType="Spn" isAddressPrivate="false">  
    </endpoint>  
</client>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [WCF 用戶端組態](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [用戶端](../../../../../docs/framework/wcf/feature-details/clients.md)
