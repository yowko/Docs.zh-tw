---
title: '&lt;GCCpuGroup&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4461667bdb47d410c857b4ac2c9dd268438a02f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltgccpugroupgt-element"></a>&lt;GCCpuGroup&gt;項目
指定記憶體回收是否支援多個 CPU 群組。  
  
 \<configuration>  
\<執行階段 >  
\<GCCpuGroup>  
  
## <a name="syntax"></a>語法  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定記憶體回收是否支援多個 CPU 群組。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|記憶體回收集合不支援多個 CPU 的群組。 這是預設值。|  
|`true`|記憶體回收支援多個 CPU 群組，如果已啟用伺服器記憶體回收。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 當電腦有多個 CPU 群組，且已啟用伺服器記憶體回收 (請參閱[ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)項目)，啟用這個項目延伸的所有 CPU 群組記憶體回收和採用到的所有核心若要建立並平衡堆積的帳戶。  
  
> [!NOTE]
>  這個項目只適用於記憶體回收執行緒。 若要讓 runtime 能夠將使用者執行緒分散到所有的 CPU 群組，您必須同時啟用[< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)項目。  
  
## <a name="example"></a>範例  
 下列範例會示範如何啟用多個 CPU 群組記憶體回收。  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [如何： 停用並行記憶體回收](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [工作站和伺服器記憶體回收](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
