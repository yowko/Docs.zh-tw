---
title: "UI Automation Control Types Overview | Microsoft Docs"
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
  - "UI Automation, control types"
  - "control types, UI Automation"
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
caps.latest.revision: 22
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 22
---
# UI Automation Control Types Overview
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 控制項類型是已知的識別項，可以用來指出特定項目代表哪種控制項，例如下拉式方塊或按鈕。  
  
 有了已知的識別項，可讓輔助技術裝置更容易判斷哪些類型的控制項可在 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 使用，以及如何與控制項互動。  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## UI 自動化控制項類型必要條件  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 控制項類型提供一組提供者必須符合的條件。 一旦符合這些條件，控制項就可以使用特定的控制項類型名稱。 每個控制項類型都具有下列條件：  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制模式—必須支援哪些控制項模式、哪些控制項模式是選用項目，以及控制項不必須支援哪些控制項模式。  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性值—支援哪些屬性值。  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構—控制項的必要 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構。  
  
 當控制項符合特定控制項類型的條件時，<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> 屬性值會指出該控制項類型。  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## 目前 UI 自動化控制項類型  
 下列清單包含目前的一組 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 控制項類型：  
  
-   [UI Automation Support for the Button Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [UI Automation Support for the Calendar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [UI Automation Support for the CheckBox Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [UI Automation Support for the ComboBox Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [UI Automation Support for the DataGrid Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [UI Automation Support for the DataItem Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [UI Automation Support for the Document Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [UI Automation Support for the Edit Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [UI Automation Support for the Group Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [UI Automation Support for the Header Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [UI Automation Support for the HeaderItem Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [UI Automation Support for the Hyperlink Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [UI Automation Support for the Image Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [UI Automation Support for the List Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [UI Automation Support for the ListItem Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [UI Automation Support for the Menu Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [UI Automation Support for the MenuBar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [UI Automation Support for the MenuItem Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [UI Automation Support for the Pane Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [UI Automation Support for the ProgressBar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [UI Automation Support for the RadioButton Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [UI Automation Support for the ScrollBar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [UI Automation Support for the Separator Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [UI Automation Support for the Slider Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [UI Automation Support for the Spinner Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [UI Automation Support for the SplitButton Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [UI Automation Support for the StatusBar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [UI Automation Support for the Tab Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [UI Automation Support for the TabItem Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [UI Automation Support for the Table Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [UI Automation Support for the Text Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [UI Automation Support for the Thumb Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [UI Automation Support for the TitleBar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [UI Automation Support for the ToolBar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [UI Automation Support for the ToolTip Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [UI Automation Support for the Tree Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [UI Automation Support for the TreeItem Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [UI Automation Support for the Window Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## 請參閱  
 <xref:System.Windows.Automation.ControlType>