---
title: "緩和：自訂 IMessageFilter.PreFilterMessage 實作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 2
---
# 緩和：自訂 IMessageFilter.PreFilterMessage 實作
在以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的 Windows Forms 應用程式中，自訂 [](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md "<runtime> Element") 實作可以在呼叫 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> 方法時安全地篩選訊息，如果 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 實作：  
  
-   執行下列其中一項或兩項：  
  
    -   呼叫 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 方法來加入訊息篩選器。  
  
    -   呼叫 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 方法來移除訊息篩選器。 方法。  
  
-   並且[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]呼叫 [](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md "<runtime> Element") 方法來激發訊息。  
  
## 影響  
 這項變更只會影響以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的 Windows Forms 應用程式。  
  
 針對以舊版 .NET Framework 為目標的 Windows Forms 應用程式，在某些情況下這類實作會在呼叫 [](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md "<runtime> Element") 方法時擲回 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 例外狀況  
  
## 緩和  
 如果這不是您要的變更，以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的應用程式，可以藉由將下列組態設定加入應用程式組態檔的 [\<runtime\>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段來選擇退出：  
  
```xml  
  
<runtime> <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" /> </runtime>  
  
```  
  
 此外，以舊版 .NET Framework 為目標，但在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 下執行的應用程式，可以藉由將下列組態設定加入應用程式組態檔的 [\<runtime\>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段來選擇加入：  
  
```xml  
  
<runtime> <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" /> </runtime>  
  
```  
  
## 請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)