---
title: <bypasslist> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154942"
---
# <a name="bypasslist-element-network-settings"></a>\<繞過清單>元素（網路設置）
提供一組常規運算式，用於描述不使用代理的位址。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<預設代理>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<繞過清單>**

## <a name="syntax"></a>語法  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|**Element**|**描述**|  
|-----------------|---------------------|  
|[新增](add-element-for-bypasslist-network-settings.md)|將 IP 位址或 DNS 名稱添加到代理繞過清單中。|  
|[清楚](clear-element-for-bypasslist-network-settings.md)|清除旁路清單。|  
|[移除](remove-element-for-bypasslist-network-settings.md)|從代理繞過清單中刪除 IP 位址或 DNS 名稱。|  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**描述**|  
|-----------------|---------------------|  
|[預設代理](defaultproxy-element-network-settings.md)|設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。|  
  
## <a name="remarks"></a>備註  
 旁路清單包含常規運算式，用於描述<xref:System.Net.WebRequest>實例直接存取而不是通過代理伺服器訪問的 URI。  
  
 為此元素指定正則運算式時應小心謹慎。 正則運算式"[a-z].contoso\\\\.com"與contoso.com域中的任何主機匹配，但它也與contoso.com.cpandl.com域中的任何主機匹配。 要僅匹配contoso.com域中的主機，請使用錨點（"$"）："[a-z].contoso.com$"。\\ \\  
  
 有關正則運算式的詳細資訊，請參閱。[.NET 框架正則運算式](../../../../standard/base-types/regular-expressions.md)。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下面的示例將兩個位址添加到旁路清單中。 第一個繞過contoso.com域中所有伺服器的代理;第二個伺服器繞過其 IP 位址以 192.168 開頭的所有伺服器的代理。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [網路設置架構](index.md)
