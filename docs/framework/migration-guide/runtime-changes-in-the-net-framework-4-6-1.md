---
title: ".NET Framework 4.6.1 中的執行階段變更 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes, .NET Framework
- runtime changes, .NET Framework 4.6.1
- application compatibility
ms.assetid: 9d97421c-5fee-4523-98c9-a158e7e6a1ee
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b8c6ec4d0bad4a769fb4d19a98c9e8a4eda0db78
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-461"></a>.NET Framework 4.6.1 中的執行階段變更
在某些罕見的情況下，執行階段變更可能會影響以舊版 .NET Framework 為目標，但在新版 .NET Framework 執行階段上執行的現有應用程式。 這些變更也包含在不同的 .NET Framework 執行階段環境中執行之應用程式間的行為差異。 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 包含下列區域的變更：  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|使用 `TransportWithMessageCredential` 安全性模式的 WCF 繫結|根據預設，使用 `TransportWithMessageCredential` 安全性模式的 WCF 繫結不允許針對非對稱安全性金鑰使用含不帶正負號 "to" 標頭的訊息。 從以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 執行的應用程式開始，可放寬這項需求，並接收不帶正負號 "to" 標頭的訊息。|這是一項可選擇加入的行為。 若要允許不帶正負號 "to" 標頭的訊息，請將下列組態設定新增至應用程式組態檔的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段：<br /><br /> `<runtime>     <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />  </runtime>`<br /><br /> 由於這是可選擇加入的功能，因此不會影響現有應用程式的行為。|Edge|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName>|當 <xref:System.Windows.Controls.ItemsControl> 顯示使用虛擬化 (<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> = `true`) 和項目捲動 (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>) 的集合，且此控制項捲動以顯示高度 (像素) 與其相鄰項目不同的項目時，<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> 會逐一查看集合中的所有項目。   此 UI 在逐一查看期間沒有回應；如果集合很大，這可視為停止回應。<br /><br /> 此逐一查看行為會出現在其他情況下，即使在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 之前的版本中也一樣。 例如，當像素捲動 (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>) 遇到具有不同像素高度的項目，以及項目捲動階層式資料 (例如在已啟用分組功能的 <xref:System.Windows.Controls.TreeView> 控制項或 <xref:System.Windows.Controls.ItemsControl> 中) 遇到具有與其相鄰項目不同子系項目數的項目時，就會發生此行為。<br /><br /> 針對項目捲動和不同像素高度的情況，[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中引進了逐一查看，以修正階層式資料配置中的錯誤 (bug)。  如果是單層式資料 (沒有階層)，則不需要逐一查看，而且 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 在此情況下不會這麼做。|如果 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中出現逐一查看行為，但舊版中並未出現 (亦即如果 <xref:System.Windows.Controls.ItemsControl> 是在具有不同像素高度項目之簡單列表中的項目捲動)，則有兩個解決方式：<br /><br /> 安裝 [.NET Framework 4.6.2](../../../docs/framework/install/guide-for-developers.md)。<br /><br /> 安裝 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 的 [Hotfix HR 1605](https://support.microsoft.com/en-us/kb/3154529)。|次要|  
## <a name="see-also"></a>另請參閱  
 [4.6.1 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
