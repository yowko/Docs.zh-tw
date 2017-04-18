---
title: "逐步解說：在 WPF 中排列 Windows Form 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "排列控制項"
  - "混合應用程式 [WPF 互通性]"
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
caps.latest.revision: 31
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 28
---
# 逐步解說：在 WPF 中排列 Windows Form 控制項
這個逐步解說會顯示如何使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 配置功能在混合應用程式中排列 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  
  
 逐步解說將說明的工作包括：  
  
-   建立專案。  
  
-   使用預設配置設定  
  
-   隨內容調整大小  
  
-   使用絕對位置  
  
-   明確指定大小  
  
-   設定配置屬性  
  
-   了解疊置順序 \(Z\-order\) 限制  
  
-   停駐  
  
-   設定可視性  
  
-   裝載不會自動縮放的控制項  
  
-   縮放  
  
-   旋轉  
  
-   設定邊框距離和邊界  
  
-   使用動態配置容器  
  
 如需這個逐步解說中所說明之工作的完整程式碼清單，請參閱[在 WPF 中排列 Windows Form 控制項範例](http://go.microsoft.com/fwlink/?LinkID=159971) \(英文\)。  
  
 當您完成時，將對 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 架構應用程式中的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 配置功能將會有更深入的了解。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## 建立專案  
  
#### 若要建立並設定此專案  
  
1.  建立名稱為 `WpfLayoutHostingWf` 的 WPF 應用程式專案。  
  
2.  在 \[方案總管\] 中加入下列組件的參考。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3.  按兩下 MainWindow.xaml，在 \[XAML\] 檢視中開啟。  
  
4.  在 <xref:System.Windows.Window> 項目中，加入下列 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 命名空間對應。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  在 <xref:System.Windows.Controls.Grid> 項目中，將 <xref:System.Windows.Controls.Grid.ShowGridLines%2A> 屬性設定為 `true` 並定五個資料列和三個資料行。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## 使用預設配置設定  
 根據預設，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會處理已裝載之 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的配置。  
  
#### 若要使用預設配置設定  
  
1.  將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目中。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  按 F5 建置並執行應用程式。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=fullName> 控制項隨即顯示在 <xref:System.Windows.Controls.Canvas> 中。  已裝載的控制項會根據其內容調整大小，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目的大小會調整為可以以容納已裝載的控制項。  
  
## 隨內容調整大小  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會確保已裝載之控制項的大小能夠正確顯示其內容。  
  
#### 若要隨內容調整大小  
  
1.  將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目中。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  按 F5 建置並執行應用程式。  兩個新的按鈕控制項會調整大小，以正確顯示更長的文字字串和更大的字型大小，而且 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會重新調整大小以容納已裝載的控制項。  
  
## 使用絕對位置  
 您可以使用絕對位置將 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目放置在使用者介面 \(UI\) 的任何地方。  
  
#### 若要使用絕對位置  
  
1.  將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目中。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  按 F5 建置並執行應用程式。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目放置於距格線儲存格頂端 20 像素及距左側 20 像素的位置。  
  
## 明確指定大小  
 您可以使用 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性來指定 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目的大小。  
  
#### 若要明確指定大小  
  
1.  將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目中。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  按 F5 建置並執行應用程式。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會設為 50 像素寬乘以 70 像素高的大小，比預設配置設定還要小。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的內容會根據這個大小重新排列。  
  
## 設定配置屬性  
 永遠藉由使用 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目的屬性設定已裝載之控制項上的配置相關屬性。  直接在已裝載之控制項上設定配置屬性會產生非預期的結果。  
  
 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的已裝載控制項上設定配置相關屬性將不會有任何效果。  
  
#### 若要查看在已裝載控制項上設定屬性的效果  
  
1.  將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目中。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  在 \[方案總管\] 中按兩下 MainWindow.xaml.  vb 或 MainWindow.xaml.cs，在程式碼編輯器中開啟。  
  
3.  將下列程式碼複製到 `MainWindow` 類別定義中。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  按 F5 建置並執行應用程式。  
  
5.  按一下 \[**Click me**\] 按鈕。  `button1_Click` 事件處理常式會在已裝載的控制項上設定 <xref:System.Windows.Forms.Control.Top%2A> 和 <xref:System.Windows.Forms.Control.Left%2A> 屬性。  這會使已裝載的控制項重新調整在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目內的位置。  主項目會維持相同的螢幕區域，但是已裝載的控制項會遭到裁剪。  已裝載的控制項應該一律會填滿 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目。  
  
## 了解疊置順序 \(Z\-order\) 限制  
 根據預設，看得見<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目永遠會繪製在其他的最上層[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]項目，以及它們並沒有受到疊置順序。  若要啟用疊置順序，將<xref:System.Windows.Interop.HwndHost.IsRedirected%2A>屬性的<xref:System.Windows.Forms.Integration.WindowsFormsHost>設為 true， <xref:System.Windows.Interop.HwndHost.CompositionMode%2A>屬性，以<xref:System.Windows.Interop.CompositionMode.Full>或<xref:System.Windows.Interop.CompositionMode.OutputOnly>。  
  
#### 若要查看預設疊置順序的行為  
  
1.  將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目中。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
  
2.  按 F5 建置並執行應用程式。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會繪製在標籤項目上。  
  
#### 若要查看疊置順序的行為，IsRedirected，則為 true 時  
  
1.  取代下列 XAML 中的前一個範例中，疊置順序。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#8b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#8b)]  
  
     按 F5 建置並執行應用程式。  標籤的項目繪製於<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。  
  
## 停駐  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目支援 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 停駐。  設定 <xref:System.Windows.Controls.DockPanel.Dock%2A> 附加屬性以停駐 <xref:System.Windows.Controls.DockPanel> 項目中的已裝載控制項。  
  
#### 若要停駐已裝載的控制項  
  
1.  將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目中。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  按 F5 建置並執行應用程式。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會停駐在 <xref:System.Windows.Controls.DockPanel> 項目的右側。  
  
## 設定可視性  
 您可以設定 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目上的 <xref:System.Windows.UIElement.Visibility%2A> 屬性，使 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項隱藏或摺疊。  當控制項不可見時，就不會顯示出來，但是會佔據配置空間。  當控制項摺疊時，不會顯示出來，也不會佔據配置空間。  
  
#### 若要設定已裝載控制項的可視性  
  
1.  將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目中。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，將下列程式碼複製到類別定義中。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  按 F5 建置並執行應用程式。  
  
4.  按一下 \[**Click to make invisible**\] 按鈕，將 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目隱藏起來。  
  
5.  按一下 \[**Click to collapse**\] 按鈕，將 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目從配置中整個隱藏起來。  當 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項摺疊時，周圍項目會重新排列以使用其空間。  
  
## 裝載不會自動縮放的控制項  
 部分 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項有固定的大小，無法自動縮放以填滿配置中的可用空間。  例如，<xref:System.Windows.Forms.MonthCalendar> 控制項會以固定空間顯示月份。  
  
#### 若要裝載不會自動縮放的控制項  
  
1.  將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目中。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  按 F5 建置並執行應用程式。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會置於格線列的中央，但是不會自動縮放以填滿可用空間。  如果視窗夠大，可能會看到已裝載的 <xref:System.Windows.Forms.MonthCalendar> 控制項顯示兩個以上的月份，但是都在列的中央。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 配置引擎會將無法調整大小以填滿可用空間的項目置中。  
  
## 縮放  
 不像 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目，大多數 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項都無法連續縮放。  預設情況下， <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的縮放比例可能的話，其裝載的控制項。  若要啟用全能的縮放比例，請設定<xref:System.Windows.Interop.HwndHost.IsRedirected%2A>屬性的<xref:System.Windows.Forms.Integration.WindowsFormsHost>設為 true， <xref:System.Windows.Interop.HwndHost.CompositionMode%2A>屬性，以<xref:System.Windows.Interop.CompositionMode.Full>或<xref:System.Windows.Interop.CompositionMode.OutputOnly>。  
  
#### 若要縮放已裝載的控制項使用的預設行為  
  
1.  將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目中。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  按 F5 建置並執行應用程式。  已裝載的控制項及其周圍項目會以 0.5 的因數進行縮放。  不過，已裝載之控制項的字型不會縮放。  
  
#### 若要縮放已裝載的控制項藉由將 IsRedirected 設定為 true  
  
1.  取代下列 XAML 中的上一個縮放比例的範例。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#12b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#12b)]  
  
2.  按 F5 建置並執行應用程式。  裝載的控制項，其周圍的項目和裝載之的控制項的字型被縮放 0.5 個係數。  
  
## 旋轉  
 不像 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項不支援旋轉。  預設情況下， <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目不會旋轉與其他[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]套用旋轉轉換後的項目。  任何 180 度以外的旋轉值都會引發 <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> 事件。  若要啟用旋轉為任何角度，請設定<xref:System.Windows.Interop.HwndHost.IsRedirected%2A>屬性的<xref:System.Windows.Forms.Integration.WindowsFormsHost>設為 true， <xref:System.Windows.Interop.HwndHost.CompositionMode%2A>屬性，以<xref:System.Windows.Interop.CompositionMode.Full>或<xref:System.Windows.Interop.CompositionMode.OutputOnly>。  
  
#### 若要查看混合應用程式中的旋轉效果  
  
1.  將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目中。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  按 F5 建置並執行應用程式。  已裝載的控制項不會旋轉，但是其周圍項目會以 180 度的角度旋轉。  您可能需要調整視窗大小，才能看見項目。  
  
#### 若要查看混合應用程式中的旋轉效果，IsRedirected，則為 true 時  
  
1.  取代下列 XAML 中的前一個範例中，旋轉。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#13b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#13b)]  
  
2.  按 F5 建置並執行應用程式。  旋轉裝載的控制項。  請注意， <xref:System.Windows.Media.RotateTransform.Angle%2A>屬性，請設定為 \[任何值。  您可能需要調整視窗大小，才能看見項目。  
  
## 設定邊框距離和邊界  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 配置中的邊框距離和邊界與 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 中的邊框距離和邊界類似。  只要設定 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目上的 <xref:System.Windows.Controls.Control.Padding%2A> 和 <xref:System.Windows.FrameworkElement.Margin%2A> 屬性即可。  
  
#### 若要設定已裝載之控制項的邊框距離和邊界  
  
1.  將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目中。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  按 F5 建置並執行應用程式。  邊框距離和邊界設定會以在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 中套用的相同方法，套用至已裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  
  
## 使用動態配置容器  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 提供兩個動態配置容器：<xref:System.Windows.Forms.FlowLayoutPanel> 和 <xref:System.Windows.Forms.TableLayoutPanel>。  您也可以在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 配置中使用這些容器。  
  
#### 若要使用動態配置容器  
  
1.  將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目中。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，將下列程式碼複製到類別定義中。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  在建構函式中，加入對 `InitializeFlowLayoutPanel` 方法的呼叫。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  按 F5 建置並執行應用程式。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會填滿 <xref:System.Windows.Controls.DockPanel>，<xref:System.Windows.Forms.FlowLayoutPanel> 會以預設的 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 排列其子控制項。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)   
 [WindowsFormsHost 項目的配置考量](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)   
 [在 WPF 中排列 Windows Form 控制項範例](http://go.microsoft.com/fwlink/?LinkID=159971)   
 [逐步解說：在 WPF 中裝載 Windows Form 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)