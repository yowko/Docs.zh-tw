---
title: <namedCaches> 的 <clear> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: a90970e468359714bbbb858f3f300c26b5757a4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658853"
---
# <a name="clear-element-for-namedcaches"></a>\<清除 namedCaches 的\<> 元素 >
清除`namedCache` 集合`namedCaches`中記憶體快取的所有專案。  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches>  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 `None`  
  
### <a name="child-elements"></a>子元素  
 `None`  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|包含已命名<xref:System.Runtime.Caching.MemoryCache>實例的設定集合。|  
  
## <a name="remarks"></a>備註  
 元素會清除已`namedCache`命名快取集合中記憶體快取的所有專案。 `clear` 您可以使用`clear`專案, 然後`add`使用專案來加入新的命名快取專案, 以確保集合中沒有其他命名的快取。  
  
## <a name="see-also"></a>另請參閱

- [\<namedCaches > 元素 (快取設定)](namedcaches-element-cache-settings.md)
