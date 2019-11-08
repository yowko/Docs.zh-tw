---
title: <security> 的 <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 3d1ac85073c44f683fe0c054737c5ec7ed1cbf52
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738655"
---
# <a name="security-of-netpeerbinding"></a>\<netPeerBinding 的 \<安全性 > >
定義[\<netPeerTcpBinding >](netpeertcpbinding.md)的安全性設定，包括所使用的驗證類型，以及用於訊息傳輸的安全性。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**  
  
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
|模式|選擇項。 指定此繫結所設定之對等要使用的安全性類型。 預設值是 `Message`。 此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。|  
  
## <a name="mode-attribute"></a>mode 屬性  
  
|值|描述|  
|-----------|-----------------|  
|訊息|SOAP 安全性提供驗證、完整性和機密性。|  
|None|停用安全性。|  
|Transport|系統會使用 HTTPS 來提供安全性。|  
|TransportWithMessageCredential|HTTPS 提供驗證和機密性。 SOAP 訊息提供豐富的認證類型。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<傳輸 >](transport-of-netpeertcpbinding.md)|定義使用這個繫結設定之對等所傳送安全訊息的傳輸類型。 此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding >](bindings.md)|定義[\<netPeerTcpBinding >](netpeertcpbinding.md)的所有系結功能。|  
  
## <a name="remarks"></a>備註  
 安全性可以是訊息特定或傳輸特定。  
  
## <a name="see-also"></a>請參閱

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [保護服務和用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
- [選取認證類型](../../../wcf/feature-details/selecting-a-credential-type.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding >](bindings.md)
