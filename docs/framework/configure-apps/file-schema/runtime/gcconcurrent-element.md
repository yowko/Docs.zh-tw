---
title: <gcConcurrent> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b2774c32b4ee3e67772f84d599ecc5dbeb6598b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252585"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent > 元素

指定 Common Language Runtime 是否會在個別的執行緒執行記憶體回收。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<gcConcurrent>**  

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
|`enabled`|必要屬性。<br /><br /> 指定執行階段是否同時執行記憶體回收。|

## <a name="enabled-attribute"></a>enabled 屬性

|值|說明|
|-----------|-----------------|
|`false`|不會同時執行垃圾收集。|
|`true`|同時執行記憶體回收。 這是預設值。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

在 .NET Framework 4 之前，工作站記憶體回收支援並行記憶體回收，這會在另一個執行緒上，在背景中執行記憶體回收。 在 .NET Framework 4 中，並行記憶體回收取代為背景 GC，這也會在另一個執行緒上，在背景中執行記憶體回收。 從 .NET Framework 4.5 開始，在伺服器記憶體回收中可以使用背景記憶體回收。 `<gcConcurrent>`元素會控制執行時間是否執行並行或背景垃圾收集 (如果有的話), 或是是否在前景執行垃圾收集。

### <a name="to-disable-background-garbage-collection"></a>若要停用背景垃圾收集

> [!WARNING]
> 從 .NET Framework 4 開始，背景記憶體回收就取代了並行記憶體回收。 .NET Framework 檔中會交替使用「*並行*」和「*背景*」這兩個詞彙。 若要停用背景記憶體回收，請使用 `<gcConcurrent>` 項目，如本文所述。

依預設，執行階段會使用並行或背景記憶體回收，這已針對延遲進行最佳化。 如果您的應用程式與使用者互動程度極高，則請讓並行記憶體回收維持啟用狀態，藉此最小化應用程式為了執行記憶體回收而暫停的時間。 如果您將 `enabled` 項目的 `<gcConcurrent>` 屬性設為 `false`，執行階段就會使用針對輸送量最佳化的非並行記憶體回收。 下列組態檔會停用背景記憶體回收。

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

 如果電腦設定檔`<gcConcurrentSetting>`中有設定, 則會定義所有 .NET Framework 應用程式的預設值。 電腦組態檔設定會覆寫應用程式組態檔設定。

 如需並行和背景垃圾收集的詳細資訊, 請參閱[垃圾收集的基本](../../../../standard/garbage-collection/fundamentals.md)概念一文中的[並行垃圾收集](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection)一節。

## <a name="example"></a>範例

下列範例會啟用並行垃圾收集:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [記憶體回收的基本概念](../../../../standard/garbage-collection/fundamentals.md)
