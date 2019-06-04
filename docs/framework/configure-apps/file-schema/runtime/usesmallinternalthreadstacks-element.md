---
title: <UseSmallInternalThreadStacks> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70113d98c5a4ab41700f6c9842dba89e2b49c297
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489323"
---
# <a name="usesmallinternalthreadstacks-element"></a>\<UseSmallInternalThreadStacks > 項目
藉由指定明確的堆疊大小，它會建立它會在內部使用，而不是使用預設堆疊大小為這些執行緒進行特定執行緒時，使用 common language runtime (CLR)，減少記憶體的要求。  
  
 \<組態 > 項目  
\<執行階段 > 項目  
\<UseSmallInternalThreadStacks > 項目  
  
## <a name="syntax"></a>語法  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定是否要要求 CLR 使用明確的堆疊大小，而不是預設的堆疊大小時它會建立內部使用的特定執行緒。 明確的堆疊大小是小於 1 MB 的預設堆疊大小。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|true|要求明確的堆疊大小。|  
|False|使用預設堆疊大小。 這是.NET Framework 4 的預設值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 這個組態項目用來要求縮減的虛擬記憶體的使用，在處理序中，因為如果遵循，則要求，CLR 會使用其內部的執行緒，則明確的執行緒大小是小於預設大小。  
  
> [!IMPORTANT]
>  這個組態項目是 CLR，而不是絕對必要的需求的要求。 在.NET Framework 4 中，要求會接受僅適用於 x86 架構。 這個項目可能會完全忽略未來的 CLR 版本中，或以一律用於進行選取的內部執行緒的明確的堆疊大小。  
  
 指定這個組態項目往來可靠性較小的虛擬記憶體使用，是否 CLR 會接受要求，因為較小的堆疊大小可能會無法使堆疊更可能溢位。  
  
## <a name="example"></a>範例  
 下列範例示範如何要求 CLR 使用明確堆疊調整某些大小它會在內部使用的執行緒。  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
