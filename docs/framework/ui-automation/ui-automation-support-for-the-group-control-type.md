---
title: Group 控制項類型的 UI 自動化支援
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Group control type
- Group control type
- control types, Group
ms.assetid: 18e01bab-01f8-4567-b867-88dce9c4a435
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: a5bc202c0297eb3f0d4f6fa06b3beca0f9112272
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875315"
---
# <a name="ui-automation-support-for-the-group-control-type"></a>Group 控制項類型的 UI 自動化支援
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題提供群組控制項類型的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 支援相關資訊。 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中，控制項類型是一組控制項條件，控制項必須符合條件才能使用 <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> 屬性。 這些條件包括 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的特定方針、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性值和 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項模式。  
  
 群組控制項代表階層內的節點。 群組控制項類型會在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構中建立分隔界限，讓組成群組的項目在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構內以邏輯方式區分開來。  
  
 下列章節會定義群組控制項類型所需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、屬性、控制項模式和事件。 無論是 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]或 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]， [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]需求都適用於所有群組控制項。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>必要的使用者介面自動化樹狀結構  
 下表描述群組控制項之 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀的控制項檢視和內容檢視，並說明各檢視中可包含的內容。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的詳細資訊，請參閱 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)。  
  
|控制項檢視|內容檢視|  
|------------------|------------------|  
|群組<br /><br /> -0 或多個控制項|群組<br /><br /> -0 或多個控制項|  
  
 群組控制項通常會有[ListItem 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)， [TreeItem 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)，或[的 UI 自動化支援DataItem 控制項類型](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)控制項下樹狀子目錄中找到的類型。 由於 'Group' 是泛型容器，因此群組控制項底下的樹狀結構中可有任何類型的控制項。  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必要的使用者介面自動化屬性  
 下表列示 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性，其值或定義與群組控制項特別有關。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性的詳細資訊，請參閱 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性|值|注意|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|請參閱備註。|此屬性的值在應用程式中的所有控制項都不得重複。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|請參閱備註。|包含整個控制項的最外層矩形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|請參閱備註。|如果有週框即受支援。 如果週框中沒有任何可點選的點，而且您執行的是特殊化點擊測試，則會覆寫並提供可點選的點。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|請參閱備註。|如果控制項可接收鍵盤焦點，就必定支援此屬性。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|請參閱備註。|群組控制項通常會從控制項的標籤文字取得名稱。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|請參閱備註。|群組控制項通常會自行設定標籤。 在這些情況下，會在此傳回 `null` 。 如果群組沒有靜態文字標籤，則必須以 LabeledBy 屬性值傳回。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|群組|此值與所有使用者介面架構的值相同。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|「群組」|對應到群組控制項類型的當地語系化字串。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|此群組控制項一律包含在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的內容檢視。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|此群組控制項一律包含在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>必要的使用者介面自動化控制項模式  
 下表列出群組控制項類型支援所需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項模式。 如需控制項模式的詳細資訊，請參閱 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)。  
  
|控制項模式|支援|注意|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|視情況而定|可用來顯示或隱藏資訊的群組控制項必須支援展開摺疊模式。|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>必要的使用者介面自動化事件  
 下表列出所有群組控制項都必須支援的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。 如需事件的詳細資訊，請參閱 [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件|支援|注意|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要|無|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Automation.ControlType.Group>  
 [UI 自動化控制項類型概觀](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI 自動化概觀](../../../docs/framework/ui-automation/ui-automation-overview.md)
