---
title: <clientCertificate> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 277e5e33bcc7f9d417da7ce24caa4c6200c23e23
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919544"
---
# <a name="clientcertificate-of-servicecredentials"></a>\<serviceCredentials > 的\<clientCertificate >
定義雙工通訊模式中，用來簽署與加密服務至用戶端之訊息的 X.509 憑證。  
  
 \<system.ServiceModel>  
\<行為 >  
\<serviceBehaviors>  
\<serviceBehaviors>  
\<行為 >  
\<serviceCredentials>  
\<clientCertificate>  
  
## <a name="syntax"></a>語法  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<authentication>](authentication-of-clientcertificate-element.md)|指定用戶端憑證的驗證選項。|  
|[\<certificate>](certificate-of-clientcertificate-element.md)|指定要使用的憑證。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。|  
  
## <a name="remarks"></a>備註  
 當服務必須具有用戶端的憑證才能與用戶端安全地進行通訊時，則會使用這個項目。 這種情況發生在使用雙工通訊模式時。 在較為典型的要求/回應模式中，用戶端會在要求中納入其憑證，服務便使用此憑證加密與簽署其對於用戶端的回應。 然而，在雙工通訊模式中，服務沒有來自用戶端的要求，因此需要用戶端的憑證，進而保護傳送到用戶端的訊息安全。 所以，您必須在超出範圍的交涉中取得用戶端的憑證，並使用此項目指定憑證。 如需雙工服務的詳細資訊[, 請參閱如何:建立雙工合約](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)。  
  
 設定在這個項目中的憑證，只能在繫結是以 `MutualCertificateDuplex` 訊息安全性驗證模式所設定的情況下，才可用來加密傳送給用戶端的訊息。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [如何：建立雙工合約](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [安全性行為](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [使用憑證](../../../wcf/feature-details/working-with-certificates.md)
