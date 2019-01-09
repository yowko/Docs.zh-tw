---
title: '&lt;ServiceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: b9e32509a5e182301455eaf0e602a03c51fbc23a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150769"
---
# <a name="ltservicecredentialsgt"></a>&lt;ServiceCredentials&gt;
指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。  
  
 \<system.ServiceModel>  
\<行為 >  
\<serviceBehaviors>  
\<行為 >  
\<serviceCredentials>  
  
## <a name="syntax"></a>語法  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`type`|字串，指定這個組態項目的型別。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|指定當用戶端憑證可在超出範圍使用時，要使用的憑證。 這個項目也會指定用戶端憑證驗證設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>。|  
|[\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|指定這個服務的目前發行的權杖。 此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>。|  
|[\<peer>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|指定對等節點的目前認證。 此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。|  
|[\<s >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|指定安全對話的目前認證。 此項目的型別為 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>。|  
|[\<v >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|指定服務用來識別本身的憑證。 此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>。|  
|[\<userNameAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|指定使用者名稱密碼驗證的設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.UserNameServiceElement>。|  
|[\<windowsAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|指定 Windows 認證驗證的設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsServiceElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<行為 >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定行為項目。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
