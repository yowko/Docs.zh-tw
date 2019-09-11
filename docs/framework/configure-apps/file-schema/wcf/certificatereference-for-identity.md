---
title: <certificateReference> 的 <identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 93a6290d780ff61756f7315cd0c32f0e199ca00f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849992"
---
# <a name="certificatereference-for-identity"></a>\<身分識別 > \<的 certificateReference >
指定 X.509 憑證驗證的設定。 使用此身分識別連接到端點的安全 Windows Communication Foundation （WCF）用戶端會確認伺服器所提供的宣告是否包含用來建立此身分識別的身分識別宣告。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<用戶端 >** ](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<端點 >** ](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<身分識別 >** ](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateReference >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<certificateReference findValue="String"
                      isChainIncluded="Boolean"
                      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                      storeLocation="LocalMachine/CurrentUser"
                      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier">
</certificateReference>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|findValue|指定要在 X.509 憑證存放區中搜尋的值。 這個屬性所包含的型別必須滿足指定之 `X509FindType` 值的需求。 預設值是空字串。|  
|isChainIncluded|布林值，這個值會指定是否使用憑證鏈結完成驗證。|  
|storeLocation|指定用戶端可用來驗證伺服器憑證之憑證存放區的位置。<br /><br /> 有效值包括以下的值：<br /><br /> LocalMachine指派給本機電腦的憑證存放區。<br />CurrentUser指派給目前使用者的憑證存放區。<br /><br /> 預設值為 LocalMachine。<br /><br /> 此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。|  
|storeName|指定要開啟之 X.509 憑證存放區的名稱。<br /><br /> 有效值包括以下的值：<br /><br /> 通訊錄其他使用者的憑證存放區。<br />AuthRoot協力廠商憑證授權單位單位（Ca）的憑證存放區。<br />CertificateAuthority中繼 Ca 的憑證存放區。<br />禁止已撤銷憑證的憑證存放區。<br />'個人憑證的憑證存放區。<br />路徑信任的根 Ca 的憑證存放區。<br />TrustedPeople直接信任之人員和資源的憑證存放區。<br />TrustedPublisher直接信任之發行者的憑證存放區。<br /><br /> 預設值為 My。<br /><br /> 此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreName>。|  
|X509FindType|指定要執行之 X.509 搜尋的型別。 `findValue` 屬性所包含的型別必須滿足指定之 X509FindType 的需求。<br /><br /> 有效值包括以下的值：<br /><br /> -FindByThumbPrint<br />-   FindBySubjectName<br />-FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />- FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> 預設值為 FindBySubjectDistinguishedName。<br /><br /> 此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509FindType>。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identity>](identity.md)|指定設定，這個設定可讓其他端點與此端點交換訊息時啟用端點驗證。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
