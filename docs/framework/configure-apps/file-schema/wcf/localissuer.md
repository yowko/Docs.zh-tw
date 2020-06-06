---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397868"
---
# \<localIssuer>
指定要用來取得安全性權杖的本機簽發者位址和繫結。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|address|必要字串。 指定本機簽發者的 URI。|  
|繫結|選擇性字串。 系統提供的繫結之一。 如需清單，請參閱[系統提供](../../../wcf/system-provided-bindings.md)的系結。|  
|bindingConfiguration|選擇性字串。 指定組態檔中的繫結組態。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<identity>](identity.md)|指定本機簽發者的身分識別資訊。|  
|[\<headers>](headers-element.md)|位址標頭集合，這些位址標頭是正確定址本機簽發者時的必要項目。 您可以使用 `add` 關鍵字將標頭加入這個集合。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|指定用來向服務驗證用戶端的自訂權杖。|  
  
## <a name="remarks"></a>備註  
 當取得某個安全性權杖服務 (STS) 所核發的權杖時，用戶端應用程式必須以特定位址和繫結完成設定，才能與該 STS 進行通訊。 當未 <xref:System.ServiceModel.WSFederationHttpBinding> 提供 Security Token Service 的 URL，或同盟系結的簽發者位址是 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` 或時 `null` ，用戶端的 Windows Communication Foundation （WCF）通道會使用和所指定的值 `address` `binding` 來與 STS 通訊，以取得發行的權杖。 如需設定本機簽發者的詳細資訊，請參閱[如何：設定本機簽發者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)。  
  
## <a name="example"></a>範例  
 下列範例會設定 `address` 項目的 `binding`、`bindingConfiguration` 和 `localIssuer` 屬性。  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [安全性行為](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [HOW TO：設定本機簽發者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)
- [安全性行為](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [聯合與發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [保護用戶端安全](../../../wcf/securing-clients.md)
- [如何：建立同盟用戶端](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [聯合與發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)
