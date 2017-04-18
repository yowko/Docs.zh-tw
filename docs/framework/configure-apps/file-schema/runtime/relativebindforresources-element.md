---
title: "&lt;relativeBindForResources&gt; 項目 | Microsoft Docs"
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
  - "<relativeBindForResources> 項目"
  - "RelativeBindForResources 項目"
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;relativeBindForResources&gt; 項目
最佳化附屬組件的探查。  
  
## 語法  
  
```vb  
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定 Common Language Runtime 是否最佳化附屬組件的探查。|  
  
## 啟用屬性  
  
|值|說明|  
|-------|--------|  
|`false`|執行階段不會最佳化附屬組件的探查。  此為預設值。|  
|`true`|執行階段最佳化附屬組件的探查。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含與執行階段初始化選項有關的資訊。|  
  
## 備註  
 一般來說，資源管理員資源探查，如 [封裝和部署資源](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) 主題中所提供。  這表示，當資源管理員探查資源的特定當地語系化版本時，它可能會查看全域組件快取，查看應用程式程式碼基底的特定文化特性資料夾，為附屬組件查詢 Windows Installer ，以及引發 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> 事件。  `<relativeBindForResources>` 元素最佳化資源管理員附屬組件探查的方式。  它可以改善效能，當探查資源在下列情況時：  
  
-   在附屬組件中部署位置和程式碼組件相同。  換句話說，如果程式碼組件安裝在全域組件快取，附屬組件也必須安裝於此。  如果程式碼組件安裝於應用程式程式碼基底，附屬組件也必須安裝在程式碼基底的特定文化特性資料夾。  
  
-   當 Windows Installer 不使用，或很少使用且僅用於附屬組件的隨選安裝。  
  
-   當應用程式程式碼不會處理 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> 事件。  
  
 設定 `<relativeBindForResources>` 項目的 `enabled` 屬性為 `true` 最佳化附屬組件中的資源管理員的探查如下：  
  
-   其使用父程式碼組件的位置指定附屬組件的探查。  
  
-   它不會查詢附屬組件的 Windows Installer。  
  
-   這樣做不會引發 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> 事件。  
  
## 請參閱  
 [封裝和部署資源](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)   
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)