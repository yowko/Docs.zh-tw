---
title: <authentication> 項目的 <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: b96d53312d672eebd67de82f69cd9a0a2b5bd22e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117753"
---
# <a name="authentication-of-servicecertificate-element"></a>\<驗證 > 的\<v > 項目
指定用戶端 Proxy 用來驗證服務憑證的設定，而這份憑證是使用 SSL/TLS 交涉所取得。  
  
 \<system.ServiceModel>  
\<behaviors>  
endpointBehaviors 區段  
\<behavior>  
\<clientCredentials>  
\<serviceCertificate>  
\<驗證 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|customCertificateValidatorType|字串。 用來驗證自訂型別的型別和組件。|  
|certificateValidationMode|指定用來驗證認證之三個模式的其中一個。 如果設定為 `Custom`，也必須提供 customCertificateValidator。 預設為 `ChainTrust`。|  
|revocationMode|用於檢查撤銷憑證清單 (CRL) 的模式之一。 預設為 `Online`。|  
|trustedStoreLocation|兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。 當與用戶端交涉服務憑證時，會使用這個值。 針對執行驗證**受信任的人**將儲存在指定的存放區位置。 預設為 `CurrentUser`。|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator 屬性  
  
|值|描述|  
|-----------|-----------------|  
|String|指定型別名稱和組件以及用來尋找此型別的其他資料。|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode 屬性  
  
|值|描述|  
|-----------|-----------------|  
|列舉|下列其中一個值：None、 PeerTrust、 ChainTrust、 PeerOrChainTrust、 Custom。<br /><br /> 如需詳細資訊，請參閱 < [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。|  
  
## <a name="revocationmode-attribute"></a>revocationMode 屬性  
  
|值|描述|  
|-----------|-----------------|  
|列舉|下列其中一個值：NoCheck、 Online、 Offline。<br /><br /> 如需詳細資訊，請參閱 < [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation 屬性  
  
|值|描述|  
|-----------|-----------------|  
|列舉|下列其中一個值：LocalMachine 或 CurrentUser。 預設為 CurrentUser。 如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 LocalMachine 之下。 如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 CurrentUser 中。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|指定對用戶端驗證服務時所使用的憑證。|  
  
## <a name="remarks"></a>備註  
 這個組態項目的 `certificateValidationMode` 屬性會指定用來驗證憑證的信任層級。 根據預設，層級會設為 `ChainTrust`，指定每一個憑證必須出現在鏈結頂端以受信任的憑證授權單位為結尾的憑證階層中。 這是最安全的模式。 您也可以將值設定為 `PeerOrChainTrust`，指定可接受自行發出的憑證 (對等信任)，以及信任鏈結內的憑證。 這個值會在開發及偵錯用戶端和服務時使用，因為自行發出的憑證不需要從受信任的授權單位購買。 部署用戶端時，請改用 `ChainTrust` 值。 您也可以將值設為 `Custom` 或 `None`。 若要使用 `Custom` 值，您必須同時將 `customCertificateValidator` 屬性 (Attribute) 設為可用來驗證憑證的組件與型別。 若要建立自己的自訂驗證程式，您必須繼承自抽象 X509CertificateValidator 類別。 如需詳細資訊，請參閱[如何：建立使用自訂憑證驗證程式服務](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)。  
  
 `revocationMode` 屬性會指定檢查憑證是否已被撤銷的方法。 預設為 `online`，表示會自動檢查該憑證是否已被撤銷。 如需詳細資訊，請參閱 < [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。  
  
## <a name="example"></a>範例  
 下列範例會執行兩個工作。 它先指定網域名稱與端點通訊時要使用用戶端的服務憑證`www.contoso.com`透過 HTTP 通訊協定。 第二，指定驗證時使用的撤銷模式和存放區位置。  
  
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

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [如何：建立使用自訂憑證驗證程式服務](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)
- [保護用戶端安全](../../../../../docs/framework/wcf/securing-clients.md)
- [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
