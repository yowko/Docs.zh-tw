---
title: <security> 的 <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: 68d3aa4da793e0338c2b0b704335bafce7cc3e31
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073945"
---
# <a name="security-of-wshttpbinding"></a>\<安全性 > 的\<wsHttpBinding >
代表的安全性功能[ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。  
  
 \<system.ServiceModel>  
\<bindings>  
\<wsHttpBinding>  
\<binding>  
\<安全性 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|模式|-選擇性。 指定套用的安全性類型。 預設為 `Message`。<br />-此屬性為類型<xref:System.ServiceModel.SecurityMode>。|  
  
## <a name="mode-attribute"></a>Mode 屬性  
  
|值|描述|  
|-----------|-----------------|  
|None|停用安全性。|  
|Transport|系統會使用 HTTPS 來提供安全性。 而服務必須使用 SSL 憑證來設定。 用戶端使用 HTTPS 來完全保護訊息，並使用服務的 SSL 憑證來驗證訊息。 用戶端驗證是透過 `ClientCredentials` 屬性 [\<傳輸 >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)。|  
|訊息|系統會使用 SOAP 訊息安全性來提供安全性。 根據預設，SOAP 本文會經過加密與簽署。 這個模式提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及透過 Security.Message 屬性將何種保護層級套用至訊息主體。 每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。|  
|TransportWithMessageCredential|在這個模式中，HTTPS 會提供完整性、機密性和伺服器驗證，而 SOAP 訊息安全性會提供用戶端驗證。 根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|定義傳輸安全性設定。 這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|定義訊息的安全性設定。 這個項目對應至 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型別。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|HTTP 傳輸應用程式的安全繫結。|  
  
## <a name="remarks"></a>備註  
 WSHttpBinding 類別主要是用來與實作 WS-* 規格的服務進行交互操作。 此繫結的傳輸安全性為使用 HTTP 或 HTTPS 的安全通訊端層 (SSL)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結來設定服務和用戶端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
