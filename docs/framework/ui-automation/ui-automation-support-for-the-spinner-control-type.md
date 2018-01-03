---
title: "Spinner 控制項類型的 UI 自動化支援"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Spinner control type
- Spinner control type
- control types, Spinner
ms.assetid: 3a29d185-65d8-42e3-bcc3-7f43e96f40c5
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8a5c5fda5b3f29e8c91290e7dcb3de0635ee94b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-spinner-control-type"></a>Spinner 控制項類型的 UI 自動化支援
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題提供微調按鈕控制項類型的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 支援相關資訊。 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中，控制項類型是一組控制項條件，控制項必須符合條件才能使用 <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> 屬性。 這些條件包括 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性值和控制項模式的特定方針。  
  
 微調控制項可用來選取某個範圍的項目或數字。  
  
 下列章節會定義微調控制項類型所需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、屬性、控制項模式和事件。 無論是 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]或 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]， [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]需求都適用於所有微調控制項。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>必要的使用者介面自動化樹狀結構  
 下表說明微調控制項支援範圍值、值和選取控制項模式時之相關 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視和內容檢視，並說明每個檢視可以包含的內容。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的詳細資訊，請參閱 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)。  
  
 **範圍值或值控制項模式**  
  
|控制項檢視|內容檢視|  
|------------------|------------------|  
|Spinner<br /><br /> 編輯 （0 或 1）<br />按鈕 (2)|Spinner|  
  
 **Selection 控制項模式**  
  
|控制項檢視|內容檢視|  
|------------------|------------------|  
|Spinner<br /><br /> 編輯 （0 或 1）<br />按鈕 (2)<br />清單項目 （0 個以上）|Spinner<br /><br /> -ListItem （0 個以上）|  
  
 為確保自動化測試工具可區別控制項檢視樹狀子結構中的兩個按鈕，請依適當的情況指派 `SmallIncrement` 或 `SmallDecrement``AutomationId` 。 針對某些實作，相關的編輯控制項可以是微調控制項的對等項目。  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必要的使用者介面自動化屬性  
 下表列出 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性，其值或定義與微調控制項特別有關。 如需有關[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]屬性，請參閱[用戶端的使用者介面自動化屬性](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性|值|備註|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|請參閱備註。|此屬性的值在應用程式中的所有控制項都不得重複。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|請參閱備註。|包含整個控制項的最外層矩形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|請參閱備註。|微調控制項可點選的點會將焦點置於控制項的編輯部分。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|請參閱備註。|如果控制項可接收鍵盤焦點，就必定支援此屬性。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|請參閱備註。|微調控制項的名稱通常來自靜態文字標籤。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|請參閱備註。|微調控制項有靜態文字標籤。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Spinner|此值與所有使用者介面架構的值相同。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|「微調」|對應到微調控制項類型的當地語系化字串。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|微調控制項必須一律為內容。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|微調控制項必須一律為控制項。|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>必要的使用者介面自動化控制項模式和屬性  
 下表列出微調控制項必須支援的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項模式。 如需控制項模式的詳細資訊，請參閱 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)。  
  
|控制項模式/模式屬性|支援/值|備註|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|視情況而定|若微調控制項有可供選取的項目清單，則必須支援此模式。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|False|微調控制項一律是單一選擇容器。|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|視情況而定|跨數值範圍的微調控制項可支援此模式。|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|視情況而定|跨一組不連續選項或數字的微調控制項可支援此模式。|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>必要的使用者介面自動化事件  
 下表列出所有微調控制項都必須支援的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。 如需事件的詳細資訊，請參閱 [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件|支援|備註|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|視情況而定|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要項|無|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Automation.ControlType.Spinner>  
 [UI 自動化控制項類型概觀](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI 自動化概觀](../../../docs/framework/ui-automation/ui-automation-overview.md)
