---
title: Windows Form 控制項和對等 WPF 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
ms.openlocfilehash: 0daa399e2d000a228773ee20f157af7439f7acbb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396663"
---
# <a name="windows-forms-controls-and-equivalent-wpf-controls"></a><span data-ttu-id="13c5d-102">Windows Form 控制項和對等 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="13c5d-102">Windows Forms Controls and Equivalent WPF Controls</span></span>
<span data-ttu-id="13c5d-103">許多[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項都有對等項目[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項，但有部分[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項中有沒有對等項目[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="13c5d-103">Many [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls, but some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have no equivalents in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="13c5d-104">本主題會比較這兩項技術所提供的控制項類型。</span><span class="sxs-lookup"><span data-stu-id="13c5d-104">This topic compares control types provided by the two technologies.</span></span>  
  
 <span data-ttu-id="13c5d-105">您隨時可以使用主應用程式的互通性[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項中沒有對等項目，您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-應用程式。</span><span class="sxs-lookup"><span data-stu-id="13c5d-105">You can always use interoperation to host [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls that do not have equivalents in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
 <span data-ttu-id="13c5d-106">下表顯示哪些[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項和元件都有對等項目[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制功能。</span><span class="sxs-lookup"><span data-stu-id="13c5d-106">The following table shows which [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and components have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control functionality.</span></span>  
  
|<span data-ttu-id="13c5d-107">Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="13c5d-107">Windows Forms control</span></span>|<span data-ttu-id="13c5d-108">對等 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="13c5d-108">WPF equivalent control</span></span>|<span data-ttu-id="13c5d-109">備註</span><span class="sxs-lookup"><span data-stu-id="13c5d-109">Remarks</span></span>|  
|---------------------------|----------------------------|-------------|  
|<xref:System.Windows.Forms.BindingNavigator>|<span data-ttu-id="13c5d-110">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-110">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|<span data-ttu-id="13c5d-111"><xref:System.Windows.Controls.ListBox> 與撰寫。</span><span class="sxs-lookup"><span data-stu-id="13c5d-111"><xref:System.Windows.Controls.ListBox> with composition.</span></span>||  
|<xref:System.Windows.Forms.ColorDialog>|<span data-ttu-id="13c5d-112">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-112">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<span data-ttu-id="13c5d-113"><xref:System.Windows.Controls.ComboBox> 不支援自動完成。</span><span class="sxs-lookup"><span data-stu-id="13c5d-113"><xref:System.Windows.Controls.ComboBox> does not support auto-complete.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<span data-ttu-id="13c5d-114"><xref:System.Windows.Controls.TextBox> 並將兩個<xref:System.Windows.Controls.Primitives.RepeatButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-114"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.ErrorProvider>|<span data-ttu-id="13c5d-115">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-115">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<span data-ttu-id="13c5d-116"><xref:System.Windows.Controls.WrapPanel> 或 <xref:System.Windows.Controls.StackPanel></span><span class="sxs-lookup"><span data-stu-id="13c5d-116"><xref:System.Windows.Controls.WrapPanel> or <xref:System.Windows.Controls.StackPanel></span></span>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|<span data-ttu-id="13c5d-117">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-117">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FontDialog>|<span data-ttu-id="13c5d-118">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-118">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<span data-ttu-id="13c5d-119"><xref:System.Windows.Window> 不支援子視窗。</span><span class="sxs-lookup"><span data-stu-id="13c5d-119"><xref:System.Windows.Window> does not support child windows.</span></span>|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|<span data-ttu-id="13c5d-120">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-120">No equivalent control.</span></span>|<span data-ttu-id="13c5d-121">沒有 F1 說明。</span><span class="sxs-lookup"><span data-stu-id="13c5d-121">No F1 Help.</span></span> <span data-ttu-id="13c5d-122">「 這是什麼 」 工具提示會取代說明。</span><span class="sxs-lookup"><span data-stu-id="13c5d-122">"What's This" Help is replaced by ToolTips.</span></span>|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="13c5d-123">捲動已內建容器控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-123">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.ImageList>|<span data-ttu-id="13c5d-124">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-124">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|<span data-ttu-id="13c5d-125">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-125">No equivalent control.</span></span>|<span data-ttu-id="13c5d-126">您可以使用<xref:System.Windows.Documents.Hyperlink>類別將非固定格式內容內超連結。</span><span class="sxs-lookup"><span data-stu-id="13c5d-126">You can use the <xref:System.Windows.Documents.Hyperlink> class to host hyperlinks within flow content.</span></span>|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|<span data-ttu-id="13c5d-127"><xref:System.Windows.Controls.ListView>控制項提供的唯讀狀態的詳細資料檢視。</span><span class="sxs-lookup"><span data-stu-id="13c5d-127">The <xref:System.Windows.Controls.ListView> control provides a read-only details view.</span></span>|  
|<xref:System.Windows.Forms.MaskedTextBox>|<span data-ttu-id="13c5d-128">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-128">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|<span data-ttu-id="13c5d-129"><xref:System.Windows.Controls.Menu> 控制項樣式設定可以近似的行為和外觀<xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="13c5d-129"><xref:System.Windows.Controls.Menu> control styling can approximate the behavior and appearance of the <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> class.</span></span>|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|<span data-ttu-id="13c5d-130">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-130">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.NumericUpDown>|<span data-ttu-id="13c5d-131"><xref:System.Windows.Controls.TextBox> 並將兩個<xref:System.Windows.Controls.Primitives.RepeatButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-131"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|<span data-ttu-id="13c5d-132"><xref:Microsoft.Win32.OpenFileDialog>類別是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]周圍的包裝函式[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-132">The <xref:Microsoft.Win32.OpenFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] control.</span></span>|  
|<xref:System.Windows.Forms.PageSetupDialog>|<span data-ttu-id="13c5d-133">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-133">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|<span data-ttu-id="13c5d-134">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-134">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|<span data-ttu-id="13c5d-135">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-135">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|<span data-ttu-id="13c5d-136">沒有對等的控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-136">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|<span data-ttu-id="13c5d-137"><xref:Microsoft.Win32.SaveFileDialog>類別是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]周圍的包裝函式[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-137">The <xref:Microsoft.Win32.SaveFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] control.</span></span>|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|<span data-ttu-id="13c5d-138"><xref:System.Windows.Controls.ToolBar> 與撰寫。</span><span class="sxs-lookup"><span data-stu-id="13c5d-138"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="13c5d-139"><xref:System.Windows.Controls.ToolBar> 與撰寫。</span><span class="sxs-lookup"><span data-stu-id="13c5d-139"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|<span data-ttu-id="13c5d-140"><xref:System.Windows.Controls.ToolBar> 與撰寫。</span><span class="sxs-lookup"><span data-stu-id="13c5d-140"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripPanel>|<span data-ttu-id="13c5d-141"><xref:System.Windows.Controls.ToolBar> 與撰寫。</span><span class="sxs-lookup"><span data-stu-id="13c5d-141"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="13c5d-142">捲動已內建容器控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-142">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.WebBrowser>|<span data-ttu-id="13c5d-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="13c5d-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span></span>|<span data-ttu-id="13c5d-144"><xref:System.Windows.Controls.Frame>控制項可以裝載的 HTML 網頁。</span><span class="sxs-lookup"><span data-stu-id="13c5d-144">The <xref:System.Windows.Controls.Frame> control can host HTML pages.</span></span><br /><br /> <span data-ttu-id="13c5d-145">從開始[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]，則<xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType>控制項可以裝載的 HTML 網頁，以及將備份<xref:System.Windows.Controls.Frame>控制項。</span><span class="sxs-lookup"><span data-stu-id="13c5d-145">Starting in the [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], the <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> control can host HTML pages and also backs the <xref:System.Windows.Controls.Frame> control.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13c5d-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13c5d-146">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="13c5d-147">WPF Designer for Windows Form 開發人員</span><span class="sxs-lookup"><span data-stu-id="13c5d-147">WPF Designer for Windows Forms Developers</span></span>](https://msdn.microsoft.com/library/47ad0909-e89b-4996-b4ac-874d929f94ca)  
 [<span data-ttu-id="13c5d-148">逐步解說：在 WPF 中裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="13c5d-148">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="13c5d-149">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="13c5d-149">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="13c5d-150">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="13c5d-150">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
