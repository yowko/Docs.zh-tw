---
title: 依功能區分 Windows Form 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: 3a82642c985b7ec1cee885cdda7b054adbe3dfee
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115475"
---
# <a name="windows-forms-controls-by-function"></a>依功能區分 Windows Form 控制項
Windows Form 提供控制項和執行數個函數的元件。 下表列出 Windows Form 控制項和元件，根據一般的函式。 此外，其中有多個控制項提供相同的功能，建議使用的控制項都會列出它所取代的控制項的相關附註。 在個別的後續資料表，其建議的取代項目會列出已被取代的控制項。  
  
> [!NOTE]
>  下表待辦事項清單，每個控制項或 Windows Form; 中，您可以使用的元件如需更完整的清單，請參閱[Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>建議的控制項和元件，由函式  
  
|功能|控制項|描述|  
|--------------|-------------|-----------------|  
|資料顯示|<xref:System.Windows.Forms.DataGridView> 控制項|<xref:System.Windows.Forms.DataGridView>控制項提供可自訂的資料表顯示資料。 <xref:System.Windows.Forms.DataGridView>類別可讓您自訂的資料格、 資料列、 資料行和框線。 **注意：** <xref:System.Windows.Forms.DataGridView>控制項提供許多基本和進階功能中遺漏<xref:System.Windows.Forms.DataGrid>控制項。 如需詳細資訊，請參閱[差異 Windows Form DataGridView 和 DataGrid 控制項之間](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|資料繫結和瀏覽|<xref:System.Windows.Forms.BindingSource> 元件|提供貨幣管理、 變更通知和其他服務，以簡化將控制項繫結至資料的表單上。|  
||<xref:System.Windows.Forms.BindingNavigator> 控制項|提供工具列型別介面來瀏覽和操作表單上的資料。|  
|文字編輯|<xref:System.Windows.Forms.TextBox> 控制項|顯示可編輯的使用者在執行階段，或以程式設計方式變更設計階段時輸入的文字。|  
||<xref:System.Windows.Forms.RichTextBox> 控制項|可讓具有純文字或 rtf 文字格式 (RTF) 格式顯示的文字。|  
||<xref:System.Windows.Forms.MaskedTextBox> 控制項|限制使用者輸入的格式|  
|（唯讀） 的資訊顯示|<xref:System.Windows.Forms.Label> 控制項|顯示使用者無法直接編輯的文字。|  
||<xref:System.Windows.Forms.LinkLabel> 控制項|為 Web 樣式連結顯示文字，並觸發事件，當使用者按一下的特殊文字。 文字通常是另一個視窗或網站的連結。|  
||<xref:System.Windows.Forms.StatusStrip> 控制項|顯示使用加框擺設的區域中，通常在父表單底部的應用程式的目前狀態的相關資訊。|  
||<xref:System.Windows.Forms.ProgressBar> 控制項|向使用者顯示作業的目前進度。|  
|網頁上顯示|<xref:System.Windows.Forms.WebBrowser> 控制項|讓使用者巡覽表單中的網頁。|  
|從清單選取項目|<xref:System.Windows.Forms.CheckedListBox> 控制項|顯示可捲動清單的項目，每個伴隨核取方塊。|  
||<xref:System.Windows.Forms.ComboBox> 控制項|顯示下拉式清單的項目。|  
||<xref:System.Windows.Forms.DomainUpDown> 控制項|顯示使用者可以捲動以查看使用向上和向下按鈕的文字項目的清單。|  
||<xref:System.Windows.Forms.ListBox> 控制項|顯示文字和圖形化的項目 （圖示） 的清單。|  
||<xref:System.Windows.Forms.ListView> 控制項|顯示四種不同檢視的其中一個項目。 檢視包含純文字、 小圖示的文字、 文字、 具有大圖示和詳細資料檢視。|  
||<xref:System.Windows.Forms.NumericUpDown> 控制項|顯示使用者可以使用向上和向下按鈕來捲動的數字清單。|  
||<xref:System.Windows.Forms.TreeView> 控制項|顯示階層式物件的集合節點可以包含選擇性的核取方塊或圖示的文字。|  
|圖形顯示|<xref:System.Windows.Forms.PictureBox> 控制項|在框架中顯示圖形化的檔案，例如點陣圖和圖示。|  
|圖形儲存體|<xref:System.Windows.Forms.ImageList> 控制項|做為映像儲存機制。 <xref:System.Windows.Forms.ImageList> 控制項和其所包含的映像可以重複使用從某個應用程式的下一步。|  
|值的設定|<xref:System.Windows.Forms.CheckBox> 控制項|會顯示核取方塊和文字方塊的標籤。 通常用來設定選項。|  
||<xref:System.Windows.Forms.CheckedListBox> 控制項|顯示可捲動清單的項目，每個伴隨核取方塊。|  
||<xref:System.Windows.Forms.RadioButton> 控制項|顯示可以開啟或關閉的按鈕。|  
||<xref:System.Windows.Forms.TrackBar> 控制項|可讓使用者藉由移動沿著標尺的"thumb"，標尺上設定的值。|  
|日期設定|<xref:System.Windows.Forms.DateTimePicker> 控制項|顯示圖形化的行事曆，讓使用者選取日期或時間。|  
||<xref:System.Windows.Forms.MonthCalendar> 控制項|顯示圖形化的行事曆，讓使用者選取日期範圍。|  
|對話方塊|<xref:System.Windows.Forms.ColorDialog> 控制項|顯示色彩選擇器對話方塊，可讓使用者介面項目色彩設定。|  
||<xref:System.Windows.Forms.FontDialog> 控制項|顯示對話方塊，可讓使用者設定的字型和其屬性。|  
||<xref:System.Windows.Forms.OpenFileDialog> 控制項|顯示對話方塊，可讓使用者瀏覽至並選取檔案。|  
||<xref:System.Windows.Forms.PrintDialog> 控制項|顯示對話方塊，可讓使用者選取印表機並設定其屬性。|  
||<xref:System.Windows.Forms.PrintPreviewDialog> 控制項|顯示對話方塊，顯示如何控制<xref:System.Drawing.Printing.PrintDocument>元件會在列印時出現。|  
||<xref:System.Windows.Forms.FolderBrowserDialog> 控制項|會顯示一個對話方塊，可讓使用者瀏覽、 建立，並最終選取資料夾。|  
||<xref:System.Windows.Forms.SaveFileDialog> 控制項|顯示對話方塊，可讓使用者儲存檔案。|  
|功能表控制項|<xref:System.Windows.Forms.MenuStrip> 控制項|建立自訂功能表。 **注意：** <xref:System.Windows.Forms.MenuStrip>設計來取代<xref:System.Windows.Forms.MainMenu>控制項。|  
||<xref:System.Windows.Forms.ContextMenuStrip> 控制項|建立自訂內容功能表。 **注意：** <xref:System.Windows.Forms.ContextMenuStrip>設計來取代<xref:System.Windows.Forms.ContextMenu>控制項。|  
|命令|<xref:System.Windows.Forms.Button> 控制項|啟動、 停止或中斷處理程序。|  
||<xref:System.Windows.Forms.LinkLabel> 控制項|為 Web 樣式連結顯示文字，並觸發事件，當使用者按一下的特殊文字。 文字通常是另一個視窗或網站的連結。|  
||<xref:System.Windows.Forms.NotifyIcon> 控制項|表示在背景中執行的應用程式在工作列的狀態通知區域中顯示的圖示。|  
||<xref:System.Windows.Forms.ToolStrip> 控制項|建立可以有 Microsoft Windows XP、 Microsoft Office、 Microsoft Internet Explorer 中或自訂外觀及操作、 使用或佈景主題，而不支援溢位和執行階段項目重新排序的工具列。 **注意：** <xref:System.Windows.Forms.ToolStrip>控制項的設計是要取代<xref:System.Windows.Forms.ToolBar>控制項。|  
|使用者說明|<xref:System.Windows.Forms.HelpProvider> 元件|提供控制項的快顯畫面或線上說明。|  
||<xref:System.Windows.Forms.ToolTip> 元件|提供當使用者將滑鼠指標停留在控制項上時，會顯示控制項用途的簡短描述的快顯視窗。|  
|群組其他控制項|<xref:System.Windows.Forms.Panel> 控制項|將一組未加上標籤、 可捲動的畫面格上的控制項。|  
||<xref:System.Windows.Forms.GroupBox> 控制項|一組的控制項 （例如選項按鈕） 上加上標籤，不可捲動的框架。|  
||<xref:System.Windows.Forms.TabControl> 控制項|提供有效率的方式來組織及存取索引標籤式的頁面分組的物件。|  
||<xref:System.Windows.Forms.SplitContainer> 控制項|提供以可移動的分隔列分隔的兩個面板。 **注意：** <xref:System.Windows.Forms.SplitContainer>控制項的設計是要取代<xref:System.Windows.Forms.Splitter>控制項。|  
||<xref:System.Windows.Forms.TableLayoutPanel> 控制項|代表會在資料列和資料行所組成的方格中動態配置其內容的面板。|  
||<xref:System.Windows.Forms.FlowLayoutPanel> 控制項|代表透過水平或垂直方式動態配置其內容的面板。|  
|音效|<xref:System.Media.SoundPlayer> 控制項|播放.wav 格式的音效檔。 可以載入或以非同步方式播放音效。|  
  
## <a name="superseded-controls-and-components-by-function"></a>取代控制項和元件，由函式  
  
|功能|已取代的控制項|建議的替代方案|  
|--------------|------------------------|-----------------------------|  
|資料顯示|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|資訊顯示 （唯讀控制項）|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|功能表控制項|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|命令|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|表單配置|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>另請參閱

- [在 Windows Form 上使用的控制項](controls-to-use-on-windows-forms.md)
- [使用 .NET Framework 開發自訂的 Windows Form 控制項](developing-custom-windows-forms-controls.md)
