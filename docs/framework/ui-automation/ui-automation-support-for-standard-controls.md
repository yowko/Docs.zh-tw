---
title: "UI Automation Support for Standard Controls | Microsoft Docs"
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
  - "controls, UI Automation support for"
  - "UI Automation, support for standard controls"
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
caps.latest.revision: 11
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 10
---
# UI Automation Support for Standard Controls
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的最新資訊，請參閱 [Windows Automation API：UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題將說明針對 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]、[!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] 架構所開發的應用程式中，其標準控制項的 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 支援。  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## Windows Presentation Foundation 控制項  
 提供資訊或支援使用者互動的所有 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項項目，都有 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的完整原生支援。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 看不見其他如面板等的項目。  
  
<a name="Win32_Controls"></a>   
## Win32 控制項  
 大多數 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 控制項都是透過 UIAutomationClientsideProviders.dll 中的用戶端提供者公開至 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]。 此組件會自動註冊為用於使用者介面自動化用戶端應用程式。  
  
 完整支援只提供給 ComCtrl32.dll 第 6 版 \(隨附於 [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] \(含\) 以後的版本\) 以後的控制項。  
  
 支援的控制項如下。  
  
|類別名稱|控制項類型|  
|----------|-----------|  
|按鈕|按鈕|  
|按鈕|RadioButton|  
|按鈕|群組|  
|按鈕|核取方塊|  
|按鈕|超連結|  
|按鈕|SplitButton|  
|按鈕|核取方塊|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Edit|文件|  
|Edit|Edit|  
|SysLink|超連結|  
|Static|Text|  
|Static|Image|  
|SysIPAddress32|自訂|  
|SysHeader32|Header\/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|清單|  
|ListBox|清單|  
|ListBox|ListItem|  
|\#32768|功能表|  
|\#32768|MenuItem|  
|msctls\_progress32|進度列|  
|RichEdit|Document. 請參閱「注意」。|  
|RichEdit20A|文件|  
|RichEdit20W|文件|  
|RichEdit50W|文件|  
|ScrollBar|滑桿|  
|msctls\_trackbar32|滑桿|  
|msctls\_updown32|Spinner|  
|msctls\_statusbar32|StatusBar|  
|SysTabControl32|索引標籤|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|MenuItem|  
|ToolbarWindow32|按鈕|  
|ToolbarWindow32|核取方塊|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Separator|  
|tooltips\_class32|ToolTip|  
|\#32774|ToolTip|  
|ReBarWindow32|工具列|  
|SysTreeView32|樹狀結構|  
|SysTreeView32|TreeItem|  
  
 **注意** 只有隨附於 [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] 的版本 \(在 RichEd20.dll 3.1 版 \(含\) 以後版本以及 MsftEdit.dll 4.1 版 \(含\) 以後版本\) 才支援 RichEdit 控制項。  
  
 不支援的控制項如下。  
  
|類別名稱|控制項類型|  
|----------|-----------|  
|SysAnimate32|Image|  
|SysPager|Spinner|  
|SysDateTimePick32|自訂|  
|SysMonthCal32|行事曆|  
|MS\_WINNOTE|工具提示|  
|VBBubble|工具提示|  
|ScrollBar \(當做獨立控制項使用時\)|滑桿|  
|SuperGrid|自訂|  
  
<a name="Windows_Forms_Controls"></a>   
## Windows Form 控制項  
 [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] 控制項是透過 UIAutomationClientsideProviders.dll 中的用戶端提供者公開至 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]。 此組件會自動註冊為用於使用者介面自動化用戶端應用程式。  
  
 一般來說，[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 支援 [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] 控制項 \(即 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 通用控制項的 Managed 包裝函式\)。 支援的控制項如下。  
  
|類別名稱|  
|----------|  
|按鈕|  
|核取方塊|  
|CheckedListBox|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FontDialog|  
|GroupBox|  
|HscrollBar|  
|ImageList|  
|標籤|  
|ListBox|  
|ListView|  
|MainMenu\/ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog|  
|PrintDialog|  
|進度列|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabControl\/TabPage|  
|TextBox|  
|計時器|  
|工具列|  
|ToolTip|  
|TrackBar|  
|TreeView|  
|VscrollBar|  
|Web 瀏覽器|  
  
 下列控制項只透過其 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] 支援公開至 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]。 部分功能可能無法使用。  
  
|控制項名稱|  
|-----------|  
|BindingSource|  
|DataGrid|  
|DataGridView|  
|DataNavigator|  
|DomainUpDown|  
|ErrorProvider|  
|FlowLayoutPanel|  
|表單|  
|LinkLabel|  
|HelpProvider|  
|MaskedTextBox|  
|MenuStrip\/ContextMenuStrip|  
|NumericUpDown|  
|面板|  
|PictureBox|  
|PrintDocument|  
|PrintPreview\-Control|  
|PrintPreview\-Dialog|  
|PropertyGrid|  
|UserControl|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer\/SplitterPanel|  
|Splitter|  
|RaftingContainer|  
|StatusStrip|  
  
## 請參閱  
 [UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)