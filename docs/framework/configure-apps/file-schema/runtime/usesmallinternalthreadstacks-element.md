---
title: "&lt;UseSmallInternalThreadStacks&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2558423b412333a4d6ac9f650ad8ff3dab449d74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a>&lt;UseSmallInternalThreadStacks&gt;項目
藉由指定明確的堆疊大小，它會建立特定的執行緒，它會在內部使用，而不是使用預設堆疊大小，這些執行緒時，使用 common language runtime (CLR)，減少記憶體的要求。  
  
 \<設定 > 項目  
\<runtime > 項目  
\<UseSmallInternalThreadStacks > 項目  
  
## <a name="syntax"></a>語法  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定是否要求 CLR 使用明確的堆疊大小，而不是預設堆疊大小時它會建立特定的執行緒，它會在內部使用。 明確的堆疊大小會小於 1 MB 的預設堆疊大小。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|true|要求明確的堆疊大小。|  
|false|使用預設堆疊大小。 這是預設值[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 這個組態項目用來要求在處理程序，減少的虛擬記憶體使用，因為如果接受要求，則 CLR 會使用其內部執行緒的明確執行緒大小為小於預設大小。  
  
> [!IMPORTANT]
>  這個組態項目是要求 CLR，而不是絕對必要的需求。 在[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，要求會被接受只適用於 x86 架構。 可能在未來版本的 CLR 中完全忽略這個項目，或明確的堆疊大小一定會用於選取的內部執行緒會被取代。  
  
 指定這個組態項目往來的較小的虛擬記憶體使用可靠性是否 CLR 會接受要求，因為較小的堆疊大小可能無法使堆疊可能溢位。  
  
## <a name="example"></a>範例  
 下列範例會示範如何要求 CLR 使用明確堆疊調整特定大小的執行緒，它會在內部使用。  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
