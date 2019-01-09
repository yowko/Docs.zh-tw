---
title: '&lt;transportConfigurationTypes&gt;'
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 5a51450d198ea395098f8a6a38d9104d0fe8538b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145467"
---
# <a name="lttransportconfigurationtypesgt"></a>&lt;transportConfigurationTypes&gt;
代表組態項目的集合，這些項目會識別特定傳輸的類型。 這可以用來加入自訂 WAS 通訊協定。  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment >  
\<transportConfigurationTypes >  
  
## <a name="syntax"></a>語法  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|name|傳輸的名稱|  
|transportConfigurationType|實作傳輸的型別|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|新增組態項目，此項目會識別特定傳輸的類型。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|定義服務裝載環境為特定傳輸產生的類型。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [裝載](../../../../../docs/framework/wcf/feature-details/hosting.md)
