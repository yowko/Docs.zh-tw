---
title: GCLOHThreshold 元素
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451217"
---
# <a name="gclohthreshold-element"></a>GCLOHThreshold 元素

指定導致垃圾收集行程將物件放在大型物件堆積（LOH）上的閾值大小（以位元組為單位）。

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<執行時間 >](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold >

## <a name="syntax"></a>語法

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`enabled`|必要屬性。<br /><br />指定導致物件在大型物件堆積上執行的臨界值大小。|

### <a name="enabled-attribute"></a>enabled 屬性

|值|描述|
|-----------|-----------------|
|`nnnn`|導致物件在大型物件堆積上執行的臨界值大小（以位元組為單位）。|

## <a name="child-elements"></a>子元素

None。

## <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

這項設定是在 .NET Framework 4.8 中引進。

## <a name="see-also"></a>另請參閱

- [執行時間設定架構](index.md)
- [組態檔結構描述](../index.md)
- [記憶體回收的基本概念](../../../../standard/garbage-collection/fundamentals.md)
- [GC 的 NET Core 執行時間設定選項](../../../../core/run-time-config/garbage-collector.md)
