---
title: <security> 的 <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: c6f9e34724ccc3a0d05da3e1886b4f0bcbaae064
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670439"
---
# <a name="security-of-wsdualhttpbinding"></a>\<security> of \<wsDualHttpBinding>
定義的安全性功能[ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)。  
  
 \<system.ServiceModel>  
\<bindings>  
\<wsDualHttpBinding>  
\<binding>  
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
|模式|-選擇性。 指定套用的安全性類型。 預設值為 `Message`。 此屬性的型別為 <xref:System.ServiceModel.WSDualHttpSecurityMode>。|  
  
## <a name="mode-attribute"></a>Mode 屬性  
  
|值|描述|  
|-----------|-----------------|  
|None|停用安全性。|  
|訊息|系統會使用 SOAP 訊息安全性來提供安全性。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|定義訊息層級安全性的設定。 此項目的型別為 <xref:System.ServiceModel.MessageSecurityOverHttp>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|定義的所有繫結功能[ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)。|  
  
## <a name="remarks"></a>備註  
 雙重繫結會向服務公開用戶端的 IP 位址， 用戶端應該使用安全性確保本身只連接其信任的服務。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
