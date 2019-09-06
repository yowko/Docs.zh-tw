---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 782ca3344774b8412a18e3cf13bff5f969751ea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252148"
---
# <a name="certificatereference"></a>\<certificateReference>
指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateReference >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|storeName|X.509 憑證存儲的名稱。 預設值為 "My"。 選擇性。|  
|storeLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 x.509 憑證存放區的位置。 預設值為 "LocalMachine"。 選擇性。|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType>值，指定要執行的搜尋類型。 預設值為 "FindBySubjectDistinguishedName"。 選擇性。|  
|findValue|要在 X.509 憑證存放區內搜尋的值。 選擇性。|  
|isChainIncluded|指定是否應該使用憑證鏈來執行驗證。 預設值為 "true";驗證是使用憑證鏈來執行。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|設定用來加密和解密權杖的憑證。|  
  
## <a name="remarks"></a>備註  
 `<certificateReference>`元素會指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。 當它指定為專案的子`<serviceCertificate>`專案時，它會指定用來加密和解密權杖之 x.509 憑證的位置和驗證設定。 `<certificateReference>`元素是<xref:System.ServiceModel.Configuration.CertificateReferenceElement>由類別表示。
