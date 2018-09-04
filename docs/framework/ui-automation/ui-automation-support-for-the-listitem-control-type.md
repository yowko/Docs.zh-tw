---
title: ListItem 控制項類型的 UI 自動化支援
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 69fe598fc38d9a82d0b95318774d16a49bbdf49f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499311"
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>ListItem 控制項類型的 UI 自動化支援
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題提供 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項類型的 <xref:System.Windows.Automation.ControlType.ListItem> 支援相關資訊。 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中，控制項類型是一組控制項條件，控制項必須符合條件才能使用 <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> 屬性。 這些條件包括 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性值和控制項模式的特定方針。  
  
 清單項目控制項是實作清單項目控制項類型的控制項範例。  
  
 下列章節會定義清單項目控制項類型所需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、屬性、控制項模式和事件。 無論是 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]或 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]， [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]需求都適用於所有清單控制項。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>必要的使用者介面自動化樹狀結構  
 下表描述與清單項目控制項相關之 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視和內容檢視，並說明各檢視中可包含的內容。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的詳細資訊，請參閱 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)。  
  
|控制項檢視|內容檢視|  
|------------------|------------------|  
|ListItem<br /><br /> -映像 （0 或以上）<br />文字 （0 或以上）<br />編輯 （0 或以上）|ListItem|  
  
 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的內容檢視中，清單項目控制項的子系必須一律為 "0"。 如果控制項結構，其他項目都包含底下的清單項目，則其應遵循的需求[TreeItem 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)控制項類型。  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必要的使用者介面自動化屬性  
 下表列出 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性，其值或定義與清單項目控制項特別有關。 如需詳細資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]屬性，請參閱[UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性|值|注意|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|請參閱備註。|此屬性的值在應用程式中的所有控制項都不得重複。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|請參閱備註。|這個屬性的值應包含清單項目的影像區域和文字內容。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|視情況而定|如果清單控制項有可點選的點 (可以按一下讓清單取得焦點的點)，則該點必須透過此屬性公開。 如果清單控制項被子代清單項目完全覆蓋，則會引發 <xref:System.Windows.Automation.NoClickablePointException> ，表示用戶端必須從清單控制項內的項目查詢是否有可點選的點。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|請參閱備註。|清單項目控制項的名稱屬性值取自於項目的文字內容。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|請參閱備註。|如果有靜態文字標籤，那麼這個屬性必須公開該控制項的參考。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ListItem|此值與所有使用者介面架構的值相同。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|「清單項目」|對應到清單項目控制項類型的當地語系化字串。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|此清單控制項一律包含在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的內容檢視。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|此清單控制項一律包含在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|如果此容器可以接受鍵盤輸入，則此屬性值應為 true。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|清單控制項的說明文字應解釋，為什麼會要求使用者從選項清單中選擇選項，而這通常也是透過工具提示顯示的資訊類型。 例如，「選取項目以設定顯示器的解析度。」|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|視情況而定|表示基礎物件的清單項目控制項應公開此屬性。 這些清單項目控制項通常會有相關聯的圖示，可讓使用者將控制項與基礎物件建立關聯。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|視情況而定|此屬性必須傳回值，表示清單項目目前是否捲動到實作捲動控制項模式之父容器的檢視範圍內。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>必要的使用者介面自動化控制項模式  
 下表列出清單項目控制項必須支援的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項模式。 如需控制項模式的詳細資訊，請參閱 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)。  
  
|控制項模式|支援|注意|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|是|清單項目控制項必須實作此控制項模式。 這可讓清單項目控制項傳遞已選取的訊息。|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|視情況而定|如果清單項目位於可捲動的容器內，則必須實作此控制項模式。|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|視情況而定|如果清單項目是可以核取的，而且動作不會變更選取狀態，則必須實作此控制項模式。|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|視情況而定|如果可以操作項目隱藏或顯示資訊，則必須實作此控制項模式。|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|視情況而定|如果項目可以編輯，則必須實作此控制項模式。 變更清單項目控制項時， <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>和 <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>的值也會跟著變更。|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|視情況而定|如果支援在清單容器內進行逐項空間巡覽，而且容器是以資料列和資料行的方式排列，則必須實作方格項目控制項模式。|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|視情況而定|如果項目有可以對其執行的命令 (選取除外)，則必須實作此模式。 這通常是與按兩下清單項目控制項相關聯的動作。 例如，從 [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)]開啟文件，或在 [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)]中播放音樂檔案。|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>必要的使用者介面自動化事件  
 下表列出所有清單項目控制項都必須支援的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。 如需事件的詳細資訊，請參閱 [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件|支援|注意|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|視情況而定|無|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|必要|無|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|必要|無|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要|無|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Automation.ControlType.ListItem>  
 [UI 自動化控制項類型概觀](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI 自動化概觀](../../../docs/framework/ui-automation/ui-automation-overview.md)
