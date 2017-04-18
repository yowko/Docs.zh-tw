---
title: "&lt;performanceCounters&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<perfomanceCounters> 項目"
  - "performanceCounters 項目"
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;performanceCounters&gt; 項目
指定效能計數器所共用的全域記憶體的大小。  
  
## 語法  
  
```  
<performanceCounters filemappingsize="524288" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|filemappingsize|必要屬性。<br /><br /> 指定效能計數器所共用之全域記憶體的大小 \(以位元組計\)。  預設值為 524288。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`Configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|  
  
## 備註  
 效能計數器會使用記憶體對應檔或共用記憶體來發行效能資料，共用記憶體的大小可決定一次可使用多少個執行個體。共用記憶體有兩種類型：全域共用記憶體和個別共用記憶體。全域共用記憶體是由跟著 .NET Framework 1.0 或 1.1 版安裝的所有效能計數器分類所使用。跟著 .NET Framework 2.0 版安裝的效能計數器分類可使用個別共用記憶體，每一個效能計數器分類有它自己的記憶體。  
  
 全域共用記憶體的大小只能由組態檔來設定，預設的大小為 524,288 個位元組，最大值為 33,554,432 個位元組，而最小值為 32,768 個位元組。由於全域共用記憶體是由所有的處理序和分類所共用，所以第一位建立者會指定大小。如果您在應用程式組態檔中定義大小，則只有在此應用程式是第一個讓效能計數器執行的應用程式時，才會使用這個大小。因此，指定 `filemappingsize` 值的正確位置是 Machine.config 檔。全域共用記憶體中的記憶體不能由個別效能計數器釋放，因此，如果建立了大量且不同名稱之效能計數器執行個體，則全域共用記憶體最後還是會耗盡。  
  
 如需取得個別共用記憶體的大小，會先參考登錄機碼 HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\*\<category name\>*\\Performance 內的 DWORD FileMappingSize 值，接著是組態檔中為全域共用記憶體所指定的值。  如果 FileMappingSize 值不存在，則個別共用記憶體的大小會設定為組態檔中全域設定的四分之一 \(1\/4\)。  
  
## 請參閱  
 <xref:System.Diagnostics.PerformanceCounter>   
 <xref:System.Diagnostics.PerformanceCounterCategory>   
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>   
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>