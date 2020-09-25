---
title: <security> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 60b863a0a2a846a60dde2e4b323a305b5096b1cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169891"
---
# <a name="security-of-webhttpbinding"></a>\<security> 的 \<webHttpBinding>

指定以設定之端點的安全性需求 [\<webHttpBinding>](webhttpbinding.md) 。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.ServiceModel>
  <bindings>
    <webHttpBinding>
      <binding name = "String">
        <security mode="None/Transport/TransportCredentialOnly">
          <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                     realm="String" />
        </security>
      </binding>
    </webHttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|mode|指定端點是否使用傳輸層級安全性或不使用安全性。 預設值為 `None`。 此屬性的型別為 <xref:System.ServiceModel.WebHttpSecurityMode>。|  
  
## <a name="mode-attribute"></a>Mode 屬性  
  
|值|描述|  
|-----------|-----------------|  
|無|停用安全性。|  
|傳輸|系統會使用 HTTPS 來提供安全性。 而服務必須使用 SSL 憑證來設定。 HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。 用戶端驗證是透過的屬性來控制 `ClientCredentialType` [\<transport>](transport-of-webhttpbinding.md) 。|  
|TransportCredentialOnly|這個模式不提供訊息完整性和機密性， 但會提供 HTTP 架構的用戶端驗證。 請謹慎使用這個模式， 它應該用於以其他方式提供傳輸安全性的環境中 (例如 IPSec) ，而且只有 WCF 基礎結構會提供用戶端驗證。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|定義傳輸安全性設定。 這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|繫結項目，用於設定 Windows Communication Foundation (WCF) Web 服務的端點，這些服務會回應 HTTP 要求，而非 SOAP 訊息。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [確保服務與用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
- [選取認證類型](../../../wcf/feature-details/selecting-a-credential-type.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結來設定服務和用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [WCF Web HTTP 程式設計模型](../../../wcf/feature-details/wcf-web-http-programming-model.md)
