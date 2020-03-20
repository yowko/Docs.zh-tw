---
title: gc併發元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 5957337aa960a0d5f445249b410dbfaddb7b08e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400040"
---
# <a name="gcconcurrent-element"></a>\<gc併發>元素

指定 Common Language Runtime 是否會在個別的執行緒執行記憶體回收。

[\<配置>](../configuration-element.md)\
&nbsp;&nbsp;[\<運行時>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gc 併發>

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

#### <a name="enabled-attribute"></a>啟用的屬性

|值|描述|
|-----------|-----------------|
|`false`|不同時運行垃圾回收。|
|`true`|同時執行記憶體回收。 這是預設值。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

在 .NET 框架 4 之前，工作站垃圾回收支援併發垃圾回收，該回收在後臺在單獨的執行緒上執行垃圾回收。 在 .NET 框架 4 中，併發垃圾回收被後臺 GC 替換，後臺 GC 也在單獨的執行緒的後臺執行垃圾回收。 從 .NET 框架 4.5 開始，後臺收集在伺服器垃圾回收中可用。 **gcConcurrent**元素控制運行時是否執行併發或後臺垃圾回收，是否可用，或者它是否在前臺執行垃圾回收。

### <a name="to-disable-background-garbage-collection"></a>禁用後臺垃圾回收

> [!WARNING]
> 從 .NET 框架 4 開始，併發垃圾回收將被後臺垃圾回收替換。 術語*併發*和*背景*在 .NET 框架文檔中可互換使用。 要禁用後臺垃圾回收，請使用**gcConcurrent**元素，如本文所述。

依預設，執行階段會使用並行或背景記憶體回收，這已針對延遲進行最佳化。 如果您的應用程式與使用者互動程度極高，則請讓並行記憶體回收維持啟用狀態，藉此最小化應用程式為了執行記憶體回收而暫停的時間。 如果將`enabled`**gcConcurrent**元素的屬性設置為`false`，運行時將使用非併發垃圾回收，該回收針對輸送量進行了優化。

以下設定檔禁用後臺垃圾回收：

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

如果電腦設定檔中有**gcConcurrent設置，** 它將為所有 .NET Framework 應用程式定義預設值。 電腦組態檔設定會覆寫應用程式組態檔設定。

有關併發和後臺垃圾回收的詳細資訊，請參閱"[垃圾回收基礎知識](../../../../standard/garbage-collection/fundamentals.md)"一文中的[併發垃圾回收](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection)、[後臺工作站垃圾回收](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)和[後臺伺服器垃圾回收](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection)部分。

## <a name="example"></a>範例

以下示例支援後臺垃圾回收：

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
- [Fundamentals of Garbage Collection (記憶體回收的基本概念)](../../../../standard/garbage-collection/fundamentals.md)
