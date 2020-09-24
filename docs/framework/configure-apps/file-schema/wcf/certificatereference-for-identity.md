---
title: <certificateReference> 為 <identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: f3daa2dcdf9b464b51cfb9c883cbb828bccb42df
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148993"
---
# <a name="certificatereference-for-identity"></a>\<certificateReference> 為 \<identity>

指定 X.509 憑證驗證的設定。 使用這個身分識別連接到端點的 WCF) 用戶端 (的安全 Windows Communication Foundation，會確認伺服器提供的宣告是否包含用來建立此身分識別的身分識別宣告。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<certificateReference findValue="String"
                      isChainIncluded="Boolean"
                      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                      storeLocation="LocalMachine/CurrentUser"
                      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier">
</certificateReference>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|findValue|指定要在 X.509 憑證存放區中搜尋的值。 這個屬性所包含的型別必須滿足指定之 `X509FindType` 值的需求。 預設值是空字串。|  
|isChainIncluded|布林值，這個值會指定是否使用憑證鏈結完成驗證。|  
|storeLocation|指定用戶端可用來驗證伺服器憑證之憑證存放區的位置。<br /><br /> 有效值如下：<br /><br /> -LocalMachine：指派給本機電腦的憑證存放區。<br />-CurrentUser：指派給目前使用者的憑證存放區。<br /><br /> 預設值為 LocalMachine。<br /><br /> 此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。|  
|storeName|指定要開啟之 X.509 憑證存放區的名稱。<br /><br /> 有效值如下：<br /><br /> -AddressBook：其他使用者的憑證存放區。<br />-AuthRoot：協力廠商憑證授權單位單位的憑證存放區 (CAs) 。<br />-CertificateAuthority：中繼 Ca 的憑證存放區。<br />-不允許：撤銷憑證的憑證存放區。<br />-My：個人憑證的憑證存放區。<br />-Root：根信任 Ca 的憑證存放區。<br />-TrustedPeople：直接信任之人員和資源的憑證存放區。<br />-TrustedPublisher：直接信任之發行者的憑證存放區。<br /><br /> 預設值為 My。<br /><br /> 此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreName>。|  
|X509FindType|指定要執行之 X.509 搜尋的型別。 `findValue` 屬性所包含的型別必須滿足指定之 X509FindType 的需求。<br /><br /> 有效值如下：<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />- FindByTimeValid<br />- FindByTimeNotYetValid<br />- FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />- FindBySubjectKeyIdentifier<br /><br /> 預設值為 FindBySubjectDistinguishedName。<br /><br /> 此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509FindType>。|  
  
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
