---
title: gcConcurrent 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 249518ae7477d284d50f9010757db83b7752c657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102914"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent> 項目

指定 Common Language Runtime 是否會在個別的執行緒執行記憶體回收。

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a>語法

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`enabled`|必要屬性。<br /><br />指定執行階段是否同時執行記憶體回收。|

#### <a name="enabled-attribute"></a>enabled 屬性

|值|描述|
|-----------|-----------------|
|`false`|不會同時執行垃圾收集。|
|`true`|同時執行記憶體回收。 此為預設值。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

在 .NET Framework 4 之前，工作站垃圾收集支援並行垃圾收集，這會在個別執行緒的背景中執行垃圾收集。 在 .NET Framework 4 中，並行垃圾收集已由背景 GC 取代，這也會在另一個執行緒的背景中執行垃圾收集。 從 .NET Framework 4.5 開始，會在伺服器垃圾收集中提供背景集合。 **GcConcurrent**元素會控制執行時間是否執行並行或背景垃圾收集（如果有的話），或是是否在前景執行垃圾收集。

### <a name="to-disable-background-garbage-collection"></a>若要停用背景垃圾收集

> [!WARNING]
> 從 .NET Framework 4 開始，並行垃圾收集會由背景垃圾收集取代。 .NET Framework 檔中會交替使用「*並行*」和「*背景*」這兩個詞彙。 若要停用背景垃圾收集，請使用**gcConcurrent**元素，如本文中所述。

依預設，執行階段會使用並行或背景記憶體回收，這已針對延遲進行最佳化。 如果您的應用程式與使用者互動程度極高，則請讓並行記憶體回收維持啟用狀態，藉此最小化應用程式為了執行記憶體回收而暫停的時間。 如果您將 `enabled` **gcConcurrent**元素的屬性設定為 `false` ，執行時間會使用非並行垃圾收集，這會針對輸送量進行優化。

下列設定檔會停用背景垃圾收集：

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

如果電腦設定檔中有**gcConcurrentSetting**設定，它會定義所有 .NET Framework 應用程式的預設值。 電腦組態檔設定會覆寫應用程式組態檔設定。

如需並行和背景垃圾收集的詳細資訊，請參閱[背景垃圾收集](../../../../standard/garbage-collection/background-gc.md)。

## <a name="example"></a>範例

下列範例會啟用背景垃圾收集：

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [執行時間設定架構](index.md)
- [設定檔架構](../index.md)
- [Fundamentals of Garbage Collection (記憶體回收的基本概念)](../../../../standard/garbage-collection/fundamentals.md)
