---
title: <GCCpuGroup> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85cfe57f7a3b8cfecfae4c4ae00efaea464e6120
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090338"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup > 項目
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
|`false`|記憶體回收不支援多個 CPU 群組。 這是預設值。|  
|`true`|記憶體回收會支援多個 CPU 群組，如果已啟用伺服器記憶體回收。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 當電腦具有多個 CPU 群組，而且啟用伺服器記憶體回收之後 (請參閱[ \<Gcserver> >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)項目)，啟用這個項目延伸到所有 CPU 群組的記憶體回收和採用到的所有核心帳戶建立和平衡堆積時。  
  
> [!NOTE]
>  這個項目僅適用於記憶體回收執行緒。 若要啟用使用者執行緒分散到所有 CPU 群組的執行階段，您也必須啟用[< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)項目。  
  
## <a name="example"></a>範例  
 下列範例示範如何啟用多個 CPU 群組記憶體回收。  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [若要停用並行記憶體回收](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [工作站和伺服器記憶體回收](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
