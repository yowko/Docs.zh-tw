---
title: <add> 的 <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 325d6b8111115384b18547bd11ccec8a4a8af711
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920117"
---
# <a name="add-of-issuerchannelbehaviors"></a>\<新增 issuerChannelBehaviors > \<的 >

新增與 STS 通訊時要使用的端點行為。

> [!NOTE]
> 如果任何端點行為包含[ \<clientCredentials >](clientcredentials.md)元素, 則會擲回例外狀況。

\<system.ServiceModel>\
\<行為 > \
endpointBehaviors 區段\<行為 > \
\<clientCredentials > \
\<issuedToken > \
\<issuerChannelBehaviors > 元素 \
\<add>

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

|項目|說明|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|包含與指定的服務權杖服務通訊時, 所要使用的 Windows Communication Foundation (WCF) 用戶端端點行為集合。|

## <a name="remarks"></a>備註

`issuerAddress` 包含用戶端想要進行通訊之 Security Token Service 的 URI。 `behaviorConfiguration`指向端點行為, 應用程式會在 Windows Communication Foundation (WCF) 建立的通道中使用該行為, 從安全性權杖服務取得發行的權杖。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)
- [安全性行為](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [同盟與發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [保護服務和用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
- [保護用戶端安全](../../../wcf/securing-clients.md)
- [如何：建立同盟用戶端](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [如何：設定本機簽發者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [同盟與發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
