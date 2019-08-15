---
title: 逐步解說：在 WPF 中排列 Windows Forms 控制項
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: fa0181e95a03324c4cfa9395ae57439c260d1c23
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972300"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>逐步解說：在 WPF 中排列 Windows Forms 控制項

本逐步解說將示範如何使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置功能, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]在混合式應用程式中排列控制項。

這個逐步解說中所述的工作包括：

- 建立專案。

- 使用預設的版面配置設定。

- 依內容調整大小。

- 使用絕對位置。

- 明確指定大小。

- 設定版面配置屬性。

- 了解疊置順序的限制。

- 停駐。

- 設定可見度。

- 裝載不會自動縮放的控制項。

- 縮放。

- 旋轉。

- 設定邊框距離及邊界。

- 使用動態版面配置容器。

如需本逐步解說中所述工作的完整程式代碼清單, 請參閱[在 WPF 中排列 Windows Forms 控制項範例](https://go.microsoft.com/fwlink/?LinkID=159971)。

當您完成時, 您將瞭解以[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式為基礎的版面配置功能。

## <a name="prerequisites"></a>必要條件

若要完成這個逐步解說，您必須具有 Visual Studio。

## <a name="creating-the-project"></a>建立專案

### <a name="to-create-and-set-up-the-project"></a>建立並設定專案

1. 建立名為`WpfLayoutHostingWf`的 WPF 應用程式專案。

2. 在 [方案總管] 中，加入下列組件的參考。

    - WindowsFormsIntegration

    - System.Windows.Forms

    - System.Drawing

3. 按兩下 MainWindow.xaml，在 XAML 檢視中加以開啟。

4. 在元素中, 新增下列[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]命名空間對應。 <xref:System.Windows.Window>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. 在元素中, <xref:System.Windows.Controls.Grid.ShowGridLines%2A>將屬性設定`true`為, 並定義五個數據列和三個數據行。 <xref:System.Windows.Controls.Grid>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a>使用預設的版面配置設定

根據預設, <xref:System.Windows.Forms.Integration.WindowsFormsHost>專案會處理裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項的版面配置。

### <a name="to-use-default-layout-settings"></a>使用預設的版面配置設定

1. 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. 按 F5 鍵建置並執行應用程式。 控制項會出現在中<xref:System.Windows.Controls.Canvas>。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> 裝載的控制項會根據其內容調整大小, 而元素<xref:System.Windows.Forms.Integration.WindowsFormsHost>的大小則會調整以容納裝載的控制項。

## <a name="sizing-to-content"></a>依內容調整大小

<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素可確保裝載的控制項已調整大小, 以適當地顯示其內容。

### <a name="to-size-to-content"></a>依內容調整大小

1. 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. 按 F5 鍵建置並執行應用程式。 這兩個新的按鈕控制項會調整大小, 以適當地顯示較長的文字字串和<xref:System.Windows.Forms.Integration.WindowsFormsHost>較大的字型大小, 並調整專案大小以配合裝載的控制項。

## <a name="using-absolute-positioning"></a>使用絕對位置

您可以使用絕對位置, 將<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素放在使用者介面 (UI) 的任何位置。

### <a name="to-use-absolute-positioning"></a>使用絕對位置

1. 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. 按 F5 鍵建置並執行應用程式。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會從方格資料格的頂端放置20個圖元, 而從左邊起算20個圖元。

## <a name="specifying-size-explicitly"></a>明確指定大小

您可以<xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.FrameworkElement.Width%2A>使用和<xref:System.Windows.FrameworkElement.Height%2A>屬性來指定元素的大小。

### <a name="to-specify-size-explicitly"></a>明確指定大小

1. 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. 按 F5 鍵建置並執行應用程式。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素設定為50圖元寬乘以70圖元高的大小, 小於預設的版面配置設定。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項的內容會據以重新排列。

## <a name="setting-layout-properties"></a>設定版面配置屬性

一律使用<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素的屬性, 在裝載的控制項上設定版面配置相關屬性。 直接在裝載的控制項上設定版面配置屬性，將產生非預期的結果。

 在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的裝載控制項上設定版面配置相關屬性沒有任何作用。

### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>查看在裝載控制項上設定屬性的效果

1. 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. 在 [方案總管] 中，按兩下 MainWindow.xaml. vb 或 MainWindow.xaml.cs，以便在程式碼編輯器中加以開啟。

3. 將下列程式碼複製到`MainWindow`類別定義中。

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. 按 F5 鍵建置並執行應用程式。

5. 按一下 [**按一下我**] 按鈕。 事件處理常式會在<xref:System.Windows.Forms.Control.Top%2A>裝載<xref:System.Windows.Forms.Control.Left%2A>的控制項上設定和屬性。 `button1_Click` 這會導致裝載的控制項重新置放在<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素內。 主機會維持相同的螢幕區域，但會裁剪裝載的控制項。 相反地, 裝載的控制項應一律填<xref:System.Windows.Forms.Integration.WindowsFormsHost>滿元素。

## <a name="understanding-z-order-limitations"></a>了解疊置順序的限制

可見<xref:System.Windows.Forms.Integration.WindowsFormsHost>的元素一律會在其他 WPF 專案上繪製, 而且不會受到迭置順序的影響。 若要查看此迭置順序行為, 請執行下列動作:

1. 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. 按 F5 鍵建置並執行應用程式。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會在 label 元素上繪製。

## <a name="docking"></a>停駐

<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]停駐。 設定附加屬性, 將裝載的控制項停駐于<xref:System.Windows.Controls.DockPanel>元素中。 <xref:System.Windows.Controls.DockPanel.Dock%2A>

### <a name="to-dock-a-hosted-control"></a>停駐裝載的控制項

1. 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. 按 F5 鍵建置並執行應用程式。 元素會停駐在專案的右側<xref:System.Windows.Controls.DockPanel>。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>

## <a name="setting-visibility"></a>設定可見度

您可以藉由[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]設定專案上<xref:System.Windows.Forms.Integration.WindowsFormsHost>的<xref:System.Windows.UIElement.Visibility%2A>屬性, 讓控制項不可見或折迭。 當控制項隱藏時，它不會顯示，但會佔據版面配置空間。 當控制項摺疊時，它不會顯示，也不會佔據配置空間。

### <a name="to-set-the-visibility-of-a-hosted-control"></a>設定裝載控制項的可見度

1. 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. 在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，將下列程式碼複製到類別定義中。

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. 按 F5 鍵建置並執行應用程式。

4. 按一下 [**按一下以讓隱藏**專案] 按鈕, <xref:System.Windows.Forms.Integration.WindowsFormsHost>讓元素看不見。

5. 按一下 [**按一下以**折迭] 按鈕, <xref:System.Windows.Forms.Integration.WindowsFormsHost>以完全隱藏版面配置中的元素。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]當控制項折迭時, 周圍的元素會重新排列以佔用其空間。

