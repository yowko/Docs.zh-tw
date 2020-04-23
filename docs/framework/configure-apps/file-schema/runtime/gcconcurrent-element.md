---
title: gc 併發元素
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
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102914"
---
# <a name="gcconcurrent-element"></a>\<gc併發>元素

指定 Common Language Runtime 是否會在個別的執行緒執行記憶體回收。

[\<設定>](../configuration-element.md)\
&nbsp;&nbsp;[\<執行時>](runtime-element.md)\
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

#### <a name="enabled-attribute"></a>開啟的屬性

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

在 .NET 框架 4 之前,工作站垃圾回收支援併發垃圾回收,該回收在後台在單獨的線程上執行垃圾回收。 在 .NET 框架 4 中,併發垃圾回收被後台 GC 替換,後台 GC 也在單獨的線程的後台執行垃圾回收。 從 .NET 框架 4.5 開始,後台收集在伺服器垃圾回收中可用。 **gcConcurrent**元素控制運行時是否執行併發或後台垃圾回收,是否可用,或者它是否在前臺執行垃圾回收。

### <a name="to-disable-background-garbage-collection"></a>關閉後臺垃圾資源

> [!WARNING]
> 從 .NET 框架 4 開始,併發垃圾回收將被後台垃圾回收替換。 術語*並發*和*背景*在 .NET 框架文檔中可互換使用。 要禁用後台垃圾回收,請使用**gcConcurrent**元素,如本文所述。

依預設，執行階段會使用並行或背景記憶體回收，這已針對延遲進行最佳化。 如果您的應用程式與使用者互動程度極高，則請讓並行記憶體回收維持啟用狀態，藉此最小化應用程式為了執行記憶體回收而暫停的時間。 如果將`enabled`**gcConcurrent**元素的屬性`false`設置為 ,運行時將使用非併發垃圾回收,該回收針對輸送量進行了優化。

以下設定檔禁用後台垃圾回收:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

如果電腦設定檔中有**gcConcurrent 設定,** 它將為所有 .NET Framework 應用程式定義預設值。 電腦組態檔設定會覆寫應用程式組態檔設定。

有關併發和後台垃圾回收的詳細資訊,請參閱[後台垃圾回收](../../../../standard/garbage-collection/background-gc.md)。

## <a name="example"></a>範例

以下範例支援後台垃圾回收:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [執行時設定架構](index.md)
- [設定檔案架構](../index.md)
- [Fundamentals of Garbage Collection (記憶體回收的基本概念)](../../../../standard/garbage-collection/fundamentals.md)
