---
title: Menu 控制項類型的 UI 自動化支援
description: 取得功能表控制項類型消費者介面自動化支援的相關資訊。 瞭解所需的樹狀結構、屬性、控制項模式和事件。
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu
- UI Automation, Menu control type
- Menu control type
ms.assetid: 016323cb-f800-4938-b77b-2eb25d646090
ms.openlocfilehash: eb5521ce07e903a1f8fc4144f76dbe3f135066a0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96282986"
---
# <a name="ui-automation-support-for-the-menu-control-type"></a>Menu 控制項類型的 UI 自動化支援

> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題提供功能表控制項類型的 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 支援相關資訊。 其中說明控制項的 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 樹狀結構，並提供特定控制項案例的屬性和控制項模式。  
  
 功能表控制項可將命令和事件處理常式的關聯項目以階層方式組織。 在一般的 Microsoft Windows 應用程式中，功能表列會包含數個功能表按鈕 **(例如 [** 檔案]、[ **編輯**] 和 [ **視窗]**) ，而且每個功能表按鈕都會顯示功能表。 功能表又包含一組功能表項目 (例如 [開新檔案] **F:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty**、[開啟舊檔] **UI Automation Properties Overview** 和 [關閉檔案] **TLA#tla_win32**)，這些項目可展開顯示更多的功能表項目，或在按一下時可執行特定的動作。  
  
 下列章節會定義功能表控制項類型所需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、屬性、控制項模式和事件。 這些 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 需求適用于所有清單控制項，不論是 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 、Win32 或 Windows Forms。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>必要的使用者介面自動化樹狀結構  

 下表描述功能表控制項之 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視和內容檢視，並說明各檢視中可包含的內容。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的詳細資訊，請參閱 [UI Automation Tree Overview](ui-automation-tree-overview.md)。  
  
|控制項檢視|內容檢視|  
|------------------|------------------|  
|功能表<br /><br /> -MenuItem (1 或多個) |不適用 (除非功能表控制項為非功能表項目之物件父系的內容功能表)<br /><br /> -MenuItem (1 或多個) |  
  
 功能表控制項一律會出現在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視和內容檢視。 功能表控制項類別應該顯示於其資訊所參考的控制項下方。 使用者介面自動化用戶端必須接聽 `MenuOpenedEvent` ，以確保它們持續取得功能表控制項所傳達的資訊。 內容功能表控制項是特殊案例。 它們會顯示為桌面的子系。  
  
<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>必要的使用者介面自動化屬性  

 下表列出 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性，其值或定義與功能表控制項類型特別有關。 如需屬性的詳細資訊 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ，請參閱 [用戶端的消費者介面自動化屬性](ui-automation-properties-for-clients.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性|值|備忘錄|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|不支援|功能表控制項不需要設定 Name 屬性。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|典型的功能表控制項不預期有標籤。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|功能表|此值與所有使用者介面架構的值相同。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|此功能表控制項不會包含在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的內容檢視中。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|此功能表控制項一律包含在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視中。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns"></a>必要的使用者介面自動化控制項模式  

 功能表控制項類型沒有必要的控制項模式。  
  
<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>必要的使用者介面自動化事件  

 當功能表控制項出現在畫面時，必須引發 `MenuOpenedEvent` 。 `MenuOpenedEvent` 將包含控制項的文字。 當功能表從畫面消失時，必須引發 `MenuClosedEvent` 。  
  
 下表列出所有功能表控制項都必須支援的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。 如需 [UI Automation Events Overview](ui-automation-events-overview.md)事件的詳細資訊，請參閱  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件|支援/值|備註|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent>|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent>|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 屬性變更事件。|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 屬性變更事件。|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性變更事件。|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要|無|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Automation.ControlType.Menu>
- [UI 自動化控制項模式概觀](ui-automation-control-patterns-overview.md)
- [UI 自動化控制項類型概觀](ui-automation-control-types-overview.md)
- [UI 自動化概觀](ui-automation-overview.md)
