---
title: gcServer 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 8eab5e36bab90510aff4f1a3e15328197ac59ed7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968939"
---
# <a name="gcserver-element"></a>\<gcServer > 元素

指定 Common Language Runtime 是否執行伺服器記憶體回收。

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<執行時間 >](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer >

## <a name="syntax"></a>語法

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>屬性和元素

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`enabled`|必要屬性。<br /><br />指定執行階段是否執行伺服器記憶體回收。|

#### <a name="enabled-attribute"></a>enabled 屬性

|值|描述|
|-----------|-----------------|
|`false`|不執行伺服器記憶體回收。 這是預設值。|
|`true`|執行伺服器記憶體回收。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

Common Language Runtime (CLR) 支援兩種類型的記憶體回收：工作站記憶體回收 (可用於所有系統)，以及伺服器記憶體回收 (可用於多處理器系統)。 使用**gcServer**元素來控制 CLR 執行的垃圾收集類型。 使用 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> 屬性來決定是否啟用伺服器記憶體回收。

針對單一處理器電腦，預設的工作站記憶體回收應該是最快的選項。 無論是工作站或伺服器，都可以用於兩個處理器的電腦。 針對兩個以上的處理器，伺服器記憶體回收應該是最快的選項。 最常見的是多處理器伺服器系統會停用伺服器 GC，而當伺服器應用程式的許多實例都在同一部電腦上執行時，會改為使用工作站 GC。

此項目只能用在應用程式組態檔中；如果是在或電腦組態檔中，就會忽略此項目。

> [!NOTE]
> 在 .NET Framework 4 (含) 以前版本中，當伺服器記憶體回收啟用時，無法使用並行記憶體回收。 從 .NET Framework 4.5 開始，伺服器記憶體回收為並行。 若要使用非並行伺服器垃圾收集，請將**gcServer**元素設定為 `true`，並將[gcConcurrent 元素](gcconcurrent-element.md)設為 `false`。

從 .NET Framework 4.6.2 開始，您也可以使用下列元素來設定伺服器 GC：

- [GCNoAffinitize](gcnoaffinitize-element.md)，指定伺服器 GC 堆積和處理器之間是否有相似性。 根據預設，每個處理器都有一個伺服器 GC 堆積。

- [GCHeapCount](gcheapcount-element.md)，這會限制進程所使用的堆積數目。

- [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)，定義可用伺服器 GC 堆積與個別處理器之間的親和性。

## <a name="example"></a>範例

下列範例會啟用伺服器垃圾收集：

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>請參閱

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [停用並行垃圾收集](gcconcurrent-element.md#to-disable-background-garbage-collection)
