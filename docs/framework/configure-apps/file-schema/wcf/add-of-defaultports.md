---
title: '&lt;defaultPorts&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 0932ef9afacb6278c4857dcfd6ba545595ff8f9d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147716"
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a>&lt;defaultPorts&gt; 的 &lt;add&gt;
預設通訊端點，用戶端應用程式會接聽這個端點。  
  
 \<system.ServiceModel>  
\<行為 >  
\<serviceBehaviors>  
\<行為 >  
\<useRequestHeadersForMetadataAddress >  
\<a d d >  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|連接埠|指定預設通訊埠編號的整數。|  
|scheme|指定與通訊連接埠相關之通訊協定設定群組的字串。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<a d d >](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
