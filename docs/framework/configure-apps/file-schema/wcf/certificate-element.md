---
title: <certificate> 項目
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: eea8130911ca3780a6e4e753c17877e58c50b139
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704319"
---
# <a name="certificate-element"></a>\<憑證 > 項目
指定要用來簽署與加密對等用戶端之訊息的 X.509 憑證。  
  
 \<system.ServiceModel>  
\<behaviors>  
\<endpointBehaviors>  
\<behavior>  
\<clientCredentials>  
\<peer>  
\<certificate>  
  
## <a name="syntax"></a>語法  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`findValue`|字串，其中包含要在 X.509 憑證存放區內搜尋的值。 屬性所包含的型別必須滿足指定之 `x509FindType` 的需求。 預設為空字串。|  
|`storeLocation`|指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區針對這個位置驗證對等的憑證。 有效值包括以下的值：<br /><br /> -LocalMachine: 指派憑證存放區到本機電腦。<br />-CurrentUser: 指派憑證存放區目前的使用者。<br /><br /> 預設為 LocalMachine。|  
|`storeName`|指定要開啟之 X.509 憑證存放區的名稱。 有效值包括以下的值：<br /><br /> -AddressBook:其他使用者的憑證存放區。<br />-   AuthRoot:第三方憑證授權單位 (Ca) 憑證存放區。<br />-CertificateAuthority:中繼憑證授權單位 (Ca) 憑證存放區。<br />-不允許：已撤銷之憑證的憑證存放區。<br />-我：個人憑證的憑證存放區。<br />根目錄：受信任的根憑證授權單位 (Ca) 憑證存放區。<br />-TrustedPeople:直接信任之人員和資源的憑證存放區。<br />-TrustedPublisher:直接信任之發行者的憑證存放區。<br /><br /> 預設為 My。|  
|`X509FindType`|定義要執行之 X.509 搜尋的類型。 有效值包括以下的值：<br /><br /> -FindByThumbPrint<br />-   FindBySubjectName<br />-   FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> `findValue` 屬性所包含的型別必須滿足指定之 `X509FindType` 的需求。<br /><br /> 預設值為 FindBySubjectDistinguishedName。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<peer>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|指定驗證對等用戶端時所使用的認證。|  
  
## <a name="remarks"></a>備註  
 這個組態項目包含在驗證對等網狀結構中鄰接項目時所使用的 X509Certificate2 執行個體。  
  
 如需端對端程式設計的詳細資訊，請參閱[對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。  
  
## <a name="example"></a>範例  
 下列程式碼說明如何尋找對等案例中使用的憑證。  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [保護對等通道應用程式的安全](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
