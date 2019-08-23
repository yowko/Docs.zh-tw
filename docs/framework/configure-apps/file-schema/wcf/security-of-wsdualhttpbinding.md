---
title: <security> 的 <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: bed7f4ce325e0d5e387e310ca15a3b72ac93f18e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936549"
---
# <a name="security-of-wsdualhttpbinding"></a>\<wsDualHttpBinding > 的\<安全性 >
定義[ \<wsDualHttpBinding >](wsdualhttpbinding.md)的安全性功能。  
  
 \<system.ServiceModel>  
\<bindings>  
\<wsDualHttpBinding>  
\<系結 >  
\<安全性 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|模式|選擇性. 指定套用的安全性類型。 預設值為 `Message`。 此屬性的型別為 <xref:System.ServiceModel.WSDualHttpSecurityMode>。|  
  
## <a name="mode-attribute"></a>Mode 屬性  
  
|值|說明|  
|-----------|-----------------|  
|None|停用安全性。|  
|訊息|系統會使用 SOAP 訊息安全性來提供安全性。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[\<message>](message-of-wsdualhttpbinding.md)|定義訊息層級安全性的設定。 此項目的型別為 <xref:System.ServiceModel.MessageSecurityOverHttp>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|定義[ \<wsDualHttpBinding >](wsdualhttpbinding.md)的所有系結功能。|  
  
## <a name="remarks"></a>備註  
 雙重繫結會向服務公開用戶端的 IP 位址， 用戶端應該使用安全性確保本身只連接其信任的服務。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [保護服務和用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
