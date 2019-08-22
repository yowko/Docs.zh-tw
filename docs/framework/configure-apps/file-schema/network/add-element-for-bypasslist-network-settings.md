---
title: bypasslist 的 <add> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: dd8790efa14018817c9e51e688b17c22d31d482f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659577"
---
# <a name="add-element-for-bypasslist-network-settings"></a>\<新增 bypasslist 的 > 元素 (網路設定)
將 IP 位址或 DNS 名稱新增至 proxy 略過清單。  
  
 \<configuration>  
\<system.net>  
\<defaultProxy>  
\<bypasslist>  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|**屬性**|**描述**|  
|-------------------|---------------------|  
|**address**|描述 IP 位址或 DNS 名稱的正則運算式。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[bypasslist](bypasslist-element-network-settings.md)|提供一組正則運算式, 描述不使用 proxy 的位址。|  
  
## <a name="remarks"></a>備註  
 `add`元素會將描述 IP 位址或 DNS 伺服器名稱的正則運算式插入至略過 proxy 伺服器的地址清單。  
  
 `address`屬性的值應該是描述一組 IP 位址或主機名稱的正則運算式。  
  
 為此元素指定正則運算式時, 請務必小心。 正則運算式 "[a-z] +\\. contoso\\.com" 符合 contoso.com 網域中的任何主機, 但也符合 contoso.com.cpandl.com 網域中的任何主機。 若只要比對 contoso.com 網域中的主機, 請使用錨點 ("$"): "[a-z] +\\. contoso\\.com $"。  
  
 如需正則運算式的詳細資訊, 請參閱。[.NET Framework 正則運算式](../../../../../docs/standard/base-types/regular-expressions.md)。  
  
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
