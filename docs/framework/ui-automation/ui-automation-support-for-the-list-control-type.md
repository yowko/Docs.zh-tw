---
title: List 控制項類型的 UI 自動化支援
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 015eb38038f85621d027ef82118bf4133a45917a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659651"
---
# <a name="ui-automation-support-for-the-list-control-type"></a>List 控制項類型的 UI 自動化支援
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題提供清單控制項類型的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 支援相關資訊。 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中，控制項類型是一組控制項條件，控制項必須符合條件才能使用 <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> 屬性。 這些條件包括 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性值和控制項模式的特定方針。  
  
 清單控制項類型提供了組織一組以上相同項目的方法，並可讓使用者選取一個以上的項目。 清單控制項類型對於可以包含的子項目限制並不嚴格。 這可讓使用者介面自動化提供者支援選取範圍容器的已知項目。  
  
 無論是 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]或 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]， [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]需求都適用於下列章節實作清單控制項類型的所有控制項。 清單控制項是實作清單控制項類型的控制項範例。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>必要的使用者介面自動化樹狀結構  
 下表說明與清單控制項相關的兩種 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構檢視，並說明每種檢視所包含的內容。 控制項檢視只包含屬於控制項的項目，內容檢視則會從樹狀結構移除多餘的資訊。 例如，用來設定下拉式方塊標籤的文字控制項將公開為 `ComboBox NameProperty`。 由於文字控制項已在控制項檢視中透過這種方式公開，就無須公開兩次，因此會從內容檢視移除。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的詳細資訊，請參閱 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)。  
  
|控制項檢視|內容檢視|  
|------------------|------------------|  
|包含對應控制項的項目。|從樹狀結構移除多餘資訊，使輔助技術得以處理對使用者有意義的最小資訊集。|  
|清單<br /><br /> -DataItem （0 或以上）<br />-ListItem （0 或以上）<br />群組 （0 或以上）<br />-捲軸 （0、 1 或 2）|清單<br /><br /> -DataItem （0 或以上）<br />-ListItem （0 或以上）<br />群組 （0 或以上）|  
  
 針對實作清單控制項類型的控制項 (例如清單控制項)，其控制項檢視包含：  
  
-   在清單控制項內零個以上的項目 (可以是 List Item 或 Data Item 控制項類型的項目)  
  
-   清單控制項中零個以上的群組控制項  
  
-   0、1 或 2 個捲軸控制項  
  
-  
  
 針對實作清單控制項類型的控制項 (例如清單控制項)，其內容檢視包含：  
  
-   在清單控制項內零個以上的項目 (可以是清單項目或資料項目控制項類型的項目)  
  
-   清單控制項中零個以上的群組  
  
 除了集中成群組的項目，清單控制項所包含的項目不能有階層式關聯性。 如果項目在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構中有子系，那麼清單容器就應為樹狀結構控制項類型。  
  
 清單控制項中可選取的項目，將從清單控制項之 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構中的子系取得。 清單控制項內的所有項目都必須屬於相同的選取群組。 清單中可選取的項目，應該公開為 ListItem (而非 DataItem) 控制項類型。  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必要的使用者介面自動化屬性  
 下表列出 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性，其值或定義與清單控制項特別有關。 如需詳細資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]屬性，請參閱[UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性|值|注意|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|請參閱備註。|此屬性的值在應用程式中的所有控制項都不得重複。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|請參閱備註。|包含整個控制項的最外層矩形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|請參閱備註。|如果清單控制項有可按的點 (可以按一下讓清單取得焦點的點)，則該點必須透過此屬性公開。<br /><br /> 如果值`IsOffScreen`屬性為 true，則<xref:System.Windows.Automation.NoClickablePointException>就會引發。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|請參閱備註。|如果控制項可接收鍵盤焦點，就必定支援此屬性。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|請參閱備註。|清單控制項的 Name 屬性值應傳遞要求使用者選取的選項類別。 此屬性通常會從靜態文字標籤取得其名稱。 如果沒有靜態文字標籤，應用程式開發人員就必須公開 Name 屬性的值。<br /><br /> 清單控制項唯一不需要此屬性的情況是，當控制項用於其他控制項的樹狀子目錄時。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|請參閱備註。|如果有靜態文字標籤，那麼這個屬性必須公開該控制項的參考。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|清單|此值與所有使用者介面架構的值相同。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|「清單」|對應到清單控制項類型的當地語系化字串。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|此清單控制項一律包含在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的內容檢視。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|此清單控制項一律包含在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|如果此容器可以接受鍵盤輸入，則此屬性值應為 true。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|請參閱備註。|清單控制項的說明文字應解釋為什麼會要求使用者從清單選擇選項。 例如，「從此清單選取項目將會設定顯示器的解析度。」|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>必要的使用者介面自動化控制項模式和屬性  
 下表列出清單控制項支援所需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項模式。 如需控制項模式的詳細資訊，請參閱 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)。  
  
|控制項模式/模式屬性|支援/值|注意|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|必要|當控制項所包含的項目維持為選取狀態時，支援清單控制項類型的所有控制項都必須實作 `ISelectionProvider` 。 如果容器內的項目不能選取，則必須使用群組控制項類型。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|視情況而定|清單控制項不一定需要選取某個項目。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|視情況而定|清單控制項可以是單一或多重選擇容器。|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|視情況而定|如果容器中的項目是可以捲動的，即實作此控制項模式。|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|視情況而定|當需要使用方格逐一巡覽項目時，即實作此模式。|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|視情況而定|如果控制項支援容器中項目的多重檢視，即實作此控制項模式。|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|永不|清單控制項類型並不支援`ITableProvider` 。 如果控制項需要支援此控制項模式，則控制項應為資料方格控制項類型。|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>必要的使用者介面自動化事件  
 下表列出所有清單控制項支援所需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。 如需事件的詳細資訊，請參閱 [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件|支援/值|注意|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|視情況而定|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|視情況而定|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要|無|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Automation.ControlType.List>  
 [UI 自動化控制項類型概觀](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI 自動化概觀](../../../docs/framework/ui-automation/ui-automation-overview.md)
