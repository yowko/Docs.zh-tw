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
ms.openlocfilehash: 94858f141e7d540454fca9c151c760c37f9ebbb0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697951"
---
# <a name="proxy-element-network-settings"></a>@no__t 0proxy > 元素（網路設定）
定義 Proxy 伺服器。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<proxy >**  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|**屬性**|**描述**|  
|-------------------|---------------------|  
|`autoDetect`|指定是否自動偵測到 proxy。 預設值為 `unspecified`。|  
|`bypassonlocal`|指定是否略過本機資源的 proxy。 本機資源包括本機伺服器（`http://localhost`、`http://loopback` 或 `http://127.0.0.1`），以及沒有句號（`http://webserver`）的 URI。 預設值為 `unspecified`。|  
|`proxyaddress`|指定要使用的 proxy URI。|  
|`scriptLocation`|指定設定腳本的位置。 請勿使用此屬性的 `bypassonlocal` 屬性。 |  
|`usesystemdefault`|指定是否要使用 Internet Explorer proxy 設定。 如果設定為 `true`，後續的屬性會覆寫 Internet Explorer proxy 設定。 預設值為 `unspecified`。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。|  
  
## <a name="text-value"></a>文字值  
  
## <a name="remarks"></a>備註  
 @No__t-0 元素會定義應用程式的 proxy 伺服器。 如果設定檔中缺少此元素，則 .NET Framework 會使用 Internet Explorer 中的 proxy 設定。  
  
 @No__t-0 屬性的值應該是格式正確的統一資源指標（URI）。  
  
 @No__t-0 屬性指的是 proxy 設定腳本的自動偵測。 在 Internet Explorer 中選取 [**使用自動設定腳本**] 選項時，@no__t 0 類別會嘗試尋找設定腳本（通常是名為 Wpad. dat）。 如果 `bypassonlocal` 設定為任何值，則會忽略 `scriptLocation`。
  
 針對要遷移至2.0 版的 .NET Framework 1.1 版應用程式，請使用 `usesystemdefault` 屬性。  
  
 如果 `proxyaddress` 屬性指定了不正確預設 proxy，就會擲回例外狀況（exception）。 例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。  
  
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
