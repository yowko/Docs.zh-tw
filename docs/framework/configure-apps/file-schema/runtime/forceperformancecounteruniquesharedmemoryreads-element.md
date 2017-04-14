---
title: "&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<forcePerformanceCounterUniqueSharedMemoryReads> 項目"
  - "forcePerformanceCounterUniqueSharedMemoryReads 項目"
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; 項目
指定 PerfCounter.dll 是否在 .NET Framework 1.1 版應用程式中使用 CategoryOptions 登錄設定，來決定要從分類特定的共用記憶體或全域記憶體載入效能計數器資料。  
  
## 語法  
  
```  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指示 PerfCounter.dll 是否使用 CategoryOptions 登錄設定，來決定是否要從分類特定的共用記憶體或全域記憶體載入效能計數器資料。|  
  
## 啟用屬性  
  
|值|說明|  
|-------|--------|  
|`false`|PerfCounter.dll 並不會使用 CategoryOptions 登錄設定，這是預設值。|  
|`true`|PerfCounter.dll 不會使用 CategoryOptions 登錄設定。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 之前的 .NET Framework 版本中，已載入的 PerfCounter.dll 版本都對應於已載入處理序中的執行階段。  如果電腦有安裝 .NET Framework 1.1 版和 [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)]，.NET Framework 1.1 應用程式便會載入 PerfCounter.dll 的 .NET Framework 1.1 版本。  從 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 開始，都會載入最新安裝的 PerfCounter.dll 版本。  這表示如果電腦上有安裝 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，.NET Framework 1.1 應用程式將會載入 PerfCounter.dll 的 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 版本。  
  
 從 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 開始，當使用效能計數器時，PerfCounter.dll 都會檢查每個提供者的 CategoryOptions 登錄項目，以判斷應該從分類特定的共用記憶體或全域共用記憶體讀取。  .NET Framework 1.1 PerfCounter.dll 不會讀取該登錄項目，因為它無法感知分類特定的共用記憶體，永遠都會從全域共用記憶體讀取。  
  
 為符合回溯相容性，[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll 在 .NET Framework 1.1 應用程式中執行時，不會檢查 CategoryOptions 登錄項目。  它只是使用全域共用記憶體，就像 .NET Framework 1.1 PerfCounter.dll 一樣。  不過，您可以指示 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll 藉由啟用 `<forcePerformanceCounterUniqueSharedMemoryReads>` 項目，來檢查登錄設定。  
  
> [!NOTE]
>  啟用 `<forcePerformanceCounterUniqueSharedMemoryReads>` 項目，並不保證會使用特定分類的共用記憶體。  啟用為 `true` 的設定只會使 PerfCounter.dll 參考 CategoryOptions 登錄設定。  CategoryOptions 的預設設定是使用分類特定的共用記憶體。不過，您可以變更 CategoryOptions 以指示應該使用全域共用記憶體。  
  
 包含 CategoryOptions 設定的登錄機碼是 HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\Services\\\<categoryName\>\\Performance。  預設情況下，CategoryOptions 設定為 3，指示 PerfCounter.dll 使用特定分類的共用記憶體。  如果 CategoryOptions 設為 0，PerfCounter.dll 就會使用全域共用記憶體。  只有所建立之執行個體的名稱與重複使用的執行個體相同時，才會重複使用執行個體資料。  所有版本都將能夠寫入該類別。  如果 CategoryOptions 設定為 1，就會使用全域共用記憶體，但如果類別名稱的長度與重複使用的分類相同，即可重複使用執行個體資料。  
  
 0 和 1 的設定可能會導致記憶體遺漏和效能計數器記憶體的填入。  
  
## 範例  
 下列範例會示範如何指定 PerfCounter.dll 應該參考 CategoryOptions 登錄項目，以判斷它是否應該使用分類特定的共用記憶體。  
  
```  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)