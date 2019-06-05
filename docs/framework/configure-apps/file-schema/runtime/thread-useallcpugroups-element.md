---
title: <Thread_UseAllCpuGroups> 項目
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9758e009e012c8af5f5f7bd19dcd21f34b8c7d96
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689730"
---
# <a name="threaduseallcpugroups-element"></a>\<Thread_UseAllCpuGroups > 項目

指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。

\<configuration>\
\<runtime>\
\<Thread_UseAllCpuGroups>

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
|`false`|執行階段不會跨多個 CPU 群組分配 managed 的執行緒。 這是預設值。|
|`true`|執行階段會分散到多個 CPU 群組，managed 的執行緒如果電腦有多個 CPU 群組及[ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)項目已啟用。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

當電腦具有多個 CPU 群組時，啟用這個項目會導致執行階段的所有 CPU 群組分配 managed 的執行緒。 若要使用這項功能，您也必須啟用[ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)元素，其記憶體回收會延伸到所有 CPU 群組並考量所有的核心建立，並平衡堆積時。 啟用[ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)項目時，必須啟用[ \<Gcserver> >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)項目。 如果未啟用這些項目，則啟用`<Thread_UseAllCpuGroups>`項目沒有任何作用。

## <a name="example"></a>範例

下列範例示範如何啟用多個 CPU 群組的支援。

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

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<GCCpuGroup > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
