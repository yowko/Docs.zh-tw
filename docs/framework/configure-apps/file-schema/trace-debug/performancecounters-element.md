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
ms.openlocfilehash: 6144bcbda69b2ba799e87c3e7fa2118fbe4d9bf6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673729"
---
# <a name="performancecounters-element"></a>\<performanceCounters > 項目

指定效能計數器共用之全域記憶體的大小。

 \<configuration>\
\<system.diagnostics>\
\<performanceCounters>

## <a name="syntax"></a>語法

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|filemappingsize|必要屬性。<br /><br /> 指定的大小，以位元組為單位，效能計數器所共用之全域記憶體。 預設值為 524288。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|`Configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|

## <a name="remarks"></a>備註

效能計數器會使用記憶體對應檔案或共用的記憶體，來發行效能資料。  共用記憶體的大小會決定可以一次使用多少個執行個體。  有兩種類型的共用記憶體： 全域共用記憶體和不同的共用的記憶體。  1.0 或 1.1 版的.NET Framework 版本與安裝的所有效能計數器分類會都使用全域共用的記憶體。  安裝.NET framework 2.0 版的效能計數器類別會使用不同的共用的記憶體，與每個效能計數器分類都有它自己的記憶體。

僅使用組態檔，可以設定全域共用記憶體的大小。  預設大小為 524288 個位元組，大小上限是 33,554,432 位元組為單位，最小大小為 32768 個位元組。  因為所有的處理程序與類別共用通用的共用的記憶體，第一次的建立者指定的大小。  如果您在應用程式組態檔中定義的大小，是只會使用該大小，您的應用程式是否會導致要執行的效能計數器的第一個應用程式。  因此正確的位置來指定`filemappingsize`值是在 Machine.config 檔案。  無法釋放中全域共用記憶體的記憶體，由個別的效能計數器，因此最後還是全域共用的記憶體用完，如果會建立大量的效能計數器執行個體，以不同的名稱。

針對不同的共用記憶體的大小，在登錄中的 DWORD FileMappingSize 值索引鍵 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<類別名稱 >* \Performance 參考首先，後面接著全域共用記憶體的組態檔中指定的值。 如果 FileMappingSize 值不存在，則不同的共用的記憶體大小設定為其中一個第四個 (1/4) 組態檔中的全域設定。

## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
