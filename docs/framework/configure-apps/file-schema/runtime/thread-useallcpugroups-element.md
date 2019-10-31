---
title: <Thread_UseAllCpuGroups> 項目
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115402"
---
# <a name="thread_useallcpugroups-element"></a>\<Thread_UseAllCpuGroups> Element

指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<runtime>** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<Thread_UseAllCpuGroups>**  

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
|`false`|The runtime does not distribute managed threads across multiple CPU groups. 這是預設值。|
|`true`|The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.|

### <a name="child-elements"></a>子項目

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups. To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps. Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element. If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.

## <a name="example"></a>範例

The following example shows how to enable support for multiple CPU groups.

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [\<GCCpuGroup> Element](gccpugroup-element.md)
