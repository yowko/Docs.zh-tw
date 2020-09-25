---
title: <UseSmallInternalThreadStacks> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: 4917b47e9e8196eabe691f74531d12308ef80311
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174078"
---
# <a name="usesmallinternalthreadstacks-element"></a>\<UseSmallInternalThreadStacks> 項目

要求 common language runtime (CLR) 在建立它在內部使用的特定執行緒時，指定明確的堆疊大小來減少記憶體使用，而不是使用這些執行緒的預設堆疊大小。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|已啟用|必要屬性。<br /><br /> 指定當 CLR 建立在內部使用的特定執行緒時，是否要求 CLR 使用明確堆疊大小，而不是預設堆疊大小。 明確堆疊大小小於預設堆疊大小 1 MB。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|true|要求明確的堆疊大小。|  
|false|使用預設堆疊大小。 這是 .NET Framework 4 的預設值。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  

 這個設定元素可用來要求減少在進程中使用的虛擬記憶體，因為 CLR 針對其內部執行緒使用的明確執行緒大小（如果接受要求的話）小於預設大小。  
  
> [!IMPORTANT]
> 這個設定元素是對 CLR 的要求，而不是絕對需求。 在 .NET Framework 4 中，只會針對 x86 架構接受要求。 此元素可能會在未來的 CLR 版本中完全被忽略，或由一律用於所選取內部執行緒的明確堆疊大小所取代。  
  
 如果 CLR 接受要求，則指定此設定專案會針對較小的虛擬記憶體使用量來提高可靠性，因為較小的堆疊大小可能會讓堆疊溢位更有可能。  
  
## <a name="example"></a>範例  

 下列範例示範如何要求 CLR 針對它在內部使用的特定執行緒，使用明確的堆疊大小。  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [設定檔架構](../index.md)
