---
title: '&lt;messageSenderAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: 9588ba191ef9f52cb81e52c0b8cf0b423fcaf1fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ltmessagesenderauthenticationgt"></a>&lt;messageSenderAuthentication&gt;
為訊息寄件者使用的對等憑證指定驗證設定。  
  
 \<system.ServiceModel>  
\<行為 >  
\<serviceBehaviors>  
\<行為 >  
\<serviceCredentials>  
\<對等 >  
\<messageSenderAuthentication>  
  
## <a name="syntax"></a>語法  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`certificateValidationMode`|選擇性列舉。 指定用來驗證認證的五個模式之一。 此屬性的型別為 <xref:System.ServiceModel.Security.X509CertificateValidationMode>。 如果設定為 `Custom`，也必須提供 `customCertificateValidator`。|  
|`customCertificateValidatorType`|選擇性字串。 指定用來驗證自訂型別的型別和組件。 當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。 此屬性的型別為 <xref:System.IdentityModel.Selectors.X509CertificateValidator>。 Windows Communication Foundation (WCF) 提供預設的對等憑證驗證程式，用來驗證對等憑證，針對受信任的人存放區。 它也會驗證憑證鏈結直到有效根憑證。 您可以實作自訂的驗證程式以指定不同的行為，並使用這個屬性指向自訂的驗證程式。|  
|`revocationMode`|選擇性列舉。 指定憑證撤銷模式。 此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。 系統會在撤銷憑證清單中查詢，以確認對等憑證尚未被撤銷。 這項檢查可以藉由線上檢查或是針對快取的撤銷清單來執行。 將此屬性設定為 NoCheck 可以關閉撤銷檢查。|  
|`trustedStoreLocation`|選擇性列舉。 指定對等憑證驗證 WCF 安全性系統所信任的存放區位置。 此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<peer>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|指定對等節點的目前認證。|  
  
## <a name="remarks"></a>備註  
 如果已選取訊息驗證，則必須設定這個項目。 輸出通道的每個訊息會使用簽章所提供的憑證[\<憑證 >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)。 所有訊息在傳遞至應用程式之前，都會使用這個項目的 `customCertificateValidatorType` 之屬性所指定的驗證程式來檢查訊息認證。 驗證器可接受或拒絕認證。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [對等通道訊息驗證](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [對等通道自訂驗證](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [保護對等通道應用程式的安全](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
