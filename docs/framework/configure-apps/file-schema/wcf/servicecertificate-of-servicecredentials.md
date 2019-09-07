---
title: <serviceCertificate> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: 513dcad7f4325d653df87fe9cc27572c25e153c5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399663"
---
# <a name="servicecertificate-of-servicecredentials"></a>\<serviceCredentials > 的\<serviceCertificate >
指定 X.509 憑證，而此憑證將用以驗證使用訊息安全性模式的用戶端服務。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCertificate >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<serviceCertificate findValue="String"
                    storeLocation="LocalMachine/CurrentUser"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`findValue`|字串，其中包含要在 X.509 憑證存放區內搜尋的值。 屬性所包含的型別必須滿足指定之 X509FindType 的需求。 預設為空字串。|  
|`storeLocation`|指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區來驗證伺服器的憑證。 有效值包括以下的值：<br /><br /> -LocalMachine：指派給本機電腦的憑證存放區。<br />-CurrentUser：指派給目前使用者的憑證存放區。<br /><br /> 預設為 LocalMachine。|  
|`storeName`|指定要開啟之 X.509 憑證存放區的名稱。 有效值包括以下的值：<br /><br /> 通訊錄其他使用者的憑證存放區。<br />AuthRoot協力廠商憑證授權單位單位（Ca）的憑證存放區。<br />- CertificatAuthority:中繼憑證授權單位單位（Ca）的憑證存放區。<br />禁止已撤銷憑證的憑證存放區。<br />'個人憑證的憑證存放區。<br />路徑信任的根憑證授權單位（Ca）的憑證存放區。<br />TrustedPeople直接信任之人員和資源的憑證存放區。<br />TrustedPublisher直接信任之發行者的憑證存放區。<br /><br /> 預設為 My。|  
|`x509FindType`|定義要執行之 X.509 搜尋的類型。 有效值包括以下的值：<br /><br /> -FindByThumbprint<br />-   FindBySubjectName<br />-FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />- FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> `findValue` 屬性所包含的型別必須滿足指定之 X509FindType 的需求。<br /><br /> 預設值為 FindBySubjectDistinguishedName。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。|  
  
## <a name="remarks"></a>備註  
 使用此項目指定 X.509 憑證，而此憑證將用以驗證使用訊息安全性模式的用戶端服務。 如果您使用的是會定期更新的憑證，則其指紋將會變更。 在這種情況下，請使用主體名稱當成 `x509FindType`，因為憑證可以使用相同的主體名稱重新發出。  
  
 如需使用元素的詳細資訊，請[參閱如何：指定用戶端認證](../../../wcf/how-to-specify-client-credential-values.md)值。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>
- [如何：指定用戶端認證值](../../../wcf/how-to-specify-client-credential-values.md)
- [安全性行為](../../../wcf/feature-details/security-behaviors-in-wcf.md)
