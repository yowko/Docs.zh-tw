---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: 6094006df24ee824c419a783ab29d7604757577c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201456"
---
# \<clientCredentials>

指定用來對服務驗證用戶端的認證。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`supportInteractive`|布林值，指定互動式使用者是否可以在執行階段選取用戶端認證。 預設值是 `true`。|  
|`type`|字串，指定這個組態項目的型別。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-clientcredentials-element.md)|指定用來對服務驗證用戶端的憑證。 此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>。|  
|[\<httpDigest>](httpdigest-element.md)|指定用來對服務驗證用戶端的摘要。 此項目的型別為 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>。|  
|[\<issuedToken>](issuedtoken.md)|指定用來對安全性權杖服務 (STS) 驗證用戶端的自訂權杖型別。 此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>。|  
|[\<peer>](peer-of-clientcredentials-element.md)|指定目前的對等認證。 此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|指定用來對用戶端驗證服務的憑證，並提供設定憑證選項的結構。 當超出服務至用戶端的範圍時，就必須提供此憑證。 此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>。|  
|[\<windows>](windows-of-clientcredentials-element.md)|指定 Windows 認證。 預設為目前執行緒的認證。 此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsClientElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|指定端點行為。|  
  
## <a name="remarks"></a>備註  

 在需要雙向驗證的情況下，用戶端認證可用於驗證服務的用戶端。 在用戶端必須以服務的憑證保護傳遞給服務的訊息時，這個組態區段也可以用來指定服務憑證。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [安全性行為](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [確保用戶端的安全](../../../wcf/securing-clients.md)
