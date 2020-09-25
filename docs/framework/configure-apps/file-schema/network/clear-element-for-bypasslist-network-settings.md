---
title: bypasslist 的 <clear> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: 96cef2dff3156e49a93be818230c83370dab5264
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185857"
---
# <a name="clear-element-for-bypasslist-network-settings"></a>bypasslist 的 \<clear> 項目 (網路設定)

清除 proxy 略過清單。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>Syntax  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  

 無。  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[bypasslist](bypasslist-element-network-settings.md)|提供一組正則運算式，用來描述未使用 proxy 的位址。|  
  
## <a name="remarks"></a>備註  

 `clear`專案會清除略過清單中的所有專案。  
  
## <a name="configuration-files"></a>組態檔  

 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  

 下列範例會清除 [略過] 清單，然後將兩個位址新增至 [略過] 清單。 第一個會針對 contoso.com 網域中的所有伺服器略過 proxy;第二個會針對 IP 位址開頭為192.168 的所有伺服器略過 proxy。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
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
