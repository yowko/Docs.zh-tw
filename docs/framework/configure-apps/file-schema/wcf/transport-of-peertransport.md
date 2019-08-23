---
title: <transport> 的 <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 5dbc55db25c0c49d72ec2cd8dd1041a3f8705d8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940638"
---
# <a name="transport-of-peertransport"></a>\<peerTransport > 的\<傳輸 >
指定使用這個繫結設定之對等所傳送安全訊息的傳輸類型。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<系結 >  
\<peerTransport>  
\<安全性 >  
\<transport>  
  
## <a name="syntax"></a>語法  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|credentialType|選擇性。 指定認證的類型，用於驗證對等傳輸所傳送的訊息。 此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。|  
  
## <a name="credentialtype-attribute"></a>credentialType 屬性  
  
|值|說明|  
|-----------|-----------------|  
|憑證|對等通道傳輸的驗證作業需要 X509 憑證。|  
|密碼|對等通道傳輸的驗證作業需要正確的密碼。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|定義對等傳輸的安全性設定。|  
  
## <a name="remarks"></a>備註  
 只有在  [ \<安全性 >](security-of-peertransport.md)的 [模式] 屬性設定為`Transport`或`TransportWithMessageCredential`時, 才會設定此元素。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [傳輸安全性](../../../wcf/feature-details/transport-security.md)
- [傳輸](../../../wcf/feature-details/transports.md)
- [選擇傳輸](../../../wcf/feature-details/choosing-a-transport.md)
- [繫結](../../../wcf/bindings.md)
- [擴充繫結](../../../wcf/extending/extending-bindings.md)
- [自訂繫結](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