## <a name="hosting-a-control-that-does-not-stretch"></a>裝載不會自動縮放的控制項

有些[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項具有固定的大小, 且不會伸展以填滿配置中的可用空間。 例如, <xref:System.Windows.Forms.MonthCalendar>控制項會在固定空間中顯示一個月。

### <a name="to-host-a-control-that-does-not-stretch"></a>裝載不會自動縮放的控制項

1. 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. 按 F5 鍵建置並執行應用程式。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會置中在方格的資料列中, 但不會伸展以填滿可用的空間。 如果視窗夠大, 您可能會看到兩個以上的月份是由<xref:System.Windows.Forms.MonthCalendar>裝載的控制項所顯示, 但這些是以資料列為中心。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置引擎會將無法調整大小的元素置中, 以填滿可用空間。

## <a name="scaling"></a>縮放

與 WPF 元素不同的是, 大部分的 Windows Forms 控制項都不會持續擴充。 若要提供自訂調整, 請<xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>覆寫方法。

### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>使用預設行為縮放裝載的控制項

1. 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. 按 F5 鍵建置並執行應用程式。 裝載的控制項及其周圍元素會縮放 0.5 倍。 不過，裝載控制項的字型不會進行縮放。

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>旋轉

不同于 WPF 元素, Windows Forms 控制項不支援旋轉。 套用<xref:System.Windows.Forms.Integration.WindowsFormsHost>旋轉轉換時, 元素不會與其他 WPF 專案一起旋轉。 180度以外的<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>任何旋轉值都會引發事件。

### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>查看混合式應用程式中的旋轉效果

1. 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. 按 F5 鍵建置並執行應用程式。 裝載的控制項不會旋轉，但其周圍元素會旋轉 180 度。 您可能必須調整視窗大小來查看元素。

## <a name="setting-padding-and-margins"></a>設定邊框距離及邊界

版面配置中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的填補和邊界類似于中[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]的填補和邊界。 只要在<xref:System.Windows.Controls.Control.Padding%2A> 元素<xref:System.Windows.Forms.Integration.WindowsFormsHost>上<xref:System.Windows.FrameworkElement.Margin%2A>設定和屬性即可。

### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>設定裝載控制項的邊框距離及邊界

1. 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. 按 F5 鍵建置並執行應用程式。 填補和邊界設定會以套用它們[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]的相同方式套用至裝載的控制項。

## <a name="using-dynamic-layout-containers"></a>使用動態版面配置容器

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]提供兩個動態版面配置<xref:System.Windows.Forms.FlowLayoutPanel>容器<xref:System.Windows.Forms.TableLayoutPanel>: 和。 您也可以在版面配置中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用這些容器。

### <a name="to-use-a-dynamic-layout-container"></a>使用動態版面配置容器

1. 將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. 在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，將下列程式碼複製到類別定義中。

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. 請在建構函式中加入 `InitializeFlowLayoutPanel` 方法的呼叫。

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. 按 F5 鍵建置並執行應用程式。 元素會<xref:System.Windows.Forms.FlowLayoutPanel>填滿<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>, 並在預設值中排列其子控制項。 <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Forms.Integration.WindowsFormsHost>

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [WindowsFormsHost 元素的配置考量](layout-considerations-for-the-windowsformshost-element.md)
- [在 WPF 範例中排列 Windows Forms 控制項](https://go.microsoft.com/fwlink/?LinkID=159971)
- [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
