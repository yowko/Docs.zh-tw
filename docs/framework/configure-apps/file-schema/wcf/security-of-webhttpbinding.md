---
title: <security> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 77009dc950a608da9e0db3a7d09be67e1ed46137
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738631"
---
# <a name="security-of-webhttpbinding"></a>\<security> 的 \<webHttpBinding>
指定以設定之端點的安全性需求 [\<webHttpBinding>](webhttpbinding.md) 。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>語法  
  
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
|None|停用安全性。|  
|傳輸|系統會使用 HTTPS 來提供安全性。 而服務必須使用 SSL 憑證來設定。 HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。 用戶端驗證是透過的 `ClientCredentialType` 屬性來控制 [\<transport>](transport-of-webhttpbinding.md) 。|  
|TransportCredentialOnly|這個模式不提供訊息完整性和機密性， 但會提供 HTTP 架構的用戶端驗證。 請謹慎使用這個模式， 它應該用於以其他方式（例如 IPSec）提供傳輸安全性，而且 WCF 基礎結構只提供用戶端驗證的環境中。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|定義傳輸安全性設定。 這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|繫結項目，用來設定 Windows Communication Foundation （WCF） Web 服務的端點，以回應 HTTP 要求，而不是 SOAP 訊息。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [選取認證類型](../../../wcf/feature-details/selecting-a-credential-type.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [WCF Web HTTP 程式設計模型](../../../wcf/feature-details/wcf-web-http-programming-model.md)
