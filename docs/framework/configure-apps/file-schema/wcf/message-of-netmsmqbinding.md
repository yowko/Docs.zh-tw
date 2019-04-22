---
title: <message> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: c623b7daf1e91c9c1800b9653525cd51b1087506
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58890562"
---
# <a name="message-of-netmsmqbinding"></a>\<message> of \<netMsmqBinding>

定義此 `netMsmqBinding` 繫結上的 SOAP 訊息安全性設定。

```xml
<system.ServiceModel>
  <bindings>
    <netMsmqBinding>
      <binding>
        <security>
          <message>
```

## <a name="syntax"></a>語法

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|algorithmSuite|設定訊息加密和金鑰包裝演算法，用來針對 MSMQ 傳輸上傳送的訊息實現訊息安全性。<br /><br /> 預設值為 `Aes256`。 此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。|
|clientCredentialType|指定在為 MSMQ 傳輸上傳送的訊息執行用戶端驗證時，要使用的認證類型。 有效值包括以下的值：<br /><br /> -None:這會允許服務與匿名用戶端互動。 服務和用戶端都不需要認證。<br />-Windows:這可讓 SOAP 交換加入 Windows 認證的已驗證的內容。 如此一定會執行 Kerberos 驗證。<br />-使用者名稱：這可讓服務要求使用 UserName 認證來驗證用戶端。 認證在此情況下必須使用來指定`clientCredentials`行為**注意：** Windows Communication Foundation (WCF) 不支援傳送密碼摘要或衍生金鑰使用的密碼，並使用訊息安全性這類金鑰。 因此，WCF 會強制使用 UserName 認證時，保護交換。 這個模式需要使用 `clientCredential` 行為和 `serviceCertificate` 在用戶端上指定服務憑證。 <br /><br /> 憑證：這可讓服務要求使用憑證來驗證用戶端。 此案例中的用戶端認證必須使用 `clientCredentials` 行為來指定。 此案例中的服務認證需要藉由指定 `clientCredentials`，以使用 `serviceCertificate` 行為來指定。<br />-CardSpace:這可讓服務要求用戶端使用 CardSpace 來驗證。 `serviceCertificate` 行為中必須提供 `clientCredential`。<br /><br /> 預設值為 `Windows`。 此屬性的型別為 <xref:System.ServiceModel.MessageCredentialType>。|

### <a name="child-elements"></a>子元素

None

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|定義繫結的安全性設定。|

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [WCF 中的佇列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
