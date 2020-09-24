---
title: <peer> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 7f6669d3f53a6ee0d189786fa9ca3625fdedd127
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162474"
---
# <a name="peer-of-servicecredentials"></a>\<peer> 的 \<serviceCredentials>

指定對等節點的目前認證。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  

 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|指定要用來簽署與加密對等服務之訊息的 X.509 憑證。 .|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|指定訊息寄件者的驗證選項。|  
|[\<peerAuthentication>](peerauthentication.md)|指定對等服務的驗證選項。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [對等網路](../../../wcf/feature-details/peer-to-peer-networking.md)
- [對等通道訊息驗證](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [對等通道自訂驗證](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [確保對等通道應用程式安全](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [確保服務與用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
