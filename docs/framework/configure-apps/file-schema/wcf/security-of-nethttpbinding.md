---
title: <security> 的 <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: f2750036aa4d3fbe41062ad041e50ff3a4be32b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670556"
---
# <a name="security-of-nethttpbinding"></a>\<安全性 > 的\<netHttpBinding >

定義的安全性功能[ \<basicHttpBinding >](basichttpbinding.md)。

\<system.ServiceModel>\
\<bindings>\
\<netHttpBinding>\
\<binding>\
\<安全性 >

## <a name="syntax"></a>語法

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|模式|選擇性。 指定使用的安全性類型。 預設為 `None`。 此屬性的型別為 <xref:System.ServiceModel.BasicHttpSecurityMode>。|

## <a name="mode-attribute"></a>mode 屬性

|值|描述|
|-----------|-----------------|
|None|訊息在傳輸期間並未受到保護。|
|Transport|會使用 HTTPS 傳輸來提供安全性。 SOAP 訊息是使用 HTTPS 來保護其安全。 對用戶端驗證服務時，則是使用服務的 X.509 憑證。 用戶端會透過提供的 ClientCredentialType 來驗證。|
|訊息|系統會使用 SOAP 訊息安全性來提供安全性。 根據預設，本文會經過加密與簽署。 對於此繫結，系統會要求將伺服器憑證提供給超出範圍的用戶端。 這個繫結唯一有效的 `ClientCredentialType` 是 `Certificate`。|
|TransportWithMessageCredential|完整性、機密性與伺服器驗證都是經由傳輸安全性來提供。 用戶端驗證是透過 SOAP 訊息安全性的方式提供。 當使用者是透過使用者名稱/密碼進行驗證，且有現有的 HTTP 部署來保護訊息傳輸的安全時，即與此模式有關。|
|TransportCredentialOnly|這個模式不提供訊息完整性和機密性， 但會提供 HTTP 架構的用戶端驗證。 請謹慎使用這個模式， 它應該用於提供的環境中以其他方式 （例如 IPSec) 提供傳輸安全性，且只有用戶端驗證是由 WCF 基礎結構。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|定義基本 HTTP 服務的傳輸安全性設定。 這個項目對應於 <xref:System.ServiceModel.HttpTransportSecurity>。|
|[\<message>](message-of-nethttpbinding.md)|定義基本 HTTP 服務的訊息安全性設定。 這個項目對應於 <xref:System.ServiceModel.BasicHttpMessageSecurity>。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|繫結|繫結項目[ \<basicHttpBinding >](basichttpbinding.md)。|

## <a name="remarks"></a>備註

 根據預設，SOAP 訊息並不安全，而且用戶端也尚未經過驗證。 這個項目可讓您設定 `netHttpBinding` 項目的其他安全性設定。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [保護服務和用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
- [選取認證類型](../../../wcf/feature-details/selecting-a-credential-type.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
