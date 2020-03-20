---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152810"
---
# <a name="certificatereference"></a>\<證書參考>
指定用於在憑證存放區中查找和驗證 X.509 憑證的設置。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.身份模型.服務>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<聯合配置>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<服務證書>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<證書參考>**  
  
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
|storeName|X.509 憑證存放區的名稱。 預設值為"我的"。 選擇性。|  
|storeLocation|指定<xref:System.Security.Cryptography.X509Certificates.StoreLocation>X.509 憑證存儲的位置的值。 預設值為"本地電腦"。 選擇性。|  
|x509FindType|指定<xref:System.Security.Cryptography.X509Certificates.X509FindType>要執行的搜索類型的值。 預設值為"查找主題分辨名稱"。 選擇性。|  
|findValue|要在 X.509 憑證存放區內搜尋的值。 選擇性。|  
|isChainIncluded|指定是否應使用憑證連結執行驗證。 預設值為"true";預設值為"true"，為"true"，為"true";為驗證是使用憑證連結執行的。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<服務證書>](servicecertificate.md)|配置用於加密和解密權杖的證書。|  
  
## <a name="remarks"></a>備註  
 該`<certificateReference>`元素指定用於在憑證存放區中查找和驗證 X.509 憑證的設置。 當它指定為`<serviceCertificate>`元素的子項目時，它指定用於加密和解密權杖的 X.509 憑證的位置和驗證設置。 元素`<certificateReference>`由類<xref:System.ServiceModel.Configuration.CertificateReferenceElement>表示。
