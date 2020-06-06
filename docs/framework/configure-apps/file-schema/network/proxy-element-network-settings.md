---
title: <proxy> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154786"
---
# <a name="proxy-element-network-settings"></a>\<proxy> 項目 (網路設定)
定義 Proxy 伺服器。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a>語法  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|**屬性**|**說明**|  
|-------------------|---------------------|  
|`autoDetect`|指定是否自動偵測 Proxy。 預設值是 `unspecified`。|  
|`bypassonlocal`|指定是否略過本機資源的 Proxy。 本機資源包括本機伺服器（ `http://localhost` 、 `http://loopback` 或 `http://127.0.0.1` ），以及沒有句號（）的 URI `http://webserver` 。 預設值是 `unspecified`。|  
|`proxyaddress`|指定要使用的 proxy URI。|  
|`scriptLocation`|指定設定腳本的位置。 請勿使用屬性搭配 `bypassonlocal` 這個屬性。 |  
|`usesystemdefault`|指定是否要使用 Internet Explorer proxy 設定。 如果設定為 `true` ，後續的屬性會覆寫 Internet Explorer proxy 設定。 預設值是 `unspecified`。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**元素**|**說明**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。|  
  
## <a name="text-value"></a>文字值  
  
## <a name="remarks"></a>備註  
 `proxy`元素會定義應用程式的 proxy 伺服器。 如果設定檔中缺少此元素，則 .NET Framework 會使用 Internet Explorer 中的 proxy 設定。  
  
 屬性的值應該是格式正確的 `proxyaddress` 統一資源指標（URI）。  
  
 `scriptLocation`屬性會參考 proxy 設定腳本的自動偵測。 <xref:System.Net.WebProxy>當 Internet Explorer 中選取了 [**使用自動設定腳本**] 選項時，類別會嘗試尋找設定腳本（通常是名為 Wpad. dat）。 如果 `bypassonlocal` 設定為任何值， `scriptLocation` 則會忽略。
  
 針對要 `usesystemdefault` 遷移至2.0 版的 .NET Framework 版本1.1 應用程式，請使用屬性。  
  
 如果 `proxyaddress` 屬性指定了不正確預設 proxy，則會擲回例外狀況。 例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會使用 Internet Explorer proxy 的預設值、指定 proxy 位址，並略過 proxy 以進行本機存取。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [網路設定結構描述](index.md)
