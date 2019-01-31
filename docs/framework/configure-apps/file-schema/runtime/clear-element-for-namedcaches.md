---
title: <clear> 的 <namedCaches> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: aaf5c2360b53a1cd6e5775a195c89c96ed6440a3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288661"
---
# <a name="clear-element-for-namedcaches"></a>\<清除 > 項目\<namedCaches >
清除所有`namedCache`中的項目`namedCaches`記憶體快取的集合。  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches>  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 `None`  
  
### <a name="child-elements"></a>子項目  
 `None`  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|包含集合的組態設定具名<xref:System.Runtime.Caching.MemoryCache>執行個體。|  
  
## <a name="remarks"></a>備註  
 `clear`項目清除所有`namedCache`記憶體內部快取的具名快取集合中的項目。 您可以使用`clear`項目才能使用`add`項目將加入新的具名快取項目，才能確定有沒有其他具名集合中的快取。  
  
## <a name="see-also"></a>另請參閱
- [\<namedCaches > 項目 （快取設定）](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
