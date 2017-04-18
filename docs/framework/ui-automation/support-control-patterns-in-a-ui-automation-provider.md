---
title: "Support Control Patterns in a UI Automation Provider | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control patterns, supporting in UI Automation provider"
  - "UI Automation, supporting control patterns in provider"
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
caps.latest.revision: 13
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 13
---
# Support Control Patterns in a UI Automation Provider
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題說明如何在使用者介面自動化提供者上實作一個或多個控制項模式，讓用戶端應用程式能夠操作控制項並從中取得資料。  
  
### 支援控制項模式  
  
1.  針對項目應該支援的控制項模式，實作適當的介面，例如適用於 <xref:System.Windows.Automation.InvokePattern> 的 <xref:System.Windows.Automation.Provider.IInvokeProvider>。  
  
2.  在 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=fullName> 實作中，傳回包含每個控制項介面實作的物件  
  
## 範例  
 下列範例示範單一選取自訂清單方塊的 <xref:System.Windows.Automation.Provider.ISelectionProvider> 實作。 它會傳回三個屬性並取得目前選取的項目。  
  
 [!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
 [!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]  
  
## 範例  
 下列範例示範 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> 的實作，它會傳回實作 <xref:System.Windows.Automation.Provider.ISelectionProvider> 的類別。 大部分清單方塊也會支援其他模式，但在本範例中會針對所有其他模式識別項傳回 Null 參考 \(在 [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)] 中為 `Nothing`\)。  
  
 [!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
 [!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]  
  
## 請參閱  
 [UI Automation Providers Overview](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)   
 [Server\-Side UI Automation Provider Implementation](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)