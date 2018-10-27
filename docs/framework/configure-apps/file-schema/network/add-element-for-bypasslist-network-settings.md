---
title: '&lt;新增&gt;bypasslist （網路設定） 的項目'
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
ms.openlocfilehash: ca1d33b2077736a9760f65857bffe4e96c4aeab0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182212"
---
# <a name="ltaddgt-element-for-bypasslist-network-settings"></a>&lt;新增&gt;bypasslist （網路設定） 的項目
將 IP 位址或 DNS 名稱加入至 proxy 略過清單中。  
  
 \<configuration>  
\<system.net>  
\<defaultProxy >  
\<bypasslist >  
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
|**address**|描述 IP 位址或 DNS 名稱的規則運算式。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|提供一組規則運算式，其中說明不使用 proxy 的位址。|  
  
## <a name="remarks"></a>備註  
 `add`項目會插入描述 IP 位址或 DNS 伺服器名稱略過 proxy 伺服器的位址清單的規則運算式。  
  
 值`address`屬性應該是規則運算式描述一組 IP 位址或主機名稱。  
  
 指定這個項目的規則運算式時，您應謹慎小心。 規則運算式"[a-z]、[0-9]、[_] +\\.contoso\\.com 」 比對任何裝載在 contoso.com 網域，但它也會比對 contoso.com.cpandl.com 網域中的任何主機。 若要比對 contoso.com 網域中的主機，使用錨點 （"$"）:"[a-z]、[0-9]、[_] +\\.contoso\\.com$"。  
  
 如需有關規則運算式的詳細資訊，請參閱。[.NET framework 規則運算式](../../../../../docs/standard/base-types/regular-expressions.md)。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會將略過清單中的兩個位址。 第一個會略過在 contoso.com 網域中的所有伺服器的 proxy第二個會略過的所有伺服器會開始其 IP 位址 192.168 的 proxy。  
  
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
- [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
