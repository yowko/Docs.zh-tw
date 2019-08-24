---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 262ac9be6d5ce6466cf9aff33c0c2791c0e149dd
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988384"
---
# <a name="identity"></a>\<身分識別 >
身分識別項目允許用戶端開發人員在設計階段指定服務的預期身分識別。 在用戶端和服務之間的交握程式中, Windows Communication Foundation (WCF) 基礎結構將確保預期服務的身分識別符合此元素的值, 因此可以進行驗證。 如需詳細資訊, 請參閱[服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。  
  
 \<system.ServiceModel>  
\<用戶端 >  
\<端點 >  
  
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
  <userPrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|憑證 (certificate)|指定 X.509 憑證的設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.CertificateElement>。 它包含是字串的屬性 `encodedValue`，指定由此憑證編碼的值。|  
|certificateReference|指定 X.509 憑證驗證的設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>。|  
|dns|指定用來驗證服務之 X.509 憑證的 DNS。 這個項目包含是字串的屬性 `value`，而且包含實際的身分識別。|  
|rsa|指定 X.509 憑證的 RSA 欄位值，此憑證可用來驗證用戶端的服務。 這個項目包含是字串的屬性 `value`，而且包含實際的身分識別。|  
|servicePrincipalName|指定伺服器主要名稱 (SPN) 身分識別，也就是用戶端可唯一識別服務執行個體時所用的主要名稱。 這個項目包含是字串的屬性 `value`，而且包含實際的主要名稱。 此項目的型別為 <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>。|  
|userPrincipalName|指定使用者主要名稱 (UPN) 身分識別，也就是網路上使用者的登入名稱類型。 使用者主體名稱包含 Active Directory 中使用的使用者物件名稱, 後面接著 at 符號 (\@), 然後通常是網域名稱系統父系網域。 例如, Fabrikam.com 網域樹狀結構中的 Jeff 可能會有使用者主體名稱[jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com)。  這個項目包含是字串的屬性 `value`，而且包含實際的主要名稱。 此項目的型別為 <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<custom>](custom.md)|指定 netPeerTcpBinding 的自訂對等解析程式。|  
|[\<endpoint>](endpoint-element.md)|設定服務端點。|  
|[\<用戶端 > \<的端點 >](endpoint-of-client.md)|設定通道端點。|  
|[\<issuer>](issuer.md)|指定聯合服務的安全性權杖服務 (STS)。|  
|[\<issuerMetadata>](issuermetadata.md)|為聯合服務的安全性權杖服務 (STS) 指定中繼資料端點。|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|定義自訂繫結中已發行權杖的參數。|  
|[\<localIssuer>](localissuer.md)|指定本機安全性權杖服務 (STS)。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)
- [終點位址、系結和合約](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
