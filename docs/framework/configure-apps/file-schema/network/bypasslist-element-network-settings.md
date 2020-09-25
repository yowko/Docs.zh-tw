---
title: <bypasslist> 項目 (網路設定)
description: <bypasslist>Network settings 元素提供一組正則運算式，用來描述未在 .NET Framework 中使用 proxy 的位址。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 58cdcf046b2a5a292493c5704739b22aa4ec4f17
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178407"
---
# <a name="bypasslist-element-network-settings"></a>\<bypasslist> 項目 (網路設定)

提供一組正則運算式，用來描述未使用 proxy 的位址。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a>Syntax  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  

 無。  
  
### <a name="child-elements"></a>子元素  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[add](add-element-for-bypasslist-network-settings.md)|將 IP 位址或 DNS 名稱新增至 proxy 略過清單。|  
|[清除](clear-element-for-bypasslist-network-settings.md)|清除 [略過] 清單。|  
|[remove](remove-element-for-bypasslist-network-settings.md)|從 proxy 略過清單中移除 IP 位址或 DNS 名稱。|  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。|  
  
## <a name="remarks"></a>備註  

 略過清單包含正則運算式，可描述 <xref:System.Net.WebRequest> 實例直接存取而非透過 proxy 伺服器存取的 uri。  
  
 為此元素指定正則運算式時，請特別小心。 正則運算式 "[a-z] + \\ . \\ .com" 符合 contoso.com 網域中的任何主機，但它也符合 contoso.com.cpandl.com 網域中的任何主機。 若只要比對 contoso.com 網域中的主機，請使用錨點 ( "$" ) ： "[a-z] + \\ . \\ .com $"。  
  
 如需正則運算式的詳細資訊，請參閱。[.NET Framework 正則運算式](../../../../standard/base-types/regular-expressions.md)。  
  
## <a name="configuration-files"></a>組態檔  

 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  

 下列範例會將兩個位址新增至略過清單。 第一個會針對 contoso.com 網域中的所有伺服器略過 proxy;第二個會針對 IP 位址開頭為192.168 的所有伺服器略過 proxy。  
  
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
- [網路設定結構描述](index.md)
