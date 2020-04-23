---
title: <GCCpuGroup> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102888"
---
# <a name="gccpugroup-element"></a>\<GCCpu組>元素

指定記憶體回收是否支援多個 CPU 群組。

[**\<設定>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<執行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpu組>**

## <a name="syntax"></a>語法

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`enabled`|必要屬性。<br /><br /> 指定記憶體回收是否支援多個 CPU 群組。|

## <a name="enabled-attribute"></a>啟用屬性

|值|描述|
|-----------|-----------------|
|`false`|垃圾回收不支援多個 CPU 組。 這是預設值。|
|`true`|如果啟用了伺服器垃圾回收,垃圾回收支援多個 CPU 組。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

當電腦具有多個 CPU 組並啟用伺服器垃圾回收時(請參閱[\<gcServer>](gcserver-element.md)元素),啟用此元素可跨所有 CPU 組擴展垃圾回收,並在創建和平衡堆時考慮所有內核。

> [!NOTE]
> 此元素僅適用於垃圾回收線程。 要使運行時能夠跨所有 CPU 組分發使用者線程,還必須啟用[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)元素。

## <a name="example"></a>範例

下面的範例展示如何為多個 CPU 組啟用垃圾回收。

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [執行時設定架構](index.md)
- [設定檔案架構](../index.md)
- [關閉並發垃圾資源](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [工作站和伺服器記憶體回收](../../../../standard/garbage-collection/workstation-server-gc.md)
