---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 0f5eace346fd0ed2c0532fb602585c4593d97291
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756685"
---
# <a name="identity"></a>\<identity>
身分識別項目允許用戶端開發人員在設計階段指定服務的預期身分識別。 在用戶端與服務之間的信號交換過程中的 Windows Communication Foundation (WCF) 基礎結構可確保預期的服務符合這個元素的值的身分識別，且因此可進行驗證。 如需詳細資訊，請參閱 <<c0> [ 服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
 \<system.ServiceModel>  
\<client>  
\<endpoint>  
  
## <a name="syntax"></a>語法  
  
```xml  
<identity>
  <certificate encodedValue="String" />
  <certificateReference findValue="String"
                        isChainIncluded="Boolean"
                        storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                        storeLocation="LocalMachine/CurrentUser"
                        X509FindType="Enumeration" />
  <dns value="String" />
  <rsa value="String" />
  <servicePrincipalName value="String" />
  <usePrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|憑證|指定 X.509 憑證的設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.CertificateElement>。 它包含是字串的屬性 `encodedValue`，指定由此憑證編碼的值。|  
|certificateReference|指定 X.509 憑證驗證的設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>。|  
|dns|指定用來驗證服務之 X.509 憑證的 DNS。 這個項目包含是字串的屬性 `value`，而且包含實際的身分識別。|  
|rsa|指定 X.509 憑證的 RSA 欄位值，此憑證可用來驗證用戶端的服務。 這個項目包含是字串的屬性 `value`，而且包含實際的身分識別。|  
|servicePrincipalName|指定伺服器主要名稱 (SPN) 身分識別，也就是用戶端可唯一識別服務執行個體時所用的主要名稱。 這個項目包含是字串的屬性 `value`，而且包含實際的主要名稱。 此項目的型別為 <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>。|  
|userPrincipalName|指定使用者主要名稱 (UPN) 身分識別，也就是網路上使用者的登入名稱類型。 使用者主體名稱包含使用者物件名稱後面加上的 Active Directory 中使用 at 符號 (\@)，然後一般而言，網域名稱系統父系網域。 例如，Fabrikam.com 網域樹狀目錄中的 Jeff 可能會有使用者主體名稱[ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com)。  這個項目包含是字串的屬性 `value`，而且包含實際的主要名稱。 此項目的型別為 <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<custom>](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|指定 netPeerTcpBinding 的自訂對等解析程式。|  
|[\<endpoint>](endpoint-element.md)|設定服務端點。|  
|[\<端點 > 的\<用戶端 >](endpoint-of-client.md)|設定通道端點。|  
|[\<issuer>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|指定聯合服務的安全性權杖服務 (STS)。|  
|[\<issuerMetadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|為聯合服務的安全性權杖服務 (STS) 指定中繼資料端點。|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|定義自訂繫結中已發行權杖的參數。|  
|[\<localIssuer>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|指定本機安全性權杖服務 (STS)。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [端點：位址、 繫結和合約](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
