---
title: <add> 的 <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398324"
---
# <a name="add-of-issuerchannelbehaviors"></a>\<add> 的 \<issuerChannelBehaviors>

新增與 STS 通訊時要使用的端點行為。

> [!NOTE]
> 如果任何端點行為包含 [\<clientCredentials>](clientcredentials.md) 元素，則會擲回例外狀況。

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a>語法

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子元素和父元素

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|issuerAddress|要與其進行通訊之安全性權杖簽發者的 URI。|
|behaviorConfiguration|相同組態檔中定義之端點行為的名稱。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|包含與指定的服務權杖服務通訊時，所要使用的 Windows Communication Foundation （WCF）用戶端端點行為集合。|

## <a name="remarks"></a>備註

`issuerAddress` 包含用戶端想要進行通訊之 Security Token Service 的 URI。 `behaviorConfiguration`指向端點行為，應用程式會在 Windows Communication Foundation （WCF）建立的通道中使用該行為，從安全性權杖服務取得發行的權杖。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)
- [安全性行為](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [聯合與發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [保護用戶端安全](../../../wcf/securing-clients.md)
- [如何：建立同盟用戶端](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [HOW TO：設定本機簽發者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [聯合與發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
