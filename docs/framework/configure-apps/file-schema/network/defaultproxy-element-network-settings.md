---
title: <defaultProxy> 項目 (網路設定)
description: <defaultProxy>網路設定元素會將超文字傳輸通訊協定設定 (HTTP) proxy 伺服器的 .NET Framework 中。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 806a30a52219ef9185f84a650d6a8eef8fb0dc8c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190302"
---
# <a name="defaultproxy-element-network-settings"></a>\<defaultProxy> 項目 (網路設定)

設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<defaultProxy  
  enabled="True|False"  
  useDefaultCredentials="True|False">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|`enabled`|指定是否使用 Web Proxy。 預設值是 `True`。|  
|`useDefaultCredentials`|指定此主機的預設認證是否用來存取 Web Proxy。 預設值是 `False`。|  
  
### <a name="child-elements"></a>子元素  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[bypasslist](bypasslist-element-network-settings.md)|提供一組位址的規則運算式，說明不使用 Proxy。|  
|[模組](module-element-network-settings.md)|將新的 Proxy 模組加入至應用程式。|  
|[代理](proxy-element-network-settings.md)|定義 Proxy 伺服器。|  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## <a name="remarks"></a>備註  

 如果 defaultProxy 項目是空的，則會使用來自 Internet Explorer 的 Proxy 設定。 這個行為與 .NET Framework 1.1 版的不同。  
  
 如果 [module](module-element-network-settings.md) 元素指定非公用類型、類型不是衍生自 <xref:System.Net.IWebProxy> 類別、發生這個物件的無參數函式的例外狀況，或在抓取系統指定的預設 proxy 時發生例外狀況，就會擲回例外狀況。 例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。  
  
## <a name="configuration-files"></a>組態檔  

 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  

 下列範例會使用 Internet Explorer proxy 的預設值、指定 proxy 位址，以及略過 proxy 以進行本機存取和 contoso.com。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
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
