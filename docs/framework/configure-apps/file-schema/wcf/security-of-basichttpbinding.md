---
title: <security> 的 <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: 6144e5448526d7f2a7c89693f70f71a7f26c4a22
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183659"
---
# <a name="security-of-basichttpbinding"></a>\<security> 的 \<basicHttpBinding>

定義的安全性功能 [\<basicHttpBinding>](basichttpbinding.md) 。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|mode|選擇性。 指定使用的安全性類型。 預設值為 `None`。 此屬性的型別為 <xref:System.ServiceModel.BasicHttpSecurityMode>。|  
  
## <a name="mode-attribute"></a>mode 屬性  
  
|值|描述|  
|-----------|-----------------|  
|無|-傳輸期間不會保護訊息。|  
|傳輸|會使用 HTTPS 傳輸來提供安全性。 使用 HTTPS 來維護 SOAP 訊息的安全。 對用戶端驗證服務時，則是使用服務的 X.509 憑證。 用戶端會透過提供的 ClientCredentialType 來驗證。 請參閱 [\<transport>](transport-of-basichttpbinding.md) 。|  
|訊息|系統會使用 SOAP 訊息安全性來提供安全性。 根據預設，本文會經過加密與簽署。 對於此繫結，系統會要求將伺服器憑證提供給超出範圍的用戶端。 這個繫結唯一有效的 `ClientCredentialType` 是 `Certificate`。|  
|TransportWithMessageCredential|完整性、機密性與伺服器驗證都是經由傳輸安全性來提供。 用戶端驗證是透過 SOAP 訊息安全性的方式提供。 當使用者是透過使用者名稱/密碼進行驗證，且有現有的 HTTP 部署來保護訊息傳輸的安全時，即與此模式有關。|  
|TransportCredentialOnly|這個模式不提供訊息完整性和機密性， 但會提供 HTTP 架構的用戶端驗證。 請謹慎使用這個模式， 它應該用於以其他方式提供傳輸安全性的環境中 (例如 IPSec) ，而且只有 WCF 基礎結構會提供用戶端驗證。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<transport>](transport-of-basichttpbinding.md)|定義基本 HTTP 服務的傳輸安全性設定。 這個項目對應於 <xref:System.ServiceModel.HttpTransportSecurity>。|  
|[\<message>](message-of-basichttpbinding.md)|定義基本 HTTP 服務的訊息安全性設定。 這個項目對應於 <xref:System.ServiceModel.BasicHttpMessageSecurity>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|繫結|的繫結項目 [\<basicHttpBinding>](basichttpbinding.md) 。|  
  
## <a name="remarks"></a>備註  

 根據預設，SOAP 訊息並不安全，而且用戶端也尚未經過驗證。 這個項目可讓您設定 `basicHttpBinding` 項目的其他安全性設定。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [確保服務與用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
- [選取認證類型](../../../wcf/feature-details/selecting-a-credential-type.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結來設定服務和用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
