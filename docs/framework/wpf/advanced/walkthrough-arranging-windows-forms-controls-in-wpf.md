---
title: 逐步解說：在 WPF 中排列 Windows Form 控制項
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 98b108be518a9fef03ee299d43ed591cf736f68f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484935"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>逐步解說：在 WPF 中排列 Windows Form 控制項
本逐步解說會示範如何使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置功能，來排列[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]混合式應用程式中的控制項。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立專案。  
  
-   使用預設的版面配置設定。  
  
-   依內容調整大小。  
  
-   使用絕對位置。  
  
-   明確指定大小。  
  
-   設定版面配置屬性。  
  
-   了解疊置順序的限制。  
  
-   停駐。  
  
-   設定可見度。  
  
-   裝載不會自動縮放的控制項。  
  
-   縮放。  
  
-   旋轉。  
  
-   設定邊框距離及邊界。  
  
-   使用動態版面配置容器。  
  
 在此逐步解說中所述工作的完整程式碼清單，請參閱 < [WPF 範例中排列 Windows Form 控制項](https://go.microsoft.com/fwlink/?LinkID=159971)。  
  
 當您完成時，您必須了解[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]版面配置功能在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-應用程式。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="creating-the-project"></a>建立專案  
  
#### <a name="to-create-and-set-up-the-project"></a>建立並設定專案  
  
1.  建立 WPF 應用程式專案，名為`WpfLayoutHostingWf`。  
  
2.  在 [方案總管] 中，加入下列組件的參考。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3.  按兩下 MainWindow.xaml，在 XAML 檢視中加以開啟。  
  
4.  在 <xref:System.Windows.Window>項目，新增下列[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]命名空間對應。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  在 <xref:System.Windows.Controls.Grid>項目集合<xref:System.Windows.Controls.Grid.ShowGridLines%2A>屬性設`true`和定義五個資料列和三個資料行。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a>使用預設的版面配置設定  
 根據預設，<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目處理所裝載的版面配置[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。  
  
#### <a name="to-use-default-layout-settings"></a>使用預設的版面配置設定  
  
1.  複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  按 F5 鍵建置並執行應用程式。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType>控制項會出現在<xref:System.Windows.Controls.Canvas>。 裝載的控制項的大小調整，根據其內容，而<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會調整大小以容納裝載的控制項。  
  
## <a name="sizing-to-content"></a>依內容調整大小  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目可確保裝載的控制項調整大小，以正確顯示其內容。  
  
#### <a name="to-size-to-content"></a>依內容調整大小  
  
1.  複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  按 F5 鍵建置並執行應用程式。 兩個新的按鈕控制項的大小，以正確，顯示較長的文字字串和較大的字型大小和<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會調整大小以容納裝載的控制項。  
  
## <a name="using-absolute-positioning"></a>使用絕對位置  
 您可以使用絕對位置放置<xref:System.Windows.Forms.Integration.WindowsFormsHost>使用者介面 (UI) 中的任何位置的項目。  
  
#### <a name="to-use-absolute-positioning"></a>使用絕對位置  
  
1.  複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  按 F5 鍵建置並執行應用程式。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目位於 20 像素為單位，從方格資料格上方和左邊的 20 個像素。  
  
## <a name="specifying-size-explicitly"></a>明確指定大小  
 您可以指定的大小<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目使用<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性。  
  
#### <a name="to-specify-size-explicitly"></a>明確指定大小  
  
1.  複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  按 F5 鍵建置並執行應用程式。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目設定為大小為 50 像素寬 x 70 個像素高，這是小於預設版面配置設定。 內容[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]據以重新排列控制項。  
  
## <a name="setting-layout-properties"></a>設定版面配置屬性  
 一律設定裝載控制項的配置相關的屬性所使用的屬性<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。 直接在裝載的控制項上設定版面配置屬性，將產生非預期的結果。  
  
 在裝載的控制項上設定版面配置相關屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]沒有任何作用。  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>查看在裝載控制項上設定屬性的效果  
  
1.  複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  在 [方案總管] 中，按兩下 MainWindow.xaml. vb 或 MainWindow.xaml.cs，以便在程式碼編輯器中加以開啟。  
  
3.  下列程式碼複製到`MainWindow`類別定義。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  按 F5 鍵建置並執行應用程式。  
  
5.  按一下 [ **Click me** ] 按鈕。 `button1_Click`事件處理常式集<xref:System.Windows.Forms.Control.Top%2A>和<xref:System.Windows.Forms.Control.Left%2A>上裝載的控制項的屬性。 這會導致內重新置放裝載的控制項<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。 主機會維持相同的螢幕區域，但會裁剪裝載的控制項。 相反地，裝載的控制項一律應填滿<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。  
  
## <a name="understanding-z-order-limitations"></a>了解疊置順序的限制  
 可見<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素一律應繪製之上其他 WPF 項目，以及它們不會受到疊置順序。 若要查看此疊置順序行為，執行下列作業：

1.  複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
 
2.  按 F5 鍵建置並執行應用程式。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素已經繪製標籤項目上方。  


## <a name="docking"></a>停駐  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]停駐。 設定<xref:System.Windows.Controls.DockPanel.Dock%2A>附加屬性，若要停駐中裝載的控制項<xref:System.Windows.Controls.DockPanel>項目。  
  
#### <a name="to-dock-a-hosted-control"></a>停駐裝載的控制項  
  
1.  複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  按 F5 鍵建置並執行應用程式。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目停駐在右邊<xref:System.Windows.Controls.DockPanel>項目。  
  
## <a name="setting-visibility"></a>設定可見度  
 您可以讓您[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項隱藏或摺疊它，藉由設定<xref:System.Windows.UIElement.Visibility%2A>屬性上的<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。 當控制項隱藏時，它不會顯示，但會佔據版面配置空間。 當控制項摺疊時，它不會顯示，也不會佔據配置空間。  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a>設定裝載控制項的可見度  
  
1.  複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，將下列程式碼複製到類別定義中。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  按 F5 鍵建置並執行應用程式。  
  
4.  按一下 [**按一下即可隱藏**] 按鈕，使<xref:System.Windows.Forms.Integration.WindowsFormsHost>不可見的項目。  
  
5.  按一下 **按一下以摺疊**按鈕以隱藏<xref:System.Windows.Forms.Integration.WindowsFormsHost>從配置的項目完全。 當[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]摺疊控制項、 周圍的項目會重新排列，以佔用它的空間。  
  
## <a name="hosting-a-control-that-does-not-stretch"></a>裝載不會自動縮放的控制項  
 某些[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項有固定的大小和執行自動縮放以填滿版面配置中的可用空間。 比方說，<xref:System.Windows.Forms.MonthCalendar>控制項固定間距來顯示月份。  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a>裝載不會自動縮放的控制項  
  
1.  複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  按 F5 鍵建置並執行應用程式。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會置於方格資料列，但它不會縮放以填滿可用空間。 如果視窗夠大，您可能會看到兩個或多個裝載所顯示的月份<xref:System.Windows.Forms.MonthCalendar>控制項，但這些是資料列中間。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置引擎的中心無法調整大小以填滿可用空間的項目。  
  
## <a name="scaling"></a>縮放  
 不同於 WPF 項目，大部分的 Windows Form 控制項不會持續縮放。 若要提供自訂縮放比例，您覆寫<xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>方法。 
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>使用預設行為縮放裝載的控制項  
  
1.  複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  按 F5 鍵建置並執行應用程式。 裝載的控制項及其周圍元素會縮放 0.5 倍。 不過，裝載控制項的字型不會進行縮放。

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>旋轉  
 與 WPF 項目，不同的是 Windows Form 控制項不支援旋轉。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目將不會與其他 WPF 項目套用旋轉轉換時才會旋轉。 180 度引發以外的任何旋轉值<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>事件。
 
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>查看混合式應用程式中的旋轉效果  
  
1.  複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  按 F5 鍵建置並執行應用程式。 裝載的控制項不會旋轉，但其周圍元素會旋轉 180 度。 您可能必須調整視窗大小來查看元素。  
 

## <a name="setting-padding-and-margins"></a>設定邊框距離及邊界  
 邊框距離及邊界[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置是類似於邊框距離及邊界中的[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。 只要設定<xref:System.Windows.Controls.Control.Padding%2A>並<xref:System.Windows.FrameworkElement.Margin%2A>上的屬性<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>設定裝載控制項的邊框距離及邊界  
  
1.  複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  按 F5 鍵建置並執行應用程式。 邊框距離及邊界設定會套用到裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項中套用它們的方式相同[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。  
  
## <a name="using-dynamic-layout-containers"></a>使用動態版面配置容器  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 提供兩個動態版面配置容器，<xref:System.Windows.Forms.FlowLayoutPanel>和<xref:System.Windows.Forms.TableLayoutPanel>。 您也可以使用這些容器中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置。  
  
#### <a name="to-use-a-dynamic-layout-container"></a>使用動態版面配置容器  
  
1.  複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，將下列程式碼複製到類別定義中。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  將呼叫加入`InitializeFlowLayoutPanel`建構函式的方法。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  按 F5 鍵建置並執行應用程式。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目填滿<xref:System.Windows.Controls.DockPanel>，並<xref:System.Windows.Forms.FlowLayoutPanel>排列它的子控制項，在預設<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [WindowsFormsHost 元素的配置考量](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [排列 Windows Form 控制項，在 WPF 範例](https://go.microsoft.com/fwlink/?LinkID=159971)  
 [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
