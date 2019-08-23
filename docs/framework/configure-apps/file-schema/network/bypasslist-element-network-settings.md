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
ms.openlocfilehash: bd746f07b4c4eb08bf34b01d555b5799d9af0cf3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927469"
---
# <a name="bypasslist-element-network-settings"></a>\<bypasslist > 元素 (網路設定)
提供一組正則運算式, 描述不使用 proxy 的位址。  
  
 \<configuration>  
\<system.net>  
\<defaultProxy>  
\<bypasslist>  
  
## <a name="syntax"></a>語法  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[add](add-element-for-bypasslist-network-settings.md)|將 IP 位址或 DNS 名稱新增至 proxy 略過清單。|  
|[clear](clear-element-for-bypasslist-network-settings.md)|清除略過清單。|  
|[remove](remove-element-for-bypasslist-network-settings.md)|從 proxy 略過清單中移除 IP 位址或 DNS 名稱。|  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。|  
  
## <a name="remarks"></a>備註  
 「略過清單」包含正則運算式, <xref:System.Net.WebRequest>可描述實例直接存取而不是透過 proxy 伺服器存取的 uri。  
  
 為此元素指定正則運算式時, 請務必小心。 正則運算式 "[a-z] +\\. contoso\\.com" 符合 contoso.com 網域中的任何主機, 但也符合 contoso.com.cpandl.com 網域中的任何主機。 若只要比對 contoso.com 網域中的主機, 請使用錨點 ("$"): "[a-z] +\\. contoso\\.com $"。  
  
 如需正則運算式的詳細資訊, 請參閱。[.NET Framework 正則運算式](../../../../standard/base-types/regular-expressions.md)。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會將兩個位址新增至略過清單。 第一個會略過 contoso.com 網域中所有伺服器的 proxy;第二個會略過其 IP 位址開頭為192.168 的所有伺服器的 proxy。  
  
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
