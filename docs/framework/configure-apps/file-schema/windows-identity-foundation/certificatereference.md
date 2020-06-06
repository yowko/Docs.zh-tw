---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152810"
---
# \<certificateReference>
指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
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
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|storeName|X.509 憑證存放區的名稱。 預設值為 "My"。 選擇性。|  
|storeLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 x.509 憑證存放區的位置。 預設值為 "LocalMachine"。 選擇性。|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType>值，指定要執行的搜尋類型。 預設值為 "FindBySubjectDistinguishedName"。 選擇性。|  
|findValue|要在 X.509 憑證存放區內搜尋的值。 選擇性。|  
|isChainIncluded|指定是否應該使用憑證鏈來執行驗證。 預設值為 "true";驗證是使用憑證鏈來執行。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|設定用來加密和解密權杖的憑證。|  
  
## <a name="remarks"></a>備註  
 `<certificateReference>`元素會指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。 當它指定為專案的子專案時 `<serviceCertificate>` ，它會指定用來加密和解密權杖之 x.509 憑證的位置和驗證設定。 `<certificateReference>`元素是由 <xref:System.ServiceModel.Configuration.CertificateReferenceElement> 類別表示。
