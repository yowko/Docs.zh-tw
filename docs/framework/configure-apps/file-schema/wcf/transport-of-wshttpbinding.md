---
title: <transport> 的 <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: ea025751020d6d98292f6bc3ecfe9421af0cb793
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372317"
---
# <a name="transport-of-wshttpbinding"></a>\<transport> of \<wsHttpBinding>

定義 HTTP 傳輸的驗證設定。

\<system.serviceModel>\
\<bindings>\
\<wsHttpBinding>\
\<binding>\
\<安全性 > \
\<transport>

## <a name="syntax"></a>語法

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a>類型

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`clientCredentialType`|指定用來對服務驗證用戶端的認證。 此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。|
|`proxyCredentialType`|指定用來對網域 Proxy 驗證用戶端的認證。 此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。|
|`realm`|指定摘要式驗證或基本驗證之驗證領域的字串。 預設為空字串。<br /><br /> 驗證領域至少會指定負責執行驗證之主機的名稱， 也可以指定具有存取權之使用者的集合。 使用者可以查詢驗證領域，以確定可以使用的其中一組使用者名稱和密碼。|
|`policyEnforcement`|此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。<br /><br /> 1.Never：絕不強制執行此原則 (延伸保護已停用)。<br />2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。<br />3.Always：一律強制執行此原則。 不支援延伸保護的用戶端將無法驗證。|

## <a name="clientcredentialtype-attribute"></a>clientCredentialType 屬性

|值|描述|
|-----------|-----------------|
|`None`|停用安全性。|
|`Basic`|使用基本驗證。|
|`Digest`|使用摘要式驗證。|
|`Ntlm`|使用 NTLM 驗證做為 Windows 網域的後援。|
|`Windows`|使用整合式 Windows 驗證。|
|`Certificate`|使用 X.509 憑證來驗證用戶端。|

## <a name="proxycredentialtype-attribute"></a>proxyCredentialType 屬性

|值|描述|
|-----------|-----------------|
|`None`|停用安全性。|
|`Basic`|使用基本驗證。|
|`Digest`|使用摘要式驗證。|
|`Ntlm`|使用 NTLM 做為 Windows 網域的後援。|
|`Windows`|使用整合式 Windows 驗證。|
|`Certificate`|使用 X.509 憑證來驗證用戶端。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|代表的安全性功能[ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。|

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
