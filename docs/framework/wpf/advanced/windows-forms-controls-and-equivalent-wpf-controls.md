---
title: Windows Form 控制項和對等 WPF 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
ms.openlocfilehash: acb8095b32364f1e22330f22df60085016bdc664
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834033"
---
# <a name="windows-forms-controls-and-equivalent-wpf-controls"></a>Windows Form 控制項和對等 WPF 控制項
許多[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項都有對等項目[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項，但有部分[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項中有沒有對等項目[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 本主題會比較這兩項技術所提供的控制項類型。  
  
 您隨時可以使用主應用程式的互通性[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項中沒有對等項目，您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-應用程式。  
  
 下表顯示哪些[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項和元件都有對等項目[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制功能。  
  
|Windows Form 控制項|對等 WPF 控制項|備註|  
|---------------------------|----------------------------|-------------|  
|<xref:System.Windows.Forms.BindingNavigator>|沒有對等的控制項。||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|<xref:System.Windows.Controls.ListBox> 與撰寫。||  
|<xref:System.Windows.Forms.ColorDialog>|沒有對等的控制項。||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<xref:System.Windows.Controls.ComboBox> 不支援自動完成。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<xref:System.Windows.Controls.TextBox> 並將兩個<xref:System.Windows.Controls.Primitives.RepeatButton>控制項。||  
|<xref:System.Windows.Forms.ErrorProvider>|沒有對等的控制項。||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<xref:System.Windows.Controls.WrapPanel> 或 <xref:System.Windows.Controls.StackPanel>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|沒有對等的控制項。||  
|<xref:System.Windows.Forms.FontDialog>|沒有對等的控制項。||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<xref:System.Windows.Window> 不支援子視窗。|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|沒有對等的控制項。|沒有 F1 說明。 「 這是什麼 」 工具提示會取代說明。|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|捲動已內建容器控制項。|  
|<xref:System.Windows.Forms.ImageList>|沒有對等的控制項。||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|沒有對等的控制項。|您可以使用<xref:System.Windows.Documents.Hyperlink>類別將非固定格式內容內超連結。|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|<xref:System.Windows.Controls.ListView>控制項提供的唯讀狀態的詳細資料檢視。|  
|<xref:System.Windows.Forms.MaskedTextBox>|沒有對等的控制項。||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|<xref:System.Windows.Controls.Menu> 控制項樣式設定可以近似的行為和外觀<xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType>類別。|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|沒有對等的控制項。||  
|<xref:System.Windows.Forms.NumericUpDown>|<xref:System.Windows.Controls.TextBox> 並將兩個<xref:System.Windows.Controls.Primitives.RepeatButton>控制項。||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>類別是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]周圍的包裝函式[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]控制項。|  
|<xref:System.Windows.Forms.PageSetupDialog>|沒有對等的控制項。||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|沒有對等的控制項。||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|沒有對等的控制項。||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|沒有對等的控制項。||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>類別是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]周圍的包裝函式[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]控制項。|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|<xref:System.Windows.Controls.ToolBar> 與撰寫。||  
|<xref:System.Windows.Forms.ToolStripDropDown>|<xref:System.Windows.Controls.ToolBar> 與撰寫。||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|<xref:System.Windows.Controls.ToolBar> 與撰寫。||  
|<xref:System.Windows.Forms.ToolStripPanel>|<xref:System.Windows.Controls.ToolBar> 與撰寫。||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|捲動已內建容器控制項。|  
|<xref:System.Windows.Forms.WebBrowser>|<xref:System.Windows.Controls.Frame>、 <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType>|<xref:System.Windows.Controls.Frame>控制項可以裝載的 HTML 網頁。<br /><br /> 在.NET Framework 3.5 SP1 中，啟動<xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType>控制項可以裝載的 HTML 網頁，以及將備份<xref:System.Windows.Controls.Frame>控制項。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF Designer for Windows Form 開發人員](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))
- [逐步解說：裝載在 WPF 中的 Windows Forms 控制項](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [逐步解說：裝載 Windows Forms 中的 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [移轉和互通性](migration-and-interoperability.md)
