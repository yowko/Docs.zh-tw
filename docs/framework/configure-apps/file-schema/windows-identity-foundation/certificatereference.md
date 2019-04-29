---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 6c9c77f96ff6032de43d9b5a257bc0796a19b858
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667375"
---
# <a name="certificatereference"></a>\<certificateReference>
指定用來尋找和驗證 X.509 憑證的憑證存放區中的設定。  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<serviceCertificate>  
\<certificateReference>  
  
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
|storeName|X.509 憑證存放區的名稱。 預設值是"My"。 選擇性。|  
|storeLocation|A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區位置。 預設值為"LocalMachine"。 選擇性。|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType>值，指定所要執行的搜尋的類型。 預設值為"FindBySubjectDistinguishedName 」。 選擇性。|  
|findValue|要在 X.509 憑證存放區內搜尋的值。 選擇性。|  
|isChainIncluded|指定是否應該執行驗證所使用的憑證鏈結。 預設值為"true";使用憑證鏈結，會執行驗證。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|設定用來加密和解密權杖的憑證。|  
  
## <a name="remarks"></a>備註  
 `<certificateReference>`項目會指定用來尋找和驗證 X.509 憑證的憑證存放區中的設定。 指定的子項目為時`<serviceCertficate>`項目，它會指定用來加密和解密權杖的 X.509 憑證的位置和驗證設定。 `<certificateReference>`項目由<xref:System.ServiceModel.Configuration.CertificateReferenceElement>類別。
