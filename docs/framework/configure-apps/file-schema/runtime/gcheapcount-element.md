---
title: GCHeapCount 元素
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283076"
---
# <a name="gcheapcount-element"></a>\<GCHeapCount > 元素

指定要用於伺服器垃圾收集的堆積/執行緒數目。

\<設定 > \
&nbsp;&nbsp;\<執行時間 > \
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount >

## <a name="syntax"></a>語法

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`enabled`|必要屬性。<br /><br />指定要用於伺服器垃圾收集的堆積數目。 實際的堆積數目是您指定之堆積數目的最小值，以及您的進程允許使用的處理器數目。 |

#### <a name="enabled-attribute"></a>enabled 屬性

|值|描述|
|-----------|-----------------|
|`nn`|用於伺服器 GC 的堆積數目。|

### <a name="child-elements"></a>子元素

None。

### <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

根據預設，伺服器 GC 執行緒會相似化為其各自的 CPU，讓每個處理器都有一個 GC 堆積、一個伺服器 GC 執行緒，以及一個背景伺服器 GC 執行緒。 從 .NET Framework 4.6.2 開始，您可以使用**GCHeapCount**元素來限制應用程式用於伺服器 GC 的堆積數目。 限制用於伺服器 GC 的堆積數目，對於執行多個伺服器應用程式實例的系統特別有用。

**GCHeapCount**通常會與兩個其他旗標搭配使用：

- [GCNoAffinitize](gcnoaffinitize-element.md)，控制是否使用 cpu 相似化為伺服器 GC 執行緒/堆積。

- [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)，控制 GC 執行緒/堆積與 cpu 的親和性。

如果已設定**GCHeapCount** ，且**GCNoAffinitize**已停用（其預設值），則*nn* GC threads/堆積和第一個*nn*個處理器之間會有相似性。 您可以使用**GCHeapAffinitizeMask**元素來指定進程的伺服器 GC 堆積所使用的處理器。 否則，如果有多個伺服器進程在系統上執行，其處理器使用量將會重迭。

如果已設定**GCHeapCount**並啟用**GCNoAffinitize** ，垃圾收集行程會限制用於伺服器 GC 的處理器數目，但不會將相似化為 GC 堆積和處理器。

## <a name="example"></a>範例

下列範例指出應用程式使用具有10個堆積/執行緒的伺服器 GC。 由於您不想讓這些堆積與系統上執行的其他應用程式的堆積重迭，因此，您可以使用**GCHeapAffinitizeMask**來指定進程應該使用 cpu 0 到9。

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

下列範例不會將相似化為伺服器 GC 執行緒，而且會將 GC 堆積/執行緒的數目限制為10。

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [GCNoAffinitize 元素](gcnoaffinitize-element.md)
- [GCHeapAffinitizeMask 元素](gcheapaffinitizemask-element.md)
- [記憶體回收的基本概念](../../../../standard/garbage-collection/fundamentals.md)
- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
