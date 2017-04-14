---
title: "&lt;applicationPool&gt; 項目 (Web 設定) | Microsoft Docs"
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
  - "<applicationPool> 項目"
  - "applicationPool 項目"
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# &lt;applicationPool&gt; 項目 (Web 設定)
指定當 ASP.NET 應用程式在 [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] \(含\) 以後版本中以「整合」模式執行時，ASP.NET 用來管理整個處理序行為的組態設定。  
  
> [!IMPORTANT]
>  只有在 ASP.NET 應用程式裝載於 [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] \(含\) 以後版本時，這個項目及其支援的功能才適用。  
  
## 語法  
  
```  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`maxConcurrentRequestsPerCPU`|指定 ASP.NET 允許每個 CPU 可以有多少同時要求。|  
|`maxConcurrentThreadsPerCPU`|指定每個 CPU 的應用程式集區可以執行多少同時執行緒。  如此即可提供另一種方式來控制 ASP.NET 並行，因為您可以限制每個 CPU 可用來服務要求的 Managed 執行緒數目。  這個設定預設為 0，表示雖然 CLR 執行緒集區也會限制可建立的執行緒數目，但是 ASP.NET 不限制每個 CPU 可建立的執行緒數目。|  
|`requestQueueLimit`|指定 ASP.NET 可在單一處理序中佇列要求的最大數目。  當兩個以上的 ASP.NET 應用程式在單一應用程式集區中執行時，任何應用程式發出的累計要求集合都受限於這個設定。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|[\<system.web\>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|包含 ASP.NET 與主應用程式互動方式的相關資訊。|  
  
## 備註  
 當您在「整合」模式中執行 [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] \(含\) 以後版本時，這個項目組合可讓您設定 ASP.NET 管理執行緒的方式，以及在 IIS 應用程式集區中裝載應用程式時，ASP.NET 佇列要求的方式。  如果您執行 IIS 6，或是在「傳統」或 ISAPI 模式中執行 [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] \(含\) 以後版本，則會忽略這些設定。  
  
 `applicationPool` 設定適用於所有在 .NET Framework 特定版本上執行的應用程式集區。  這個設定包含在 aspnet.config 檔中。  這個檔案在 .NET Framework 的 2.0 和 4 版中各有一個版本 \(.NET Framework 的 3.0 和 3.5 版會與 2.0 版共用 aspnet.config 檔\)。  
  
> [!IMPORTANT]
>  如果在 [!INCLUDE[win7](../../../../../includes/win7-md.md)] 上執行 [!INCLUDE[iisver](../../../../../includes/iisver-md.md)]，您可以為每個應用程式集區設定不同的 aspnet.config 檔。  如此一來，即可針對每個應用程式集區自訂執行緒的效能。  
  
 就 `maxConcurrentRequestsPerCPU` 設定而言，除非每個 CPU 真的有 5000 個以上的要求，否則 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 中的預設設定 "5000" 足以有效關閉 ASP.NET 控制的要求節流。  不過這個預設設定必須依賴 CLR 執行緒集區，才能夠自動管理每個 CPU 的並行存取。  如果應用程式大量使用非同步要求處理，或是有許多長時間執行的要求阻塞在網路 I\/O 上，這些應用程式將會因為 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 中增加的預設限制而受惠。  將 `maxConcurrentRequestsPerCPU` 設定為零會關閉使用 Managed 執行緒處理 ASP.NET 要求的功能。  當應用程式在 IIS 應用程式集區中執行時，那些要求會停留在 IIS I\/O 執行緒，因此並行存取會由 IIS 執行緒設定來節流。  
  
 `requestQueueLimit` 設定的運作方式與 [processModel](http://msdn.microsoft.com/zh-tw/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) 項目的 `requestQueueLimit` 屬性相同，這個項目可在 ASP.NET 應用程式的 Web.config 檔中設定。  但是，aspnet.config 檔中的 `requestQueueLimit` 設定會覆寫 Web.config 檔中的 `requestQueueLimit` 設定。  換句話說，如果兩個屬性都已設定 \(預設值為 true\)，aspnet.config 檔中的 `requestQueueLimit` 設定會優先適用。  
  
## 範例  
 下列範例示範如何在下列情況中，於 aspnet.config 檔內設定 ASP.NET 的整個處理序行為。  
  
-   應用程式裝載於 [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] 應用程式集區。  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] 以「整合」模式執行。  
  
-   應用程式使用的是 [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] \(含\) 以後版本。  
  
 範例中的值是預設值。  
  
```  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## 項目資訊  
  
|||  
|-|-|  
|命名空間||  
|結構描述名稱||  
|驗證檔||  
|可以是空白||  
  
## 請參閱  
 [\<system.web\> 項目 \(Web 設定\)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)