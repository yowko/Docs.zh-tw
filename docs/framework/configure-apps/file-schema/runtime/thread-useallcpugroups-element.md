---
title: <Thread_UseAllCpuGroups> 項目
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e964f1b2861926803b0449be06cbfd9567ac74a3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252278"
---
# <a name="thread_useallcpugroups-element"></a>\<Thread_UseAllCpuGroups > 元素

指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<Thread_UseAllCpuGroups >**  

## <a name="syntax"></a>語法

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`enabled`|必要屬性。<br /><br /> 指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。|

## <a name="enabled-attribute"></a>啟用屬性

|值|描述|
|-----------|-----------------|
|`false`|執行時間不會將受控執行緒分散到多個 CPU 群組。 這是預設值。|
|`true`|如果電腦有多個 cpu 群組, 而且[ \<已啟用 GCCpuGroup >](gccpugroup-element.md)元素, 則執行時間會將受控執行緒分散到多個 cpu 群組。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|說明|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

當電腦具有多個 CPU 群組時, 啟用此元素會導致執行時間將受控執行緒分散到所有 CPU 群組。 若要使用這項功能, 您也必須啟用[ \<GCCpuGroup >](gccpugroup-element.md)元素, 這會將垃圾收集延伸到所有 CPU 群組, 並在建立和平衡堆積時將所有核心納入考慮。 啟用 GCCpuGroup [ >元素需要啟用gcServer>元素。\< ](gccpugroup-element.md) [ \< ](gcserver-element.md) 如果未啟用這些元素, 啟用元素將`<Thread_UseAllCpuGroups>`不會有任何作用。

## <a name="example"></a>範例

下列範例顯示如何啟用多個 CPU 群組的支援。

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [\<GCCpuGroup > 元素](gccpugroup-element.md)
