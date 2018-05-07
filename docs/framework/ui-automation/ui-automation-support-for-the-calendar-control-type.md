---
title: Calendar 控制項類型的 UI 自動化支援
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Calendar control type
- Calendar control type
- control types, Calendar
ms.assetid: e91a7393-a7f9-4838-a1a6-857438b24bc9
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 752ac4cfddd5ca8c8b42d05e1a452cd0ef60ee36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-support-for-the-calendar-control-type"></a>Calendar 控制項類型的 UI 自動化支援
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題提供月曆控制項類型的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 支援相關資訊。 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中，控制項類型是一組控制項條件，控制項必須符合條件才能使用 <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> 屬性。 這些條件包括 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性值、控制項模式和 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件的特定指導方針。  
  
 月曆控制項可讓使用者輕鬆判斷日期並選取其他的日期。  
  
 下列章節會定義月曆控制項類型所需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、屬性、控制項模式和事件。 無論是 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]或 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]， [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]需求都適用於所有月曆控制項。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>必要的使用者介面自動化樹狀結構  
 下表描述月曆控制項之 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視和內容檢視，並說明各檢視中可包含的內容。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的詳細資訊，請參閱 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)。  
  
|控制項檢視|內容檢視|  
|------------------|------------------|  
|行事曆<br /><br /> <ul><li>DataGrid<br /><br /> <ul><li>標題 (0 或 1)</li><li>HeaderItem (0 或 7；數量取決於資料行中要顯示多少天)</li><li>ListItem (數量取決於要顯示多少天)</li><li>按鈕 (0 或 2；用於分頁月曆檢視)</li></ul></li></ul>|行事曆<br /><br /> -ListItem （數量取決於要顯示多少天）|  
  
 月曆控制項可以在使用者介面中以許多不同的形式來表示。 唯一保證位於 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構控制項檢視中的控制項為資料格、標題、標題項目和清單項目控制項。  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必要的使用者介面自動化屬性  
 下表列出 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性，其值或定義與月曆控制項特別有關。 如需有關[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]屬性，請參閱[用戶端的使用者介面自動化屬性](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性|值|注意|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|請參閱備註。|此屬性的值在應用程式中的所有控制項都不得重複。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|請參閱備註。|包含整個控制項的最外層矩形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|請參閱備註。|如果有週框即受支援。 如果週框中沒有任何可點選的點，而且您執行的是特殊化點擊測試，則會覆寫並提供可點選的點。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Calendar|此值與所有 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 架構的值相同。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|此月曆控制項一律包含在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的內容檢視中。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|此月曆控制項一律包含在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|請參閱備註。|如果控制項可接收鍵盤焦點，就必定支援此屬性。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|請參閱備註。|文件控制項的標籤。 通常會使用該文件的標題。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|「月曆」|對應到月曆控制項類型的當地語系化字串。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|請參閱備註。|月曆控制項通常會從目前的日期取得其名稱。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>必要的使用者介面自動化控制項模式  
 下表列出所有月曆控制項必須支援的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項模式。 如需控制項模式的詳細資訊，請參閱 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)。  
  
|控制項模式/模式屬性|支援|注意|  
|---------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|[是]|月曆控制項一律支援格線模式，因為月份的日期是需要空間來巡覽的項目。|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|視情況而定|大部分的月曆控制項都支援依頁面翻閱檢視。 建議使用捲軸模式，以支援分頁巡覽。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|視情況而定|大部分月曆控制項都會保留特定日、月或年做為子項目的選項。 部分月曆可複選，而其他則僅允許單選。|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|[是]|月曆控制項在其子樹狀結構一律會有星期幾的標題，因此必須支援表格模式。|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|否|因為您無法在月曆控制項上直接設定值，所以該控制項不需要值控制項模式。 如果有與控制項相關聯的特定日期，則應由選取控制項模式提供資訊。|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>必要的使用者介面自動化事件  
 下表列出所有月曆控制項都必須支援的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。 如需事件的詳細資訊，請參閱 [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件|支援|注意|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要|無|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> 屬性變更事件。|視情況而定|如果此控制項支援捲軸控制項模式，就必須支援這個事件。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> 屬性變更事件。|視情況而定|如果此控制項支援捲軸控制項模式，就必須支援這個事件。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> 屬性變更事件。|視情況而定|如果此控制項支援捲軸控制項模式，就必須支援這個事件。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> 屬性變更事件。|視情況而定|如果此控制項支援捲軸控制項模式，就必須支援這個事件。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> 屬性變更事件。|視情況而定|如果此控制項支援捲軸控制項模式，就必須支援這個事件。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> 屬性變更事件。|視情況而定|如果此控制項支援捲軸控制項模式，就必須支援這個事件。|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|必要|無|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Automation.ControlType.Calendar>  
 [UI 自動化控制項類型概觀](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI 自動化概觀](../../../docs/framework/ui-automation/ui-automation-overview.md)
