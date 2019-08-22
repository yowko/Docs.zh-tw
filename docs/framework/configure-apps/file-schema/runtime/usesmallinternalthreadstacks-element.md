---
title: <UseSmallInternalThreadStacks> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74678089bb1b19295983064eb7ad54fbf0a1e361
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663380"
---
# <a name="usesmallinternalthreadstacks-element"></a>\<UseSmallInternalThreadStacks > 元素
要求 common language runtime (CLR) 在建立內部使用的特定執行緒時, 指定明確的堆疊大小來減少記憶體使用, 而不是使用這些執行緒的預設堆疊大小。  
  
 \<configuration > 元素  
\<執行時間 > 元素  
\<UseSmallInternalThreadStacks > 元素  
  
## <a name="syntax"></a>語法  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定在建立內部使用的特定執行緒時, 是否要要求 CLR 使用明確堆疊大小, 而不是預設堆疊大小。 明確堆疊大小小於 1 MB 的預設堆疊大小。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|true|要求明確堆疊大小。|  
|false|使用預設堆疊大小。 這是 .NET Framework 4 的預設值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 這個設定元素是用來要求在進程中減少使用的虛擬記憶體, 因為 CLR 針對其內部執行緒使用的明確執行緒大小, 如果接受要求, 則小於預設大小。  
  
> [!IMPORTANT]
>  此設定元素是對 CLR 的要求, 而不是絕對需求。 在 .NET Framework 4 中, 要求僅適用于 x86 架構。 這個元素可能會在未來的 CLR 版本中完全忽略, 或由一律用於所選內部執行緒的明確堆疊大小來取代。  
  
 指定此設定元素會在 CLR 接受要求時, 將可靠性用於較小的虛擬記憶體使用, 因為較小的堆疊大小可能會使堆疊溢位更有可能。  
  
## <a name="example"></a>範例  
 下列範例示範如何要求 CLR 針對它在內部使用的特定執行緒使用明確堆疊大小。  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
