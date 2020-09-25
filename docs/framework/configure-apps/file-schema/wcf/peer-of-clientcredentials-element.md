---
title: <peer> 項目的 <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 75d8543d7db5eee1345d54f934fc89c9593b85ac
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186987"
---
# <a name="peer-of-clientcredentials-element"></a>\<peer> 項目的 \<clientCredentials>

指定驗證對等用戶端時所使用的認證。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
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

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  

 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|指定要用來簽署與加密對等用戶端之訊息的 X.509 憑證。 .|  
|[\<peerAuthentication>](peerauthentication-element.md)|指定對等用戶端的驗證選項。|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|指定訊息寄件者的驗證選項。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|指定用來對服務驗證用戶端的認證。|  
  
## <a name="remarks"></a>備註  

 這個組態項目會指定對等節點用於向網狀結構中其他節點驗證其本身的認證，以及對等節點用來驗證其他對等節點的驗證設定。 如需詳細資訊，請參閱 [對等通道訊息驗證](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) 和 [保護對等通道應用程式](../../../wcf/feature-details/securing-peer-channel-applications.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [對等網路](../../../wcf/feature-details/peer-to-peer-networking.md)
- [確保用戶端的安全](../../../wcf/securing-clients.md)
- [對等通道訊息驗證](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [對等通道自訂驗證](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [確保對等通道應用程式安全](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [確保服務與用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
