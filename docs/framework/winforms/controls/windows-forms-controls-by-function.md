---
title: "依功能區分 Windows Form 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "控制項 [Windows Form], 以函式"
  - "Windows Form 控制項, 清單"
  - "Windows Form, 依功能的控制項"
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 依功能區分 Windows Form 控制項
Windows Form 提供執行一些功能的控制項和元件。  下表根據一般功能，列出 Windows Form 控制項和元件。  此外，當有多個控制項提供相同的功能時，會列出建議使用的控制項以及一個關於其所取代的控制項的注意事項。  在後續的另一個表格中，所取代的控制項會和它們的建議取代項目一起列出。  
  
> [!NOTE]
>  下表不會列出可以在 Windows Form 中使用的每一個控制項或元件；如需更完整的清單，請參閱[在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)。  
  
## 依功能區分建議使用的控制項和元件  
  
|Function|控制項|描述|  
|--------------|---------|--------|  
|資料顯示|<xref:System.Windows.Forms.DataGridView> 控制項|<xref:System.Windows.Forms.DataGridView> 控制項提供一個可自訂的資料表來顯示資料。  <xref:System.Windows.Forms.DataGridView> 類別會啟用儲存格、資料列、資料行和框線的自訂。 **Note:**  <xref:System.Windows.Forms.DataGridView> 控制項提供許多在 <xref:System.Windows.Forms.DataGrid> 控制項中所沒有的基本及進階的功能。  如需詳細資訊，請參閱[Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。|  
|資料繫結和巡覽|<xref:System.Windows.Forms.BindingSource> 元件|提供貨幣管理、變更告知和其他服務，簡化將表單上的控制項繫結至資料的過程。|  
||<xref:System.Windows.Forms.BindingNavigator> 控制項|提供工具列類型的介面，以在表單上巡覽和操作資料。|  
|文字編輯|<xref:System.Windows.Forms.TextBox> 控制項|顯示在設計階段輸入且可由使用者在執行階段時編輯或以程式設計方式來變更的文字。|  
||<xref:System.Windows.Forms.RichTextBox> 控制項|讓文字以純文字或 RTF 格式顯示。|  
||<xref:System.Windows.Forms.MaskedTextBox> 控制項|限制使用者輸入的格式|  
|資訊顯示 \(唯讀\)|<xref:System.Windows.Forms.Label> 控制項|顯示使用者無法直接編輯的文字。|  
||<xref:System.Windows.Forms.LinkLabel> 控制項|將文字顯示為 Web 樣式連結並在使用者按一下特殊文字時觸發 \(Trigger\) 事件。  此文字通常是到另一個視窗或網站的連結。|  
||<xref:System.Windows.Forms.StatusStrip> 控制項|使用框架區域 \(通常出現在父表單底部\) 來顯示應用程式目前狀態的資訊。|  
||<xref:System.Windows.Forms.ProgressBar> 控制項|顯示作業的目前進度給使用者。|  
|Web 網頁顯示|<xref:System.Windows.Forms.WebBrowser> 控制項|讓使用者可以在表單中巡覽 Web 網頁。|  
|從清單選取|<xref:System.Windows.Forms.CheckedListBox> 控制項|顯示可捲動的項目清單，每個項目旁都有核取方塊。|  
||<xref:System.Windows.Forms.ComboBox> 控制項|顯示項目的下拉式清單。|  
||<xref:System.Windows.Forms.DomainUpDown> 控制項|顯示文字項目的清單，使用者可利用向上和向下按鈕來捲動。|  
||<xref:System.Windows.Forms.ListBox> 控制項|顯示文字和圖形項目 \(圖示\) 的清單。|  
||<xref:System.Windows.Forms.ListView> 控制項|利用四種不同檢視之一來顯示項目。  檢視包括只有文字、具有小圖示的文字、具有大圖示的文字和詳細資料檢視。|  
||<xref:System.Windows.Forms.NumericUpDown> 控制項|顯示數字的清單，使用者可利用向上和向下按鈕來捲動。|  
||<xref:System.Windows.Forms.TreeView> 控制項|顯示節點物件的階層式集合，節點物件可由含有選擇性核取方塊或圖示的文字組成。|  
|圖形顯示|<xref:System.Windows.Forms.PictureBox> 控制項|在框架 \(Frame\) 中顯示圖形檔，例如點陣圖和圖示。|  
|圖形儲存|<xref:System.Windows.Forms.ImageList> 控制項|當作影像的儲存機制。  <xref:System.Windows.Forms.ImageList> 控制項和其包含的影像可以在不同的應用程式中重複使用。|  
|設定值|<xref:System.Windows.Forms.CheckBox> 控制項|顯示文字的核取方塊和標籤，  通常是用來設定選項。|  
||<xref:System.Windows.Forms.CheckedListBox> 控制項|顯示可捲動的項目清單，每個項目旁都有核取方塊。|  
||<xref:System.Windows.Forms.RadioButton> 控制項|顯示可開啟或關閉的按鈕。|  
||<xref:System.Windows.Forms.TrackBar> 控制項|藉由在刻度上前後移動「縮圖」以允許使用者設定刻度值。|  
|日期設定|<xref:System.Windows.Forms.DateTimePicker> 控制項|顯示圖形月曆來讓使用者選取日期或時間。|  
||<xref:System.Windows.Forms.MonthCalendar> 控制項|顯示圖形月曆來讓使用者選取日期範圍。|  
|對話方塊|<xref:System.Windows.Forms.ColorDialog> 控制項|顯示色彩選擇器來讓使用者設定介面項目的色彩。|  
||<xref:System.Windows.Forms.FontDialog> 控制項|顯示對話方塊來讓使用者設定字型及其屬性 \(Attribute\)。|  
||<xref:System.Windows.Forms.OpenFileDialog> 控制項|顯示對話方塊來讓使用者巡覽並選取檔案。|  
||<xref:System.Windows.Forms.PrintDialog> 控制項|顯示對話方塊來讓使用者選取印表機並設定其屬性。|  
||<xref:System.Windows.Forms.PrintPreviewDialog> 控制項|顯示對話方塊來顯示控制項的 <xref:System.Drawing.Printing.PrintDocument> 元件在列印時如何出現。|  
||<xref:System.Windows.Forms.FolderBrowserDialog> 控制項|顯示對話方塊來讓使用者瀏覽、建立和最終選取資料夾。|  
||<xref:System.Windows.Forms.SaveFileDialog> 控制項|顯示對話方塊來讓使用者儲存檔案。|  
|功能表控制項|<xref:System.Windows.Forms.MenuStrip> 控制項|建立自訂功能表。 **Note:**  <xref:System.Windows.Forms.MenuStrip> 是設計來取代 <xref:System.Windows.Forms.MainMenu> 控制項。|  
||<xref:System.Windows.Forms.ContextMenuStrip> 控制項|建立自訂內容功能表。 **Note:**  <xref:System.Windows.Forms.ContextMenuStrip> 是設計來取代 <xref:System.Windows.Forms.ContextMenu> 控制項。|  
|命令|<xref:System.Windows.Forms.Button> 控制項|啟動、停止或插斷處理序。|  
||<xref:System.Windows.Forms.LinkLabel> 控制項|將文字顯示為 Web 樣式連結並在使用者按一下特殊文字時觸發 \(Trigger\) 事件。  此文字通常是到另一個視窗或網站的連結。|  
||<xref:System.Windows.Forms.NotifyIcon> 控制項|在工作列的狀態告知區域中顯示圖示來表示在背景執行的應用程式。|  
||<xref:System.Windows.Forms.ToolStrip> 控制項|建立工具列，它可以具有 Microsoft Windows XP、Microsoft Office、Microsoft Internet Explorer 或自訂的外觀及操作、具有或不具有佈景主題，以及具有溢位和執行階段項目重新調整順序的支援。 **Note:**  <xref:System.Windows.Forms.ToolStrip> 控制項是設計來取代 <xref:System.Windows.Forms.ToolBar> 控制項。|  
|使用者說明|<xref:System.Windows.Forms.HelpProvider> 元件|提供控制項的快顯或線上說明。|  
||<xref:System.Windows.Forms.ToolTip> 元件|提供快顯視窗 \(Pop\-Up Window\)，當使用者將指標放在控制項上時，此視窗會顯示該控制項目的簡短描述。|  
|群組其他控制項|<xref:System.Windows.Forms.Panel> 控制項|將幾個控制項群組在未標記且可捲動的框架上。|  
||<xref:System.Windows.Forms.GroupBox> 控制項|將幾個控制項 \(例如選項按鈕\) 群組在已標記且不可捲動的框架上。|  
||<xref:System.Windows.Forms.TabControl> 控制項|提供索引標籤式頁面來有效地組織和存取群組物件。|  
||<xref:System.Windows.Forms.SplitContainer> 控制項|提供可移動分隔列所區隔的兩個面板。 **Note:**  <xref:System.Windows.Forms.SplitContainer> 控制項是設計來取代 <xref:System.Windows.Forms.Splitter> 控制項。|  
||<xref:System.Windows.Forms.TableLayoutPanel> 控制項|代表會在資料列和資料行所組成的方格中動態配置其內容的面板。|  
||<xref:System.Windows.Forms.FlowLayoutPanel> 控制項|代表會以水平或垂直方式動態配置其內容的面板。|  
|音訊|<xref:System.Media.SoundPlayer> 控制項|播放 .wav 格式的音效檔。  音效可以非同步地載入或播放。|  
  
## 依功能區分所取代的控制項和元件  
  
|Function|所取代的控制項|建議的取代項目|  
|--------------|-------------|-------------|  
|資料顯示|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|資訊顯示 \(唯讀控制項\)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|功能表控制項|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|命令|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|表單配置|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## 請參閱  
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [使用 .NET Framework 開發自訂的 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)