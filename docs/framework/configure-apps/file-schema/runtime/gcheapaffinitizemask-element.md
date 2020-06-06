---
title: GCHeapAffinitizeMask 元素
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73978379"
---
# <a name="gcheapaffinitizemask-element"></a>\<GCHeapAffinitizeMask> 項目

定義 GC 堆積與個別處理器之間的親和性。

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask>

## <a name="syntax"></a>語法

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`enabled`|必要屬性。<br /><br />指定 GC 堆積與個別處理器之間的親和性。 |

#### <a name="enabled-attribute"></a>enabled 屬性

|值|描述|
|-----------|-----------------|
|`nnnn`|十進位值，形成位元遮罩，以定義伺服器 GC 堆積與個別處理器之間的親和性。 |

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

根據預設，伺服器 GC 執行緒會相似化為其各自的 CPU，讓每個處理器都有一個 GC 堆積、一個伺服器 GC 執行緒，以及一個背景伺服器 GC 執行緒。 從 .NET Framework 4.6.2 開始，當堆積數目受到**GCHeapCount**元素的限制時，您可以使用**GCHeapAffinitizeMask**元素來控制伺服器 GC 堆積和處理器之間的相似性。

**GCHeapAffinitizeMask**通常會與兩個其他旗標搭配使用：

- [GCNoAffinitize](gcnoaffinitize-element.md)，控制是否使用 cpu 相似化為伺服器 GC 執行緒/堆積。 `enabled` [GCNoAffinitize](gcnoaffinitize-element.md)元素的屬性必須是 `false` （其預設值），才能使用**GCHeapAffinitizeMask**設定。

- [GCHeapCount](gcheapcount-element.md)，這會限制進程針對伺服器 GC 所使用的堆積數目。 根據預設，每個處理器都有一個堆積。

**nnnn**是以十進位值表示的位元遮罩。 位0的位元組0代表處理器0，位元組0的位1代表處理器1，依此類推。 例如：

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

1023的值是0x3FF 或 0011 1111 1111b。 此程式會使用10個處理器，從處理器0到處理器9。

## <a name="example"></a>範例

下列範例指出應用程式使用具有10個堆積/執行緒的伺服器 GC。 由於您不想讓這些堆積與系統上執行的其他應用程式的堆積重迭，因此請使用**GCHeapAffinitizeMask**來指定進程應該使用 cpu 0 到9。

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [GCNoAffinitize 元素](gcnoaffinitize-element.md)
- [GCHeapCount 元素](gcheapcount-element.md)
- [垃圾收集的基本概念](../../../../standard/garbage-collection/fundamentals.md)
- [執行時間設定架構](index.md)
- [設定檔架構](../index.md)
