---
title: <performanceCounters> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: f52fdb2d5b0b7911de63f96663e70735d2f2496c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697159"
---
# <a name="performancecounters-element"></a>@no__t 0performanceCounters > 元素

指定效能計數器共用之全域記憶體的大小。

[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. 診斷 >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<performanceCounters >**  

## <a name="syntax"></a>語法

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|filemappingsize|必要屬性。<br /><br /> 指定效能計數器共用的全域記憶體大小（以位元組為單位）。 預設值為 524288。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|`Configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|

## <a name="remarks"></a>備註

效能計數器會使用記憶體對應檔案或共用記憶體來發行效能資料。  共用記憶體的大小會決定一次可以使用多少個實例。  共用記憶體有兩種類型：全域共用記憶體和個別的共用記憶體。  與 .NET Framework 版本1.0 或1.1 一起安裝的所有效能計數器類別都會使用全域共用記憶體。  隨 .NET Framework 版本2.0 安裝的效能計數器類別會使用不同的共用記憶體，每個效能計數器類別都有自己的記憶體。

全域共用記憶體的大小只能使用設定檔來設定。  預設大小為 524288 byes，大小上限為33554432個位元組，而最小大小為32768個位元組。  由於全域共用記憶體是由所有進程和類別共用，因此第一個建立者會指定大小。  如果您在應用程式佈建檔中定義大小，只有在您的應用程式是導致效能計數器執行的第一個應用程式時，才會使用該大小。  因此，指定 `filemappingsize` 值的正確位置是 Machine.config 檔案。  個別效能計數器無法釋放全域共用記憶體中的記憶體，因此，如果建立了大量具有不同名稱的效能計數器實例，最後就會耗盡全域共用記憶體。

針對個別共用記憶體的大小，會先參考登錄機碼 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services @ no__t-0 *\<category name >* \Performance 中的 DWORD FileMappingSize 值，後面接著值針對設定檔中的全域共用記憶體指定。 如果 FileMappingSize 值不存在，則個別的共用記憶體大小會設定為設定檔中的全域設定的第四個（1/4）。

## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
