---
title: UI 自動化控制項類型概觀
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 5274a2a090669a9c51c5247b68d2b0460625a494
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911564"
---
# <a name="ui-automation-control-types-overview"></a>UI 自動化控制項類型概觀
> [!NOTE]
> 這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 控制項類型是已知的識別項，可以用來指出特定項目代表哪種控制項，例如下拉式方塊或按鈕。  
  
 有了已知的識別項，可讓輔助技術裝置更容易判斷哪些類型的控制項可在 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 使用，以及如何與控制項互動。  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>UI 自動化控制項類型必要條件  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 控制項類型提供一組提供者必須符合的條件。 一旦符合這些條件，控制項就可以使用特定的控制項類型名稱。 每個控制項類型都具有下列條件：  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制模式—必須支援哪些控制項模式、哪些控制項模式是選用項目，以及控制項不必須支援哪些控制項模式。  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性值—支援哪些屬性值。  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構—控制項的必要 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構。  
  
 當控制項符合特定控制項類型的條件時， <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> 屬性值會指出該控制項類型。  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>目前 UI 自動化控制項類型  
 下列清單包含目前的一組 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 控制項類型：  
  
- [Button 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
- [Calendar 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
- [CheckBox 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
- [ComboBox 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
- [DataGrid 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
- [DataItem 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
- [Document 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
- [Edit 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
- [Group 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
- [Header 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
- [HeaderItem 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
- [Hyperlink 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [Image 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
- [List 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
- [ListItem 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
- [Menu 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
- [MenuBar 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
- [MenuItem 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
- [Pane 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
- [ProgressBar 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
- [RadioButton 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [ScrollBar 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [Separator 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
- [Slider 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
- [Spinner 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
- [SplitButton 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [StatusBar 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
- [Tab 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
- [TabItem 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
- [Table 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
- [Text 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
- [Thumb 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
- [TitleBar 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
- [ToolBar 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
- [ToolTip 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
- [Tree 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
- [TreeItem 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
- [Window 控制項類型的 UI 自動化支援](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Automation.ControlType>
