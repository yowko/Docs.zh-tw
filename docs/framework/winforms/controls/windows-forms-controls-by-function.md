---
title: "依功能區分 Windows Form 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c49c42b02511fea66c88544bf689b2b05e788ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-controls-by-function"></a>依功能區分 Windows Form 控制項
Windows Form 提供控制項和元件執行的函式數目。 下表列出 Windows Form 控制項和元件，依據一般函式。 此外，其中有多個控制項提供相同的功能，建議使用的控制項都會列出其所取代的控制項的相關附註。 在後續另一個表格中，已被取代的控制項會列出與其建議的取代項目。  
  
> [!NOTE]
>  下表不會列出每個控制項或元件，您可以使用在 Windows Form。如需更完整清單，請參閱[Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>建議的控制項和元件，由函式  
  
|函式|控制項|描述|  
|--------------|-------------|-----------------|  
|顯示資料|<xref:System.Windows.Forms.DataGridView> 控制項|<xref:System.Windows.Forms.DataGridView>控制項提供可自訂的資料表，以顯示資料。 <xref:System.Windows.Forms.DataGridView>類別可讓您自訂的資料格、 資料列、 資料行和框線。 **注意：** <xref:System.Windows.Forms.DataGridView>控制項提供許多基本和進階功能中遺漏<xref:System.Windows.Forms.DataGrid>控制項。 如需詳細資訊，請參閱[差異之間 Windows Form DataGridView 和 DataGrid 控制項](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|資料繫結和瀏覽|<xref:System.Windows.Forms.BindingSource>元件|藉由提供貨幣管理、 變更通知，以及其他服務，可簡化將控制項繫結至資料的表單上。|  
||<xref:System.Windows.Forms.BindingNavigator> 控制項|提供工具列類型的介面，以巡覽和操作表單上的資料。|  
|編輯文字|<xref:System.Windows.Forms.TextBox> 控制項|顯示在設計階段可由使用者在執行階段、 編輯或以程式設計方式變更輸入的文字。|  
||<xref:System.Windows.Forms.RichTextBox> 控制項|可讓具有純文字或 rtf 格式 (RTF) 格式顯示的文字。|  
||<xref:System.Windows.Forms.MaskedTextBox> 控制項|限制使用者輸入的格式|  
|資訊顯示 （唯讀）|<xref:System.Windows.Forms.Label> 控制項|顯示使用者無法直接編輯的文字。|  
||<xref:System.Windows.Forms.LinkLabel> 控制項|為 Web 樣式連結顯示的文字，並觸發事件，當使用者按一下特殊文字。 文字通常是另一個視窗或網站的連結。|  
||<xref:System.Windows.Forms.StatusStrip> 控制項|顯示使用框架的區域中，通常在父表單底部的應用程式的目前狀態的相關資訊。|  
||<xref:System.Windows.Forms.ProgressBar> 控制項|向使用者顯示目前作業的進度。|  
|網頁上顯示|<xref:System.Windows.Forms.WebBrowser> 控制項|讓使用者巡覽表單中的網頁。|  
|從清單選取項目|<xref:System.Windows.Forms.CheckedListBox> 控制項|顯示的項目，每個旁的核取方塊都可捲動的清單。|  
||<xref:System.Windows.Forms.ComboBox> 控制項|顯示下拉式清單的項目。|  
||<xref:System.Windows.Forms.DomainUpDown> 控制項|顯示使用者可以透過與上下捲動按鈕的文字項目的清單。|  
||<xref:System.Windows.Forms.ListBox> 控制項|顯示文字和圖形化項目 （圖示） 的清單。|  
||<xref:System.Windows.Forms.ListView> 控制項|其中一個四種不同檢視中顯示項目。 檢視包含純文字、 小圖示的文字、 大圖示、 文字和詳細資料檢視。|  
||<xref:System.Windows.Forms.NumericUpDown> 控制項|顯示數字，使用者可以使用向上和向下按鈕來捲動清單。|  
||<xref:System.Windows.Forms.TreeView> 控制項|顯示可以包含文字與選擇性核取方塊或圖示的節點物件的階層式實體集合。|  
|顯示圖形|<xref:System.Windows.Forms.PictureBox> 控制項|顯示圖形化的檔案，例如點陣圖與圖示，在框架中。|  
|圖形的儲存體|<xref:System.Windows.Forms.ImageList> 控制項|做為映像儲存機制。 <xref:System.Windows.Forms.ImageList>從應用程式的下一個可重複使用控制項和它們所包含的映像。|  
|設定值|<xref:System.Windows.Forms.CheckBox> 控制項|顯示核取方塊和標籤的文字。 通常用來設定選項。|  
||<xref:System.Windows.Forms.CheckedListBox> 控制項|顯示的項目，每個旁的核取方塊都可捲動的清單。|  
||<xref:System.Windows.Forms.RadioButton> 控制項|顯示可以開啟或關閉的按鈕。|  
||<xref:System.Windows.Forms.TrackBar> 控制項|可讓使用者透過移動一個 「 捲動方塊 」 沿著標尺，標尺上設定的值。|  
|日期設定|<xref:System.Windows.Forms.DateTimePicker> 控制項|顯示圖形化行事曆，讓使用者選取日期或時間。|  
||<xref:System.Windows.Forms.MonthCalendar> 控制項|顯示圖形化行事曆，讓使用者選取日期範圍。|  
|對話方塊|<xref:System.Windows.Forms.ColorDialog> 控制項|顯示色彩選擇器 對話方塊，可讓使用者介面項目的色彩。|  
||<xref:System.Windows.Forms.FontDialog> 控制項|顯示對話方塊，讓使用者設定的字型和其屬性。|  
||<xref:System.Windows.Forms.OpenFileDialog> 控制項|顯示對話方塊，可讓使用者瀏覽至並選取檔案。|  
||<xref:System.Windows.Forms.PrintDialog> 控制項|顯示對話方塊，可讓使用者選取印表機並設定其屬性。|  
||<xref:System.Windows.Forms.PrintPreviewDialog> 控制項|顯示對話方塊，顯示如何控制<xref:System.Drawing.Printing.PrintDocument>元件會在列印時出現。|  
||<xref:System.Windows.Forms.FolderBrowserDialog> 控制項|會顯示一個對話方塊，可讓使用者瀏覽、 建立和最終選取資料夾。|  
||<xref:System.Windows.Forms.SaveFileDialog> 控制項|顯示對話方塊，可讓使用者儲存檔案。|  
|功能表控制項|<xref:System.Windows.Forms.MenuStrip> 控制項|建立自訂功能表。 **注意：** <xref:System.Windows.Forms.MenuStrip>設計來取代<xref:System.Windows.Forms.MainMenu>控制項。|  
||<xref:System.Windows.Forms.ContextMenuStrip> 控制項|建立自訂內容功能表。 **注意：** <xref:System.Windows.Forms.ContextMenuStrip>設計來取代<xref:System.Windows.Forms.ContextMenu>控制項。|  
|命令|<xref:System.Windows.Forms.Button> 控制項|啟動、 停止或中斷處理程序。|  
||<xref:System.Windows.Forms.LinkLabel> 控制項|為 Web 樣式連結顯示的文字，並觸發事件，當使用者按一下特殊文字。 文字通常是另一個視窗或網站的連結。|  
||<xref:System.Windows.Forms.NotifyIcon> 控制項|代表在背景中執行的應用程式在工作列的狀態通知區域中顯示的圖示。|  
||<xref:System.Windows.Forms.ToolStrip> 控制項|建立包含 Microsoft Windows XP、 Microsoft Office、 Microsoft Internet Explorer 中或自訂外觀及操作，或沒有、 佈景主題與支援溢位和執行階段項目重新排列工具列。 **注意：** <xref:System.Windows.Forms.ToolStrip>控制項用來取代<xref:System.Windows.Forms.ToolBar>控制項。|  
|使用者說明|<xref:System.Windows.Forms.HelpProvider>元件|提供控制項的快顯或線上說明。|  
||<xref:System.Windows.Forms.ToolTip>元件|提供的快顯視窗，使用者將指標停留在控制項上時，顯示控制項用途的簡短描述。|  
|群組其他控制項|<xref:System.Windows.Forms.Panel> 控制項|群組一組未加上標籤，可捲動的框架上的控制項。|  
||<xref:System.Windows.Forms.GroupBox> 控制項|群組加上標籤，不可捲動的框架上的一組控制項 （例如選項按鈕）。|  
||<xref:System.Windows.Forms.TabControl> 控制項|提供索引標籤式的頁面來組織及存取有效率地群組物件。|  
||<xref:System.Windows.Forms.SplitContainer> 控制項|提供以可移動的分隔列分隔的兩個面板。 **注意：** <xref:System.Windows.Forms.SplitContainer>控制項用來取代<xref:System.Windows.Forms.Splitter>控制項。|  
||<xref:System.Windows.Forms.TableLayoutPanel> 控制項|代表會在資料列和資料行所組成的方格中動態配置其內容的面板。|  
||<xref:System.Windows.Forms.FlowLayoutPanel> 控制項|代表透過水平或垂直方式動態配置其內容的面板。|  
|音訊|<xref:System.Media.SoundPlayer> 控制項|播放音效中的.wav 格式檔案。 可以載入或以非同步方式播放音效。|  
  
## <a name="superseded-controls-and-components-by-function"></a>取代控制項和元件，由函式  
  
|函式|已取代的控制項|建議的替代|  
|--------------|------------------------|-----------------------------|  
|顯示資料|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|資訊顯示 （唯讀控制項）|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|功能表控制項|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|命令|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|表單配置|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>另請參閱  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [使用 .NET Framework 開發自訂的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
