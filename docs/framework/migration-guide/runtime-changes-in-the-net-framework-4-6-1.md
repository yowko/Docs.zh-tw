---
title: ".NET Framework 4.6.1 中的執行階段變更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework 執行階段變更"
  - ".NET Framework 4.6.1 在執行階段變更"
  - "應用程式相容性"
ms.assetid: 9d97421c-5fee-4523-98c9-a158e7e6a1ee
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# .NET Framework 4.6.1 中的執行階段變更
在某些罕見的情況下，執行階段變更可能會影響以舊版 .NET Framework 為目標，但在新版 .NET Framework 執行階段上執行的現有應用程式。 這些變更也包含在不同的 .NET Framework 執行階段環境中執行之應用程式間的行為差異。 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]還包含下列各方面的變更︰  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|WCF 繫結與`TransportWithMessageCredential`安全性模式|根據預設，WCF 繫結，會使用`TransportWithMessageCredential`安全性模式不允許使用不帶正負號的訊息 「 目標 」 標頭的非對稱安全性金鑰。 開始執行的應用程式[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]，就可以放寬這項需求，並接收不要簽署 「 目標 」 標頭的訊息。|這是一項可選擇加入的行為。 允許具有訊息 「 目標 」 標頭不帶正負號，加入下列組態設定來[ <> \> ](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)應用程式的組態檔區段︰<br /><br /> `<runtime>     <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />  </runtime>`<br /><br /> 由於這是可選擇加入的功能，因此不會影響現有應用程式的行為。|邊緣|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName>|當<xref:System.Windows.Controls.ItemsControl>顯示集合使用虛擬化 (<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> = `true`) 和項目捲動 (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>)，並捲動以顯示項目與其相鄰項目，其高度，單位為像素與不同的控制項時<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName>逐一查看集合中的所有項目。   在這個反覆項目; 兩者的 UI 完全沒有回應 如果是大型的集合，這可以視為停止回應。<br /><br /> 這個反覆項目就會發生在其他情況下，即使在之前的版本中[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]。 比方說，它發生於捲動的像素 (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>) 項目捲動時遇到與不同的像素高度和項目時階層式資料 (例如在<xref:System.Windows.Controls.TreeView>控制項或<xref:System.Windows.Controls.ItemsControl>與啟用的群組) 時遇到具有不同數目的子系的項目比相鄰的項目。<br /><br /> 項目捲動和不同的像素高度的情況下，針對反覆項目中所導入[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]能夠修正導致配置中的階層式資料。  如果是一般資料，則不會需要它 （具有沒有階層），而[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]不會在此情況下執行它。|如果反覆項目中出現[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]而不是在較早的版本-也就是如果<xref:System.Windows.Controls.ItemsControl>項目-可捲動的一般清單以及不同的像素高度-個項目有兩種解決方法︰<br /><br /> 安裝[.NET Framework 4.6.2](../../../docs/framework/install/guide-for-developers.md)。<br /><br /> 安裝[hotfix HR 1605](https://support.microsoft.com/en-us/kb/3154529)的[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]。|次要|  
  
## <a name="see-also"></a>另請參閱  
 [4.6.1 在應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)