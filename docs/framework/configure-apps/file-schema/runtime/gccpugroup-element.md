---
title: <GCCpuGroup> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: 352890519c1a227d664d877c3123866e5e4e1657
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116838"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup > 元素

指定記憶體回收是否支援多個 CPU 群組。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup >**  

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
|`false`|垃圾收集不支援多個 CPU 群組。 這是預設值。|
|`true`|如果已啟用伺服器垃圾收集，垃圾收集支援多個 CPU 群組。|

### <a name="child-elements"></a>子項目

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

當電腦具有多個 CPU 群組並啟用伺服器垃圾收集時（請參閱[\<gcServer >](gcserver-element.md)元素），啟用此元素會延伸所有 CPU 群組的垃圾收集，並在建立和時將所有核心納入考慮平衡堆積。

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

## <a name="see-also"></a>請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [停用並行垃圾收集](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [工作站和伺服器記憶體回收](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
