---
title: "&lt;clientCredentials&gt; 的 &lt;serviceCertificate&gt; 項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3bd2cf4cf96fd2b80fc08523b42bd8aa2379c2d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicecertificategt-of-ltclientcredentialsgt-element"></a>&lt;clientCredentials&gt; 的 &lt;serviceCertificate&gt; 項目
指定對用戶端驗證服務時所使用的憑證。  
  
 \<系統。ServiceModel >  
\<行為 >  
\<endpointBehaviors >  
\<行為 >  
\<clientCredentials >  
\<serviceCertificate >  
  
## <a name="syntax"></a>語法  
  
```xml  
<serviceCertificate />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<defaultCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|指定服務或 STS 不透過交涉通訊協定提供憑證時要使用的 X.509 憑證。|  
|[\<但是在 scopedCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|表示特定服務 (範圍服務) 為驗證所提供之 X.509 憑證的集合。 這個集合通常用來指定聯合案例中安全性權杖服務的服務憑證。|  
|[\<驗證 >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|為用戶端使用的服務憑證指定驗證行為。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|指定用戶端用來對服務驗證本身的認證。|  
  
## <a name="remarks"></a>備註  
 這個組態項目會指定用戶端用來驗證憑證的設定，而這份憑證是由使用 SSL 驗證的服務所提供。 它另外包含的任何憑證，可讓已明確設定於用戶端上的服務在使用訊息安全性時用於加密傳給服務的訊息。  
  
 屬性的`serviceCertificate`項目是屬性的相同[ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [保護用戶端安全](../../../../../docs/framework/wcf/securing-clients.md)  
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [保護服務和用戶端](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
