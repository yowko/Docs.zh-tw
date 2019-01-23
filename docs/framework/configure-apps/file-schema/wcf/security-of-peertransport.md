---
title: '&lt;peerTransport&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 8b0b8c5f230e8e93c07e13212201896010429af0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585376"
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a>&lt;peerTransport&gt; 的 &lt;security&gt;
包含與對等通道相關聯的安全性設定，包括使用的驗證類型與訊息傳輸所用的安全性。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<peerTransport>  
\<安全性 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`mode`|指定要套用的安全性類型。 預設值為 Message。 此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。|  
  
## <a name="mode-attribute"></a>mode 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`None`|停用安全性。|  
|`Transport`|系統會使用 HTTPS 來提供安全性。|  
|`Message`|SOAP 安全性提供驗證、完整性和機密性。|  
|`TransportWithMessageCredential`|HTTPS 提供驗證和機密性。 SOAP 訊息提供豐富的認證類型。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|定義自訂繫結的對等傳輸。 此項目具有 `clientCredentialType` 屬性，可指定與服務互動時所用的認證。 此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。<br /><br /> 此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<peerTransport>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|定義自訂繫結的對等傳輸。|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [傳輸安全性](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [傳輸](../../../../../docs/framework/wcf/feature-details/transports.md)
- [選擇傳輸](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
