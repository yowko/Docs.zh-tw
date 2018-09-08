---
title: ToolTip 控制項類型的 UI 自動化支援
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ToolTip control type
- ToolTip control type
- control types, ToolTip
ms.assetid: c3779d78-3164-43ae-8dae-bfaeafffdd65
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 7d089cf01f3cee0cac40c258e48de5e9f5f95df7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180257"
---
# <a name="ui-automation-support-for-the-tooltip-control-type"></a>ToolTip 控制項類型的 UI 自動化支援
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題提供工具提示控制項類型的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 支援相關資訊。 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中，控制項類型是一組控制項條件，控制項必須符合條件才能使用 <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> 屬性。 這些條件包括 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性值和控制項模式的特定方針。  
  
 工具提示控制項是包含文字的快顯視窗。  
  
 下列章節會定義工具提示控制項類型所需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、屬性、控制項模式和事件。 無論是 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]或 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]， [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]需求都適用於所有工具提示控制項。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>必要的使用者介面自動化樹狀結構  
 下表描述工具提示控制項之 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視和內容檢視，並說明各檢視中可包含的內容。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的詳細資訊，請參閱 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)。  
  
|控制項檢視|內容檢視|  
|------------------|------------------|  
|ToolTip<br /><br /> 文字 （0 或以上）<br />-映像 （0 或以上）|ToolTip|  
  
 如果工具提示控制項可以接收鍵盤焦點，便只會出現在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的內容檢視。 否則，所有的工具提示資訊都可由其參考之 `HelpTextProperty` 項目上的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 取得。  
  
 工具提示應該會顯示於其資訊所參考的控制項下方。 用戶端必須接聽 `ToolTipOpenedEvent` 以確保它們持續取得工具提示中包含的資訊。  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必要的使用者介面自動化屬性  
 下表列示 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性，其值或定義與工具提示控制項特別有關。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性的詳細資訊，請參閱 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性|值|注意|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|請參閱備註。|此屬性的值在應用程式中的所有控制項都不得重複。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|請參閱備註。|包含整個控制項的最外層矩形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|請參閱備註。|可點選的點應該也是關閉該控制項之工具提示的一部分。 有些工具提示並沒有這項功能，因而不會有可點選的點。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|請參閱備註。|如果控制項可接收鍵盤焦點，就必定支援此屬性。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|請參閱備註。|工具提示控制項的名稱為顯示在該工具提示內的文字。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|工具提示控制項一律會由其內容自我標示。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ToolTip|此值與所有使用者介面架構的值相同。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|「工具提示」|對應到工具提示控制項類型的當地語系化字串。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|視情況而定|如果工具提示控制項可以接收鍵盤焦點，則它必須位於該樹狀結構的內容檢視中。 如果該工具提示僅限文字，則它就和引發它的控制項中的 HelpTextProperty 一樣可用。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|此工具提示控制項必須一律為控制項。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>必要的使用者介面自動化控制項模式  
 下表列示工具提示控制項必須支援的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項模式。 如需控制項模式的詳細資訊，請參閱 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)。  
  
|控制項模式|支援|注意|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|視情況而定|可以按一下 UI 項目來關閉的工具提示，必須支援 WindowPattern，以便它們可以自動關閉。|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|視情況而定|為了提供更優質的協助，工具提示控制項可以支援文字控制項模式，雖然這並非必要。 當文字有豐富的樣式和屬性 (例如色彩、粗體和斜體) 時，這種文字控制項模式相當有用。|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>必要的使用者介面自動化事件  
 當工具提示控制項出現在畫面時，必須引發 `ToolTipOpenedEvent` 。 此事件會包含參考工具提示本身的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 項目。  
  
 下表列示所有工具提示控制項都必須支援的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。 如需事件的詳細資訊，請參閱 [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件|支援|注意|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|視情況而定|無|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|視情況而定|無|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|視情況而定|無|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|視情況而定|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent>|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent>|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要|無|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Automation.ControlType.ToolTip>  
 [UI 自動化控制項類型概觀](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI 自動化概觀](../../../docs/framework/ui-automation/ui-automation-overview.md)
