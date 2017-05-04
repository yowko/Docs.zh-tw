---
title: "風險降低：自訂 IMessageFilter.PreFilterMessage 實作 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d85c827b414cc94410a921bfae9ce3e1764d22ea
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>風險降低：自訂 IMessageFilter.PreFilterMessage 實作
在以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和更新版本為目標的 Windows Forms 應用程式中，自訂 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 實作可以在呼叫 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> 方法時安全地篩選訊息，但前提是 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 實作必須：  
  
-   則會執行下列其中一項或兩項：  
  
    -   呼叫 <xref:System.Windows.Forms.Application.AddMessageFilter%2A> 方法來新增訊息篩選器。  
  
    -   呼叫 <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> 方法來移除訊息篩選器。 方法。  
  
-   **而且**藉由呼叫 <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName> 方法來提取訊息。  
  
## <a name="impact"></a>影響  
 這項變更只會影響以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和更新版本為目標的 Windows Forms 應用程式。  
  
 若是以舊版 .NET Framework 為目標的 Windows Forms 應用程式，這類實作在某些情況下會在呼叫 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> 方法時，擲回 <xref:System.IndexOutOfRangeException> 例外狀況  
  
## <a name="mitigation"></a>風險降低  
 如果這不是您要的變更，以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 或更新版本為目標的應用程式，可以藉由將下列組態設定新增至應用程式組態檔的 [\<執行階段>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，來選擇退出這項行為：  
  
```xml  
  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />   
</runtime>  
  
```  
  
 此外，以舊版 .NET Framework 為目標，但在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 或更新版本下執行的應用程式，可以藉由將下列組態設定新增至應用程式組態檔的 [\<執行階段>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，來選擇加入這項行為：  
  
```xml  
  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />   
</runtime>  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
