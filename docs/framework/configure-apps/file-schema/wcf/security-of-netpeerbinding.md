---
title: <security> 的 <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: be5ebacec466caf8d8a77bf552f42da1861e77a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936619"
---
# <a name="security-of-netpeerbinding"></a>\<netPeerBinding > 的\<安全性 >
定義[ \<netPeerTcpBinding >](netpeertcpbinding.md)的安全性設定, 包括使用的驗證類型, 以及用於訊息傳輸的安全性。  
  
 \<system.ServiceModel>  
\<bindings>  
\<netPeerBinding>  
\<系結 >  
\<安全性 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|模式|選擇性。 指定此繫結所設定之對等要使用的安全性類型。 預設值為 `Message`。 此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。|  
  
## <a name="mode-attribute"></a>mode 屬性  
  
|值|描述|  
|-----------|-----------------|  
|訊息|SOAP 安全性提供驗證、完整性和機密性。|  
|無|停用安全性。|  
|Transport|系統會使用 HTTPS 來提供安全性。|  
|TransportWithMessageCredential|HTTPS 提供驗證和機密性。 SOAP 訊息提供豐富的認證類型。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|定義使用這個繫結設定之對等所傳送安全訊息的傳輸類型。 此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|定義[ \<netPeerTcpBinding >](netpeertcpbinding.md)的所有系結功能。|  
  
## <a name="remarks"></a>備註  
 安全性可以是訊息特定或傳輸特定。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [保護服務和用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
- [選取認證類型](../../../wcf/feature-details/selecting-a-credential-type.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
