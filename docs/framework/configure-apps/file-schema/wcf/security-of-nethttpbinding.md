---
title: "&lt;netHttpBinding 的 &gt;security&lt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63d65ea50babd0cd4aa7ee92cdd6d2b281dcbc26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a>&lt;netHttpBinding 的 &gt;security&lt;
定義的安全性功能[ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)。  
  
 \<系統。ServiceModel >  
\<繫結 >  
\<netHttpBinding >  
\<繫結 >  
\<安全性 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|模式|選擇項。 指定使用的安全性類型。 預設為 `None`。 這個屬性是屬於型別<!--zz <xref:System.ServiceModel.NetHttpSecurityMode> --> `System.ServiceModel.NetHttpSecurityMode`。|
  
## <a name="mode-attribute"></a>mode 屬性  
  
|值|描述|  
|-----------|-----------------|  
|無|傳輸期間並未保護訊息數。|  
|Transport|會使用 HTTPS 傳輸來提供安全性。 SOAP 訊息是使用 HTTPS 來保護其安全。 對用戶端驗證服務時，則是使用服務的 X.509 憑證。 用戶端會透過提供的 ClientCredentialType 來驗證。|  
|訊息|系統會使用 SOAP 訊息安全性來提供安全性。 根據預設，本文會經過加密與簽署。 對於此繫結，系統會要求將伺服器憑證提供給超出範圍的用戶端。 這個繫結唯一有效的 `ClientCredentialType` 是 `Certificate`。|  
|TransportWithMessageCredential|完整性、機密性與伺服器驗證都是經由傳輸安全性來提供。 用戶端驗證是透過 SOAP 訊息安全性的方式提供。 當使用者是透過使用者名稱/密碼進行驗證，且有現有的 HTTP 部署來保護訊息傳輸的安全時，即與此模式有關。|  
|TransportCredentialOnly|這個模式不提供訊息完整性和機密性， 但會提供 HTTP 架構的用戶端驗證。 請謹慎使用這個模式， 它應使用在以其他方式 (如 IPSec) 提供傳輸安全性，且 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 基礎結構只提供用戶端驗證的環境中。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[\<傳輸 >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|定義基本 HTTP 服務的傳輸安全性設定。 這個項目對應於 <xref:System.ServiceModel.HttpTransportSecurity>。|  
|[\<訊息 >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|定義基本 HTTP 服務的訊息安全性設定。 這個項目對應至<!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|繫結|繫結項目[ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)。|  
  
## <a name="remarks"></a>備註  
 根據預設，SOAP 訊息並不安全，而且用戶端也尚未經過驗證。 這個項目可讓您設定 `netHttpBinding` 項目的其他安全性設定。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>    
 [保護服務和用戶端](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [選取認證類型](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [設定系統提供繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [使用繫結來設定 Windows Communication Foundation 服務和用戶端](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<繫結 >](../../../../../docs/framework/misc/binding.md)
