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
ms.openlocfilehash: 3a94ef65be99b01a9511f37872cbcacd6ec12264
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179441"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>逐步解說：在 WPF 中排列 Windows Forms 控制項

本逐步解說將示範如何使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 版面配置功能來排列混合式應用程式中的 @no__t 1 控制項。

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

如需本逐步解說中所述工作的完整程式代碼清單，請參閱[在 WPF 中排列 Windows Forms 控制項範例](https://go.microsoft.com/fwlink/?LinkID=159971)。

當您完成時，您將瞭解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 架構應用程式中的 @no__t 0 版面配置功能。

## <a name="prerequisites"></a>必要條件

若要完成這個逐步解說，您必須具有 Visual Studio。

## <a name="creating-the-project"></a>建立專案

若要建立並設定專案，請遵循下列步驟：

1. 建立名為 `WpfLayoutHostingWf` 的 WPF 應用程式專案。

2. 在方案總管中，新增下列元件的參考：

    - WindowsFormsIntegration
    - System.Windows.Forms
    - System.Drawing

3. 按兩下 [ *mainwindow.xaml* ]，以 xaml 視圖開啟它。

4. 在 <xref:System.Windows.Window> 元素中，新增下列 @no__t 1 命名空間對應。

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. 在 <xref:System.Windows.Controls.Grid> 元素中，將 <xref:System.Windows.Controls.Grid.ShowGridLines%2A> 屬性設定為 `true`，並定義五個數據列和三個數據行。

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a>使用預設的版面配置設定

根據預設，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素會處理所裝載之 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的版面配置。

若要使用預設的版面配置設定，請遵循下列步驟：

1. 將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. 按 <kbd>F5</kbd> 鍵建置並執行應用程式。 @No__t-0 <xref:System.Windows.Forms.Button?displayProperty=nameWithType> 控制項會出現在 <xref:System.Windows.Controls.Canvas> 中。 裝載的控制項會根據其內容調整大小，而 @no__t 0 元素會調整大小以容納裝載的控制項。

## <a name="sizing-to-content"></a>依內容調整大小

@No__t-0 元素可確保裝載的控制項已調整大小，以正確顯示其內容。

若要將大小調整為內容，請遵循下列步驟：

1. 將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. 按 <kbd>F5</kbd> 鍵建置並執行應用程式。 這兩個新的按鈕控制項會調整大小，以適當地顯示較長的文字字串和較大的字型大小，而 @no__t 0 元素會調整大小以容納裝載的控制項。

## <a name="using-absolute-positioning"></a>使用絕對位置

您可以使用絕對位置，將 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素放在使用者介面（UI）的任何位置。

若要使用絕對位置，請遵循下列步驟：

1. 將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. 按 <kbd>F5</kbd> 鍵建置並執行應用程式。 @No__t-0 元素會從方格資料格的頂端放置20個圖元，左邊有20個圖元。

## <a name="specifying-size-explicitly"></a>明確指定大小

您可以使用 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性來指定 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素的大小。

若要明確指定大小，請遵循下列步驟：

1. 將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. 按 <kbd>F5</kbd> 鍵建置並執行應用程式。 @No__t-0 元素設定為50圖元寬乘以70圖元高的大小，小於預設的版面配置設定。 @No__t-0 控制項的內容會據此重新排列。

## <a name="setting-layout-properties"></a>設定版面配置屬性

一律使用 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素的屬性，在裝載的控制項上設定版面配置相關屬性。 直接在裝載的控制項上設定版面配置屬性，將產生非預期的結果。

 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的裝載控制項上設定版面配置相關屬性沒有任何作用。

若要查看在裝載的控制項上設定屬性的效果，請遵循下列步驟：

1. 將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. 在**方案總管**中，按兩下 [ *mainwindow.xaml* ] 或 [ *MainWindow.xaml.cs* ]，在程式碼編輯器中開啟它。

3. 將下列程式碼複製到 `MainWindow` 類別定義中：

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. 按 <kbd>F5</kbd> 鍵建置並執行應用程式。

5. 按一下 [**按一下我**] 按鈕。 @No__t-0 事件處理常式會在裝載的控制項上設定 <xref:System.Windows.Forms.Control.Top%2A> 和 @no__t 2 屬性。 這會導致裝載的控制項重新置放在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素內。 主機會維持相同的螢幕區域，但會裁剪裝載的控制項。 相反地，裝載的控制項應一律填入 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素。

## <a name="understanding-z-order-limitations"></a>了解疊置順序的限制

可見 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素一律會在其他 WPF 專案上繪製，而且不會受到迭置順序的影響。 若要查看此迭置順序行為，請執行下列動作：

1. 將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. 按 <kbd>F5</kbd> 鍵建置並執行應用程式。 @No__t-0 元素會在 label 元素上繪製。

## <a name="docking"></a>停駐

<xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素支援 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 銜接。 設定 @no__t 0 附加屬性，將裝載的控制項停駐在 @no__t 1 元素中。

若要停駐裝載的控制項，請遵循下列步驟：

1. 將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. 按 <kbd>F5</kbd> 鍵建置並執行應用程式。 @No__t-0 元素停駐在 <xref:System.Windows.Controls.DockPanel> 元素的右側。

## <a name="setting-visibility"></a>設定可見度

您可以在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素上設定 <xref:System.Windows.UIElement.Visibility%2A> 屬性，讓您的 @no__t 0 控制項不可見或折迭。 當控制項隱藏時，它不會顯示，但會佔據版面配置空間。 當控制項摺疊時，它不會顯示，也不會佔據配置空間。

若要設定裝載控制項的可見度，請遵循下列步驟：

1. 將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. 在*mainwindow.xaml*或*MainWindow.xaml.cs*中，將下列程式碼複製到類別定義中：

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. 按 <kbd>F5</kbd> 鍵建置並執行應用程式。

4. 按一下 [**按一下以讓隱藏**專案] 按鈕，讓 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素不可見。

5. 按一下 [**按一下以**折迭] 按鈕，以完全隱藏配置中的 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素。 當 @no__t 0 控制項折迭時，周圍的元素會重新排列以佔用其空間。

## <a name="hosting-a-control-that-does-not-stretch"></a>裝載不會自動縮放的控制項

有些 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項具有固定的大小，且不會伸展以填滿配置中的可用空間。 例如，<xref:System.Windows.Forms.MonthCalendar> 控制項會在固定空間中顯示一個月。

若要裝載不會延展的控制項，請遵循下列步驟：

1. 將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. 按 <kbd>F5</kbd> 鍵建置並執行應用程式。 @No__t-0 元素在方格資料列中置中，但不會伸展以填滿可用空間。 如果視窗夠大，您可能會看到兩個或多個月由主控的 <xref:System.Windows.Forms.MonthCalendar> 控制項顯示，但這些會在資料列中置中。 @No__t 0 版面配置引擎會將無法調整大小的元素置中，以填滿可用空間。

## <a name="scaling"></a>縮放

與 WPF 元素不同的是，大部分的 Windows Forms 控制項都不會持續擴充。 若要提供自訂調整，請覆寫 <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> 方法。

若要使用預設行為來調整裝載的控制項，請遵循下列步驟：

1. 將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. 按 <kbd>F5</kbd> 鍵建置並執行應用程式。 裝載的控制項及其周圍元素會縮放 0.5 倍。 不過，裝載控制項的字型不會進行縮放。

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>旋轉

不同于 WPF 元素，Windows Forms 控制項不支援旋轉。 套用旋轉轉換時，@no__t 0 元素不會隨著其他 WPF 元素旋轉。 180度以外的任何旋轉值都會引發 <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> 事件。

若要查看在混合式應用程式中輪替的效果，請遵循下列步驟：

1. 將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. 按 <kbd>F5</kbd> 鍵建置並執行應用程式。 裝載的控制項不會旋轉，但其周圍元素會旋轉 180 度。 您可能必須調整視窗大小來查看元素。

## <a name="setting-padding-and-margins"></a>設定邊框距離及邊界

@No__t 0 版面配置中的填補和邊界，類似于 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 中的填補和邊界。 只要在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素上設定 <xref:System.Windows.Controls.Control.Padding%2A> 和 @no__t 1 屬性即可。

若要設定主控控制項的填補和邊界，請遵循下列步驟：

1. 將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. 按 <kbd>F5</kbd> 鍵建置並執行應用程式。 填補和邊界設定會以套用至 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 的相同方式套用至主控的 @no__t 0 控制項。

## <a name="using-dynamic-layout-containers"></a>使用動態版面配置容器

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 提供兩個動態版面配置容器，<xref:System.Windows.Forms.FlowLayoutPanel> 和 @no__t 2。 您也可以在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 版面配置中使用這些容器。

若要使用動態版面配置容器，請遵循下列步驟：

1. 將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. 在*mainwindow.xaml*或*MainWindow.xaml.cs*中，將下列程式碼複製到類別定義中：

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. 在函式中新增對 `InitializeFlowLayoutPanel` 方法的呼叫：

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. 按 <kbd>F5</kbd> 鍵建置並執行應用程式。 @No__t-0 元素會填滿 <xref:System.Windows.Controls.DockPanel>，而 <xref:System.Windows.Forms.FlowLayoutPanel> 則會在預設的 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 中排列其子控制項。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [WindowsFormsHost 元素的配置考量](layout-considerations-for-the-windowsformshost-element.md)
- [在 WPF 範例中排列 Windows Forms 控制項](https://go.microsoft.com/fwlink/?LinkID=159971)
- [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項 @ no__t-0
- [逐步解說：在 Windows Forms @ no__t-0 中裝載 WPF 複合控制項
