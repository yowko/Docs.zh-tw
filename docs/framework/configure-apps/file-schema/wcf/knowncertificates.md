---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 23fe19258e09e9e8a5e05a94ccef0e40ee1cb5fd
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400328"
---
# <a name="knowncertificates"></a>\<knownCertificates>
表示 X.509 憑證的集合，這些憑證是用來驗證由安全性權杖服務 (STS) 發行的安全性認證。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<n >** ](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<knownCertificates >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](add-of-knowncertificates.md)|將 X.509 憑證加入至集合。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|指定發行為服務認證的權杖。|  
  
## <a name="remarks"></a>備註  
 發行之權杖的情況有三個階段。 在第一個階段中，嘗試存取服務的用戶端稱為「*安全權杖服務*」。 此安全權杖服務接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 (SAML) 權杖。 用戶端接著會以權杖傳回服務。 此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。 若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。  
  
 N > 元素是任何此類安全權杖服務憑證的存放庫。 [ \< ](issuedtokenauthentication-of-servicecredentials.md) 若要新增憑證，請使用[ \<knownCertificates > 元素](knowncertificates.md)。 為每個憑證插入「 [新增>，如下列範例所示。\< ](add-of-knowncertificates.md)  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 根據預設，必須從安全權杖服務取得憑證。 這些「已知的」憑證可確保只有合法的用戶端可以存取服務。  
  
 若要檢查同盟服務驗證用戶端所需的條件，以及使用此設定元素的詳細資訊，請參閱[如何：在同盟服務](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)上設定認證。 如需聯合案例的詳細資訊，請參閱[同盟和發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)。  
  
 如需示範如何在設定中填入集合的範例，請參閱[ \<add >](add-of-knowncertificates.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<add>](add-of-knowncertificates.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [安全性行為](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [如何：在同盟服務上設定認證](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [使用憑證](../../../wcf/feature-details/working-with-certificates.md)
- [同盟與發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-knowncertificates.md)
- [保護服務和用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
