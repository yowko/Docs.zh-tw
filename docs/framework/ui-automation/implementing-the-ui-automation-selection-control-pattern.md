---
title: "Implementing the UI Automation Selection Control Pattern | Microsoft Docs"
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
  - "Selection control pattern"
  - "UI Automation, Selection control pattern"
  - "control patterns, Selection"
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
caps.latest.revision: 33
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 33
---
# Implementing the UI Automation Selection Control Pattern
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的最新資訊，請參閱 [Windows Automation API：UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題將介紹實作 <xref:System.Windows.Automation.Provider.ISelectionProvider> 的方針和慣例，包括事件和屬性的相關資訊。 其他參考的連結列於主題的結尾。  
  
 <xref:System.Windows.Automation.SelectionPattern> 控制項模式是用以支援當作可選取子項目集合的容器使用的控制項。 這個項目的子系必須實作 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>。 如需實作此控制項模式的控制項範例，請參閱[Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## 實作方針和慣例  
 實作選取控制項模式時，請注意下列方針和慣例：  
  
-   實作 <xref:System.Windows.Automation.Provider.ISelectionProvider> 的控制項允許選取一個或多個子項目。 例如，清單方塊、清單檢視和樹狀檢視都支援多重選取，而下拉式方塊、滑桿和選項按鈕群組則支援單一選取。  
  
-   有最小值、最大值和連續範圍的控制項 \(如 \[音量\] 滑桿控制項\)，應實作 <xref:System.Windows.Automation.Provider.IRangeValueProvider>，而不是實作 <xref:System.Windows.Automation.Provider.ISelectionProvider>。  
  
-   若單一選取控制項有實作 <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot> 的子控制項，例如 \[顯示內容\] 對話方塊中的 \[螢幕解析度\] 滑桿或 [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] 的 \[色彩選擇器\] 選取控制項 \(如下所示\)，應實作 <xref:System.Windows.Automation.Provider.ISelectionProvider>，其子系應實作 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> 和 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>。  
  
 ![已反白顯示黃色的色彩選擇器](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA\_ValuePattern\_ColorPicker")  
色樣字串對應範例  
  
-   功能表不支援 <xref:System.Windows.Automation.SelectionPattern>。 若使用的功能表項目同時包含圖形和文字 \(例如 [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] \[檢視\] 功能表中的 \[預覽窗格\] 項目\)，而有必要傳達狀態，則應實作 <xref:System.Windows.Automation.Provider.IToggleProvider>。  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## ISelectionProvider 的必要成員  
 <xref:System.Windows.Automation.Provider.ISelectionProvider> 介面需要下列屬性、方法和事件。  
  
|必要成員|類型|備註|  
|----------|--------|--------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|屬性|應支援使用 <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> 和 <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A> 的屬性變更事件。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|屬性|應支援使用 <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> 和 <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A> 的屬性變更事件。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|方法|無|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|事件|當容器中的選項大幅變更，需要傳送比 <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> 常數所允許的更多新增和移除事件時，會引發此事件。|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> 和 <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> 屬性可以是動態的。 例如，控制項的最初狀態可能預設沒有選取任何項目，表示 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> 為 `false`。 不過，在選取項目之後，控制項就必須至少有一個項目一律保持為選取。 同樣地，在極少數的情況下，控制項可能會允許最初選取多個項目，但之後就只允許單一選取。  
  
<a name="Exceptions"></a>   
## 例外狀況  
 提供者必須擲回下列例外狀況。  
  
|例外狀況類型|條件|  
|------------|--------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|如果未啟用此控制項。|  
|<xref:System.InvalidOperationException>|如果隱藏此控制項。|  
  
## 請參閱  
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Support Control Patterns in a UI Automation Provider](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [Implementing the UI Automation SelectionItem Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)   
 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)