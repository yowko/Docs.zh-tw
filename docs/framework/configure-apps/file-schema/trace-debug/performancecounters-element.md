---
title: "&lt;performanceCounters&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f7fdbb244663e5114880437a5a508270c80a9c79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltperformancecountersgt-element"></a>&lt;performanceCounters&gt;項目
指定效能計數器共用之全域記憶體的大小。  
  
 \<configuration>  
\<system.diagnostics >  
\<performanceCounters >  
  
## <a name="syntax"></a>語法  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|filemappingsize|必要屬性。<br /><br /> 指定的大小，以位元組為單位的效能計數器所共用的全域記憶體。 預設值為 524288。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`Configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|  
  
## <a name="remarks"></a>備註  
 效能計數器會使用記憶體對應檔案或共用的記憶體，來發行效能資料。  共用記憶體的大小會決定可以一次使用多少個執行個體。  有兩種類型的共用記憶體： 全域共用記憶體和不同的共用的記憶體。  .NET framework 1.0 或 1.1 與安裝的所有效能計數器分類會都使用全域共用的記憶體。  安裝.NET framework 2.0 版的效能計數器分類使用不同的共用的記憶體，且每個效能計數器分類有它自己的記憶體。  
  
 僅使用組態檔，可以設定全域共用記憶體的大小。  預設大小為 524288 個位元組，大小上限為 33554432 個位元組，而最小大小為 32,768 位元組。  由於全域共用的記憶體共用的所有處理程序與類別，第一個建立者指定的大小。  如果您在應用程式組態檔中定義的大小，如果您的應用程式會導致效能計數器執行第一個應用程式只使用該大小。  因此正確的位置來指定`filemappingsize`值是在 Machine.config 檔案。  無法由個別效能計數器，因此最後還是會建立大量的效能計數器執行個體使用不同的名稱，如果已用完全域共用的記憶體釋放中全域共用記憶體的記憶體。  
  
 對於不同的共用記憶體的大小，DWORD FileMappingSize 在登錄機碼值 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<類別名稱 >*\Performance 參考首先，後面接著全域共用記憶體，在組態檔中指定的值。 如果 FileMappingSize 值不存在，則不同的共用的記憶體大小會設定一個第四個 (1/4) 組態檔中的全域設定。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
