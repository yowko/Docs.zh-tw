---
title: <GCCpuGroup> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: ae9c96c9d49cf3f6be94da3f77b91423cab12e0b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430489"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup> Element

指定記憶體回收是否支援多個 CPU 群組。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<runtime>** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup>**

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
|`false`|Garbage collection does not support multiple CPU groups. 這是預設值。|
|`true`|Garbage collection supports multiple CPU groups, if server garbage collection is enabled.|

### <a name="child-elements"></a>子項目

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.

> [!NOTE]
> This element applies only to garbage collection threads. To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.

## <a name="example"></a>範例

The following example shows how to enable garbage collection for multiple CPU groups.

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [To disable concurrent garbage collection](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [工作站和伺服器記憶體回收](../../../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)
