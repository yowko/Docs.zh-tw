---
title: <namedCaches> 的 <remove> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: e9b126cee83bc8109606d915ea48549beea970c9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663479"
---
# <a name="remove-element-for-namedcaches"></a>\<移除 namedCaches > 的\<> 元素
從記憶體快取的 `namedCaches` 集合移除具名快取項目。  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches>  
\<remove>  
  
## <a name="syntax"></a>語法  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>類型  
 `None`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 `None`  
  
### <a name="child-elements"></a>子元素  
 `None`  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|包含已命名<xref:System.Runtime.Caching.MemoryCache>實例的設定集合。|  
  
## <a name="remarks"></a>備註  
 元素會從記憶體`namedCache`快取的命名快取集合中移除專案。 `remove`  
  
## <a name="see-also"></a>另請參閱

- [\<namedCaches > 元素 (快取設定)](namedcaches-element-cache-settings.md)
