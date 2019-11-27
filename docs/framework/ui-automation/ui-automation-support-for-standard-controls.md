---
title: 標準控制項的 UI 自動化支援
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: c59352f908c5f4a1fd2ca6dd631d26bb5d69f09a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441219"
---
# <a name="ui-automation-support-for-standard-controls"></a>標準控制項的 UI 自動化支援
> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題將說明針對 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 、 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]和 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]架構所開發的應用程式中，其標準控制項的 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] 支援。  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Windows Presentation Foundation 控制項  
 提供資訊或支援使用者互動的所有 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項項目，都有 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的完整原生支援。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]看不見其他如面板等的項目。  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Win32 控制項  
 大多數 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 控制項都是透過 UIAutomationClientsideProviders.dll 中的用戶端提供者公開至 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 。 此組件會自動註冊為用於使用者介面自動化用戶端應用程式。  
  
 完整支援只提供給 ComCtrl32.dll 第 6 版 (隨附於 [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] (含) 以後的版本) 以後的控制項。  
  
 支援的控制項如下。  
  
|類別名稱|控制項類型|  
|----------------|------------------|  
|按鈕|按鈕|  
|按鈕|RadioButton|  
|按鈕|群組|  
|按鈕|核取方塊|  
|按鈕|超連結|  
|按鈕|SplitButton|  
|按鈕|核取方塊|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|編輯|文件|  
|編輯|編輯|  
|SysLink|超連結|  
|靜態|Text|  
|靜態|影像|  
|SysIPAddress32|自訂|  
|SysHeader32|Header/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|清單|  
|ListBox|清單|  
|ListBox|ListItem|  
|#32768|功能表|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|文件。 請參閱「注意」。|  
|RichEdit20A|文件|  
|RichEdit20W|文件|  
|RichEdit50W|文件|  
|ScrollBar|滑桿|  
|msctls_trackbar32|滑桿|  
|msctls_updown32|Spinner|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|索引標籤|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|MenuItem|  
|ToolbarWindow32|按鈕|  
|ToolbarWindow32|核取方塊|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|分隔符號|  
|tooltips_class32|ToolTip|  
|#32774|ToolTip|  
|ReBarWindow32|ToolBar|  
|SysTreeView32|樹狀結構|  
|SysTreeView32|TreeItem|  
  
 **注意**RichEdit 控制項僅支援 Windows Vista 隨附的版本（在 Riched20.dll 版本3.1 和更新版本中，以及 4.1 Msftedit.dll 和更新版本）。  
  
 不支援的控制項如下。  
  
|類別名稱|控制項類型|  
|----------------|------------------|  
|SysAnimate32|影像|  
|SysPager|Spinner|  
|SysDateTimePick32|自訂|  
|SysMonthCal32|行事曆|  
|MS_WINNOTE|工具提示|  
|VBBubble|工具提示|  
|ScrollBar (當做獨立控制項使用時)|滑桿|  
|SuperGrid|自訂|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Windows Form 控制項  
 Windows Forms 控制項會透過 Uiautomationclientsideproviders.dll 中的用戶端提供者公開給 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]。 此組件會自動註冊為用於使用者介面自動化用戶端應用程式。  
  
 一般來說，[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]支援 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 通用控制項的 managed 包裝函式 Windows Forms 控制項。 支援的控制項如下。  
  
|類別名稱|  
|----------------|  
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
|MainMenu/ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabControl/TabPage|  
|TextBox|  
|計時器|  
|ToolBar|  
|ToolTip|  
|TrackBar|  
|TreeView|  
|VscrollBar|  
|Web 瀏覽器|  
  
 下列控制項只會透過 Microsoft Active Accessibility 的支援來公開 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]。 部分功能可能無法使用。  
  
|控制項名稱|  
|------------------|  
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
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|面板|  
|PictureBox|  
|PrintDocument|  
|PrintPreview-Control|  
|PrintPreview-Dialog|  
|PropertyGrid|  
|UserControl|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|分隔器|  
|RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>另請參閱

- [UI Automation Control Types](ui-automation-control-types.md)
