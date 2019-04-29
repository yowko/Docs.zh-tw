---
title: <defaultCertificate> 項目
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: c94531d10b7c0ef5ca0ee1f2d5683d0a259a2537
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644452"
---
# <a name="defaultcertificate-element"></a>\<defaultCertificate > 項目
指定服務或 STS 不透過交涉通訊協定提供憑證時要使用的 X.509 憑證。  
  
 \<system.ServiceModel>  
\<behaviors>  
endpointBehaviors 區段  
\<behavior>  
\<clientCredentials>  
\<serviceCertificate>  
\<defaultCertificate>  
  
## <a name="syntax"></a>語法  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|findValue|字串。 要搜尋的值。|  
|x509FindType|列舉。 要搜尋的其中一個憑證欄位。|  
|storeLocation|列舉。 搜尋兩個系統存放位置中的一個。|  
|storeName|列舉。 搜尋的其中一個系統存放區。|  
  
## <a name="findvalue-attribute"></a>findValue 屬性  
  
|值|描述|  
|-----------|-----------------|  
|String|這個值取決於要搜尋的欄位 (由 X509FindType 屬性指定)。 例如，如果搜尋指紋，則此值必須是十六進位數字字串。|  
  
## <a name="x509findtype-attribute"></a>x509FindType 屬性  
  
|值|描述|  
|-----------|-----------------|  
|列舉|這些值包括：FindByThumbprint、 FindBySubjectName、 FindBySubjectDistinguishedName、 FindByIssuerName、 FindByIssuerDistinguishedName、 FindBySerialNumber、 FindByTimeValid、 FindByTimeNotYetValid、 FindBySerialNumber、 FindByTimeExpired、 FindByTemplateNameFindByApplicationPolicy、 FindByCertificatePolicy、 FindByExtension、 FindByKeyUsage、 FindBySubjectKeyIdentifier。|  
  
## <a name="storelocation-attribute"></a>storeLocation 屬性  
  
|值|描述|  
|-----------|-----------------|  
|列舉|CurrentUser 或 LocalMachine。|  
  
## <a name="storename-attribute"></a>storeName 屬性  
  
|值|描述|  
|-----------|-----------------|  
|列舉|這些值包括：AddressBook、 AuthRoot、 CertificateAuthority、 Disallowed、 My、 Root、 TrustedPeople 和 TrustedPublisher。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|指定對用戶端驗證服務時所使用的憑證。|  
  
## <a name="remarks"></a>備註  
 對於使用以憑證為基礎之訊息安全性的繫結，這個組態項目指定的憑證會用來加密傳送給服務的訊息，而且預期會由服務用來簽署對用戶端的回覆。 它會儲存當服務未指定憑證時所要使用的單一憑證。  
  
## <a name="example"></a>範例  
 下列範例會指定要用於的端點 URI 開頭憑證 `http://www.contoso.com` 和要針對所有其他不執行憑證交涉的端點使用的憑證。  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [\<authentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)
- [保護用戶端安全](../../../../../docs/framework/wcf/securing-clients.md)
- [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
