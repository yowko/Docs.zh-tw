---
title: "UI Automation Support for the TreeItem Control Type | Microsoft Docs"
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
  - "control types, Tree Item"
  - "Tree Item control type"
  - "UI Automation, Tree Item control type"
ms.assetid: 229f341a-477f-434e-b877-4db9973068eb
caps.latest.revision: 22
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 22
---
# UI Automation Support for the TreeItem Control Type
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題提供 TreeItem 控制項類型的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 支援相關資訊。 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中，控制項類型是一組控制項必須符合才能使用 <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> 屬性的條件。 這些條件包括 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性值和控制項模式的特定指導方針。  
  
 TreeItem 控制項類型代表樹狀結構容器內的節點。 每個節點都可能包含其他節點，稱為「子節點」。 父節點或包含子節點的節點可以顯示為展開或摺疊。  
  
 下列章節會定義 TreeItem 控制項類型所需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、屬性、控制項模式和事件。 無論是 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、[!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 或 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]，[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 需求都適用於所有樹狀結構項目控制項。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## 必要的使用者介面自動化樹狀結構  
 下表描述與樹狀結構控制項相關之 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視和內容檢視，並說明各檢視中可包含的內容。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的詳細資訊，請參閱[UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)。  
  
|控制項檢視|內容檢視|  
|-----------|----------|  
|TreeItem<br /><br /> -   核取方塊 \(0 或 1\)<br />-   影像 \(0 或 1\)<br />-   按鈕 \(0 或 1\)<br />-   TreeItem \(0 個以上\)|TreeItem<br /><br /> -   TreeItem \(0 個以上\)|  
  
 樹狀結構項目控制項在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的內容檢視中可以有零個以上的樹狀結構項目子項。 如果樹狀結構項目控制項的功能超出下列控制項模式所公開的功能，則控制項應根據 Data Item 控制項類型而定。  
  
 摺疊的樹狀結構項目除非展開並可見 \(或可以捲動檢視\)，否則不會顯示在控制項檢視或內容檢視中。  
  
 控制項檢視可以包含控制項的額外詳細資訊，包括相關的影像或按鈕。 例如，大綱模式中的項目可能包含展開或摺疊大綱的影像以及按鈕。 因為資訊已經以父樹狀結構項目表示，所以這些詳細物件不會出現在內容檢視中。 捲動超出螢幕以外的樹狀結構項目會出現在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項和內容檢視中，而且應將 <xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> 設為 true。  
  
<a name="Required_UI_Automation_Properties"></a>   
## 必要的使用者介面自動化屬性  
 下表列示 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性，其值或定義與清單控制項特別有關。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性的詳細資訊，請參閱[UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性|值|備註|  
|------------------------------------------------------------------------------|-------|--------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|請參閱備註。|此屬性的值在應用程式中的所有控制項都不得重複。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|請參閱備註。|包含整個控制項的最外層矩形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|請參閱備註。|此屬性必須傳回項目的位置，使項目變更選取狀態或變成焦點所在。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|TreeItem|此值與所有使用者介面架構的值相同。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|此清單控制項一律包含在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的內容檢視。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|此清單控制項一律包含在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|請參閱備註。|此屬性可設定來表示樹狀結構項目捲動超出螢幕以外。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|請參閱備註。|如果控制項可接收鍵盤焦點，就必定支援此屬性。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|請參閱備註。|如果樹狀結構項目控制項使用視覺圖示來表示這是特定類型的物件，則必須支援此屬性並指出物件為何。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|樹狀結構項目控制項會自行設定標籤。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|「樹狀結構項目」|對應到 TreeItem 控制項類型的當地語系化字串。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|請參閱備註。|此屬性會公開每個樹狀結構項目控制項顯示的文字。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## 必要的使用者介面自動化控制項模式  
 下表列出清單控制項支援所需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項模式。 如需控制項模式的詳細資訊，請參閱[UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)。  
  
|控制項模式\/模式屬性|支援\/值|備註|  
|-----------------|-----------|--------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|視情況而定|如果樹狀結構項目有個別可執行動作的命令，即實作此控制項模式。|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|是|所有樹狀結構項目都可以展開或摺疊。|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|已展開、已摺疊或分葉節點|當樹狀結構項目未展開或摺疊時，表示是分葉節點。|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|視情況而定|如果樹狀結構容器支援捲軸控制項模式，即實作此控制項模式。|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|視情況而定|若在使用者回到樹狀結構容器時可以維持作用中的選取範圍，即實作此控制項模式。|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|是|此屬性將為容器內的所有項目公開相同的容器。|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|視情況而定|如果樹狀結構項目有相關聯的核取方塊，即實作此控制項模式。|  
  
<a name="Required_UI_Automation_Events"></a>   
## 必要的使用者介面自動化事件  
 下表列出所有樹狀結構項目控制項都必須支援的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。 如需事件的詳細資訊，請參閱[UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件|支援|備註|  
|------------------------------------------------------------------------------|--------|--------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要項|無|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|視情況而定|無|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|視情況而定|無|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|視情況而定|無|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|視情況而定|無|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|視情況而定|無|  
  
## 請參閱  
 <xref:System.Windows.Automation.ControlType.TreeItem>   
 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)   
 [UI Automation Overview](../../../docs/framework/ui-automation/ui-automation-overview.md)