---
title: <defaultProxy> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 7e49762ee017564734bfb2b2f7074d94b7eabe11
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659398"
---
# <a name="defaultproxy-element-network-settings"></a>\<defaultProxy > 元素 (網路設定)
設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。  
  
 \<configuration>  
\<system.net>  
\<defaultProxy>  
  
## <a name="syntax"></a>語法  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|`enabled`|指定是否使用 Web Proxy。 預設值為 `true`。|  
|`useDefaultCredentials`|指定此主機的預設認證是否用來存取 Web Proxy。 預設值為 `false`。|  
  
### <a name="child-elements"></a>子元素  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[bypasslist](bypasslist-element-network-settings.md)|提供一組位址的規則運算式，說明不使用 Proxy。|  
|[module](module-element-network-settings.md)|將新的 Proxy 模組加入至應用程式。|  
|[proxy](proxy-element-network-settings.md)|定義 Proxy 伺服器。|  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## <a name="remarks"></a>備註  
 如果 defaultProxy 項目是空的，則會使用來自 Internet Explorer 的 Proxy 設定。 這個行為與 .NET Framework 1.1 版的不同。  
  
 如果[module](module-element-network-settings.md)元素指定非公用類型、類型不是衍生自<xref:System.Net.IWebProxy>類別、這個物件的無參數的函式發生例外狀況, 或在抓取時發生例外狀況, 就會擲回例外狀況 (exception)系統指定的預設 proxy。 例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會使用 Internet Explorer proxy 的預設值、指定 proxy 位址, 並略過 proxy 以進行本機存取和 contoso.com。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [網路設定結構描述](index.md)
