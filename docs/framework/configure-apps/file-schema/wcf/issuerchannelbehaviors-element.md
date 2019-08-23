---
title: <issuerChannelBehaviors> 項目
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: e0e41b4f6d66cd4455c43dda7c77798553f2b58f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929932"
---
# <a name="issuerchannelbehaviors-element"></a>\<issuerChannelBehaviors > 元素

包含 Windows Communication Foundation (WCF) 用戶端端點行為 (定義于設定中) 的集合, 以便在與指定的服務權杖服務通訊時使用。 定義的行為不能包含任何[ \<clientCredentials >](clientcredentials.md)元素。

```xml
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior>
        <clientCredentials>
          <issuedToken>
            <issuerChannelBehaviors>
```

## <a name="syntax"></a>語法

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|項目|說明|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|將行為新增至集合中。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[\<issuedToken>](issuedtoken.md)|指定用來向服務驗證用戶端的自訂權杖。|

## <a name="remarks"></a>備註

當在必須使用任何行為 (包含 `<clientCredentials>` 項目之行為以外的任何行為) 與服務進行通訊時，請使用此項目。 例如, 如果必須包含[ \<dataContractSerializer >](datacontractserializer-element.md)行為元素, 則為。

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
