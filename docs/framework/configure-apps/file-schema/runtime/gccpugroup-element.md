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
# <a name="gccpugroup-element"></a>\<GCCpuGroup > 元素

指定記憶體回收是否支援多個 CPU 群組。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup >**

## <a name="syntax"></a>語法

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`enabled`|必要屬性。<br /><br /> 指定記憶體回收是否支援多個 CPU 群組。|

## <a name="enabled-attribute"></a>啟用屬性

|值|描述|
|-----------|-----------------|
|`false`|垃圾收集不支援多個 CPU 群組。 這是預設值。|
|`true`|如果已啟用伺服器垃圾收集，垃圾收集支援多個 CPU 群組。|

### <a name="child-elements"></a>子元素

None。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

當電腦具有多個 CPU 群組並啟用伺服器垃圾收集時（請參閱[\<gcServer >](gcserver-element.md)元素），啟用此元素會延伸所有 CPU 群組的垃圾收集，並在建立和平衡堆積時將所有核心納入考慮。

> [!NOTE]
> 這個元素只適用于垃圾收集執行緒。 若要讓執行時間將使用者執行緒分散到所有的 CPU 群組，您也必須啟用[\<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md)元素。

## <a name="example"></a>範例

下列範例顯示如何啟用多個 CPU 群組的垃圾收集。

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [停用並行垃圾收集](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [工作站和伺服器記憶體回收](../../../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)
