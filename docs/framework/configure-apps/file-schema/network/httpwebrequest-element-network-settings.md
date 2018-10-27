---
title: '&lt;httpWebRequest&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: 586b3e7219c72b6cd00653d6d0be3a74f6359709
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50048979"
---
# <a name="lthttpwebrequestgt-element-network-settings"></a>&lt;httpWebRequest&gt;項目 （網路設定）
自訂 Web 要求參數。  
  
 \<configuration>  
\<system.net>  
\<設定 >  
\<httpWebRequest >  
  
## <a name="syntax"></a>語法  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|**屬性**|**描述**|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|指定回應標頭的最大長度，以 kb 為單位。 預設值為 64。 -1 值表示沒有大小限制，將會加諸於回應標頭。|  
|`maximumErrorResponseLength`|指定錯誤回應，最大的長度，以 kb 為單位。 預設值為 64。 -1 值表示沒有大小限制，將會加諸於錯誤回應。|  
|`maximumUnauthorizedUploadLength`|指定上傳的最大長度，以回應未經授權之錯誤碼，以位元組為單位。 預設值為 -1。 -1 值表示沒有大小限制，將會加諸於上傳。|  
|`useUnsafeHeaderParsing`|指定是否啟用不安全的標頭的剖析。 預設值是 `false`。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  
 根據預設，.NET Framework 嚴格強制 RFC 2616 的 URI 剖析。 某些伺服器的回應可能包含控制字元，禁止在欄位中，這會導致<xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType>方法會擲回<xref:System.Net.WebException>。 如果**useUnsafeHeaderParsing**設為 **，則為 true**，<xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType>在此情況下，但是不會擲回，您的應用程式將會有數種形式的 URI 剖析攻擊弱點。 若要變更伺服器，以便回應不包含控制字元是最佳的解決方案。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定更大的正常最大的標頭的長度。  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
