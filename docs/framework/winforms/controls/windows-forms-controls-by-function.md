---
title: 依功能區分 Windows Form 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: 366b7412a61cac9d3706500adaee34fa8659fba2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922709"
---
# <a name="windows-forms-controls-by-function"></a>依功能區分 Windows Form 控制項
Windows Forms 提供可執行多項功能的控制項和元件。 下表列出根據一般功能的 Windows Forms 控制項和元件。 此外, 如果有多個控制項提供相同的函式, 建議的控制項就會列出, 並顯示其所取代控制項的相關注意事項。 在個別的後續表格中, 會列出已取代的控制項及其建議的替代專案。  
  
> [!NOTE]
> 下表不會列出您可以在 Windows Forms 中使用的每個控制項或元件;如需更完整的清單, 請參閱[要在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>依功能的建議控制項和元件  
  
|函數|控制項|說明|  
|--------------|-------------|-----------------|  
|資料顯示|<xref:System.Windows.Forms.DataGridView> 控制項|<xref:System.Windows.Forms.DataGridView>控制項提供可自訂的資料表來顯示資料。 <xref:System.Windows.Forms.DataGridView>類別可讓您自訂資料格、資料列、資料行和框線。 **注意：** 控制項提供了許多<xref:System.Windows.Forms.DataGrid>控制項中遺漏的基本和先進功能。 <xref:System.Windows.Forms.DataGridView> 如需詳細資訊, 請參閱[Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|資料系結和流覽|<xref:System.Windows.Forms.BindingSource> 元件|藉由提供貨幣管理、變更通知和其他服務, 簡化表單上的控制項與資料的系結。|  
||<xref:System.Windows.Forms.BindingNavigator> 控制項|提供工具列類型介面, 以在表單上導覽和運算元據。|  
|文字編輯|<xref:System.Windows.Forms.TextBox> 控制項|顯示在設計階段輸入的文字, 可由使用者在執行時間編輯, 或以程式設計方式變更。|  
||<xref:System.Windows.Forms.RichTextBox> 控制項|允許以純文字或 rtf 格式 (RTF) 格式來顯示文字。|  
||<xref:System.Windows.Forms.MaskedTextBox> 控制項|限制使用者輸入的格式|  
|資訊顯示 (唯讀)|<xref:System.Windows.Forms.Label> 控制項|顯示使用者無法直接編輯的文字。|  
||<xref:System.Windows.Forms.LinkLabel> 控制項|將文字顯示為 Web 樣式連結, 並在使用者按一下特殊文字時觸發事件。 文字通常是另一個視窗或網站的連結。|  
||<xref:System.Windows.Forms.StatusStrip> 控制項|使用框住的區域 (通常在父表單底部), 顯示應用程式目前狀態的相關資訊。|  
||<xref:System.Windows.Forms.ProgressBar> 控制項|向使用者顯示目前作業的進度。|  
|網頁顯示|<xref:System.Windows.Forms.WebBrowser> 控制項|讓使用者巡覽表單中的網頁。|  
|從清單中選取|<xref:System.Windows.Forms.CheckedListBox> 控制項|顯示專案的可滾動清單, 每一個都附有一個核取方塊。|  
||<xref:System.Windows.Forms.ComboBox> 控制項|顯示專案的下拉式清單。|  
||<xref:System.Windows.Forms.DomainUpDown> 控制項|顯示使用者可以使用向上和向下按鈕來滾動的文字專案清單。|  
||<xref:System.Windows.Forms.ListBox> 控制項|顯示文字和圖形專案 (圖示) 的清單。|  
||<xref:System.Windows.Forms.ListView> 控制項|以四個不同的視圖之一顯示專案。 Views 僅包含文字、包含小圖示的文字、具有大圖示的文字, 以及詳細資料檢視。|  
||<xref:System.Windows.Forms.NumericUpDown> 控制項|顯示使用者可以使用向上和向下按鈕來滾動的數位清單。|  
||<xref:System.Windows.Forms.TreeView> 控制項|顯示節點物件的階層式集合, 其中可以包含具有選擇性核取方塊或圖示的文字。|  
|圖形顯示|<xref:System.Windows.Forms.PictureBox> 控制項|顯示框架中的圖形檔案, 例如點陣圖和圖示。|  
|圖形儲存|<xref:System.Windows.Forms.ImageList> 控制項|作為影像的存放庫。 <xref:System.Windows.Forms.ImageList>控制項及其包含的影像, 可以從一個應用程式重複使用到下一個。|  
|值設定|<xref:System.Windows.Forms.CheckBox> 控制項|顯示覆選框和文字標籤。 通常用來設定選項。|  
||<xref:System.Windows.Forms.CheckedListBox> 控制項|顯示專案的可滾動清單, 每一個都附有一個核取方塊。|  
||<xref:System.Windows.Forms.RadioButton> 控制項|顯示可以開啟或關閉的按鈕。|  
||<xref:System.Windows.Forms.TrackBar> 控制項|可讓使用者沿著尺規移動「捲動方塊」, 以設定尺規上的值。|  
|日期設定|<xref:System.Windows.Forms.DateTimePicker> 控制項|顯示允許使用者選取日期或時間的圖形化行事曆。|  
||<xref:System.Windows.Forms.MonthCalendar> 控制項|顯示允許使用者選取某個日期範圍的圖形化行事曆。|  
|對話方塊|<xref:System.Windows.Forms.ColorDialog> 控制項|顯示 [色彩選擇器] 對話方塊, 可讓使用者設定介面元素的色彩。|  
||<xref:System.Windows.Forms.FontDialog> 控制項|顯示可讓使用者設定字型和其屬性的對話方塊。|  
||<xref:System.Windows.Forms.OpenFileDialog> 控制項|顯示可讓使用者流覽並選取檔案的對話方塊。|  
||<xref:System.Windows.Forms.PrintDialog> 控制項|顯示可讓使用者選取印表機並設定其屬性的對話方塊。|  
||<xref:System.Windows.Forms.PrintPreviewDialog> 控制項|顯示對話方塊, 其中會顯示控制項<xref:System.Drawing.Printing.PrintDocument>元件在列印時的顯示方式。|  
||<xref:System.Windows.Forms.FolderBrowserDialog> 控制項|顯示對話方塊, 可讓使用者流覽、建立, 最後選取資料夾|  
||<xref:System.Windows.Forms.SaveFileDialog> 控制項|顯示可讓使用者儲存檔案的對話方塊。|  
|Menu 控制項|<xref:System.Windows.Forms.MenuStrip> 控制項|建立自訂功能表。 **注意：** 的<xref:System.Windows.Forms.MenuStrip>設計目的是要<xref:System.Windows.Forms.MainMenu>取代控制項。|  
||<xref:System.Windows.Forms.ContextMenuStrip> 控制項|建立自訂內容功能表。 **注意：** 的<xref:System.Windows.Forms.ContextMenuStrip>設計目的是要<xref:System.Windows.Forms.ContextMenu>取代控制項。|  
|命令|<xref:System.Windows.Forms.Button> 控制項|啟動、停止或中斷進程。|  
||<xref:System.Windows.Forms.LinkLabel> 控制項|將文字顯示為 Web 樣式連結, 並在使用者按一下特殊文字時觸發事件。 文字通常是另一個視窗或網站的連結。|  
||<xref:System.Windows.Forms.NotifyIcon> 控制項|在工作列的狀態通知區域中顯示圖示, 代表在背景中執行的應用程式。|  
||<xref:System.Windows.Forms.ToolStrip> 控制項|建立可擁有 Microsoft Windows XP、Microsoft Office、Microsoft Internet Explorer 或自訂外觀與風格的工具列, 包括或不使用主題, 以及支援溢位和執行時間專案重新排列。 **注意：** 控制項<xref:System.Windows.Forms.ToolStrip>的設計目的是要<xref:System.Windows.Forms.ToolBar>取代控制項。|  
|使用者說明|<xref:System.Windows.Forms.HelpProvider> 元件|提供控制項的快顯或線上說明。|  
||<xref:System.Windows.Forms.ToolTip> 元件|提供一個快顯視窗, 在使用者將指標放在控制項上時, 顯示控制項用途的簡短描述。|  
|群組其他控制項|<xref:System.Windows.Forms.Panel> 控制項|在未標記的可滾動框架上, 將一組控制群組成群組。|  
||<xref:System.Windows.Forms.GroupBox> 控制項|將一組控制項 (例如選項按鈕) 組成已加上標籤的資料框架。|  
||<xref:System.Windows.Forms.TabControl> 控制項|提供索引標籤式頁面, 以有效率地組織和存取群組物件。|  
||<xref:System.Windows.Forms.SplitContainer> 控制項|提供兩個以可移動的橫條分隔的面板。 **注意：** 控制項<xref:System.Windows.Forms.SplitContainer>的設計目的是要<xref:System.Windows.Forms.Splitter>取代控制項。|  
||<xref:System.Windows.Forms.TableLayoutPanel> 控制項|代表會在資料列和資料行所組成的方格中動態配置其內容的面板。|  
||<xref:System.Windows.Forms.FlowLayoutPanel> 控制項|代表透過水平或垂直方式動態配置其內容的面板。|  
|音效|<xref:System.Media.SoundPlayer> 控制項|以 .wav 格式播放音效檔。 可以用非同步方式載入或播放聲音。|  
  
## <a name="superseded-controls-and-components-by-function"></a>依函式取代的控制項和元件  
  
|函數|取代的控制項|建議取代|  
|--------------|------------------------|-----------------------------|  
|資料顯示|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|資訊顯示 (唯讀控制項)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Menu 控制項|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|命令|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|表單配置|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>另請參閱

- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [使用 .NET Framework 開發自訂的 Windows Forms 控制項](developing-custom-windows-forms-controls.md)
