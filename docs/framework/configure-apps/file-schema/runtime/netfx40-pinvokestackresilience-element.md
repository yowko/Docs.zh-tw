---
title: "&lt;NetFx40_PInvokeStackResilience&gt; 項目 | Microsoft Docs"
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
  - "<NetFx40_PInvokeStackResilience> 項目"
  - "NetFx40_PInvokeStackResilience 項目"
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;NetFx40_PInvokeStackResilience&gt; 項目
指定執行階段是否會在執行階段期間自動修正不正確的平台叫用，其代價是 Managed 與 Unmanaged 程式碼之間的較慢轉換。  
  
## 語法  
  
```  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定執行階段是否會在 32 位元平台上於執行階段期間偵測不正確的平台叫用宣告，並且自動修正堆疊。|  
  
## 啟用屬性  
  
|值|說明|  
|-------|--------|  
|`0`|執行階段會使用 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 所引入的較快的 Interop 封送處理架構，這樣不會偵測並修正不正確的平台叫用宣告。  這是預設值。|  
|`1`|執行階段會使用較慢的轉換，可偵測並修正不正確的平台叫用宣告。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含與執行階段初始化選項有關的資訊。|  
  
## 備註  
 這個項目可讓您犧牲較快的 Interop 封送處理，以交換針對不正確平台叫用宣告的執行階段恢復。  
  
 從 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 開始，精簡的 Interop 封送處理架構就提供了從 Managed 程式碼轉換至 Unmanaged 程式碼的大幅效能改進。  在舊版的 .NET Framework 中，封送處理層會偵測到 32 位元平台上的不正確平台叫用宣告，並會自動修正堆疊。  新的封送處理架構消除了這個步驟。  因此，轉換都非常快速，但不正確的平台叫用宣告可能會造成程式失敗。  
  
 為了能在開發期間輕鬆偵測不正確的宣告，已經顯著改進了 Visual Studio 偵錯經驗。  [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) Managed 偵錯助理 \(MDA\) 會在應用程式附加偵錯工具執行時，通知您不正確的平台叫用宣告。  
  
 若要處理應用程式使用您無法重新編譯的元件，並有不正確平台叫用宣告的案例，您可以使用 `NetFx40_PInvokeStackResilience` 項目。  將這個項目加入至您的應用程式組態檔，以 `enabled="1"` 的選項進入相容性模式，具有 .NET Framework 舊版的行為，但付出轉換較慢的代價。  針對舊版 .NET Framework 編譯的組件，都會自動選擇進入此相容性模式，而不需要此項目。  
  
## 組態檔  
 這個項目只能在應用程式組態檔中使用。  
  
## 範例  
 下列範例會示範如何選擇對應用程式的不正確平台叫用宣告增加恢復，其代價是在 Managed 和  Unmanaged 程式碼之間的轉換減慢。  
  
```  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)