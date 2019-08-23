---
title: 視覺分層中的點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit testing functionality [WPF]
- visual layer [WPF], hit testing functionality
ms.assetid: b1a64b61-14be-4d75-b89a-5c67bebb2c7b
ms.openlocfilehash: 92b7e8ffab001af4dba6c571fd06c64f2865b1e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962112"
---
# <a name="hit-testing-in-the-visual-layer"></a>視覺分層中的點擊測試
本主題提供視覺分層所提供點擊測試功能的概觀。 點擊測試支援可讓您判斷幾何或點值是否落在的呈現內容<xref:System.Windows.Media.Visual>中, 讓您能夠執行使用者介面行為, 例如選取多個物件的選取矩形。  

<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>點擊測試案例  
 <xref:System.Windows.UIElement> 類別<xref:System.Windows.UIElement.InputHitTest%2A>提供方法, 可讓您對使用指定座標值的元素進行點擊測試。 在許多情況下, <xref:System.Windows.UIElement.InputHitTest%2A>方法會提供所需的功能來執行專案的點擊測試。 不過，有幾個案例，您可能需要在視覺分層實作點擊測試。  
  
- 針對非<xref:System.Windows.UIElement>物件進行點擊測試:如果您要點擊測試非<xref:System.Windows.UIElement>物件 ( <xref:System.Windows.Media.DrawingVisual>例如或繪圖物件), 這就適用。  
  
- 使用幾何進行點擊測試:如果您需要使用 geometry 物件進行點擊測試, 而不是點的座標值, 則適用這種情況。  
  
- 針對多個物件進行點擊測試:當您需要對多個物件進行點擊測試 (例如重迭的物件) 時, 就適用這種情況。 您可以取得和幾何或點交集的所有視覺效果結果，不只有第一個結果。  
  
- 忽略<xref:System.Windows.UIElement>點擊測試原則:這適用于您需要忽略<xref:System.Windows.UIElement>點擊測試原則的情況, 這會考慮是否已停用或不隱藏元素等因素。  
  
> [!NOTE]
> 如需示範在視覺分層進行點擊測試的完整程式碼範例，請參閱[使用 DrawingVisuals 進行點擊測試範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159994) 和[使用 Win32 交互操作進行點擊測試範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159995)。  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>點擊測試支援  
 類別中方法<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>的目的是要判斷幾何或點座標值是否在指定物件的呈現內容中, 例如控制項或圖形專案。 <xref:System.Windows.Media.VisualTreeHelper> 例如，您可以使用點擊測試來判斷物件的週框矩形內的滑鼠點擊是否落於圓形的幾何內。 您也可以選擇覆寫預設點擊測試實作，以執行您的自訂點擊測試計算。  
  
 下圖說明非矩形物件的區域和其週框之間的關聯性。  
  
 ![有效點擊測試區域的圖表](./media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
有效點擊測試區域的圖表  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>點擊測試和疊置順序  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 視覺分層支援對點或幾何底下的所有物件進行點擊測試，而不只有最上層物件。 以疊置順序傳回結果。 不過, 做為參數傳遞至<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法的視覺物件會決定要點擊測試之視覺化樹狀結構的哪個部分。 您可以對整個視覺化樹狀結構或其任何部分進行點擊測試。  
  
 在下圖中，圓形物件位於正方形和三角形物件上方。 如果您只想要對其 z 順序值最上層的視覺物件進行點擊測試, 您可以將視覺點擊測試列舉設定為<xref:System.Windows.Media.HitTestResultBehavior.Stop> <xref:System.Windows.Media.HitTestResultCallback>從傳回, 以在第一個專案之後停止點擊測試。  
  
 ![視覺化樹狀結構之&#45;]迭置順序的圖表(./media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
視覺化樹狀之疊置順序的圖表  
  
 如果您想要列舉特定點或幾何下的所有視覺物件, 請<xref:System.Windows.Media.HitTestResultBehavior.Continue> <xref:System.Windows.Media.HitTestResultCallback>從傳回。 這表示您可以對其他物件底下的視覺物件進行點擊測試，即使它們完全遭到遮蔽。 如需詳細資訊，請參閱「使用點擊測試結果回呼 」一節中的範例程式碼。  
  
> [!NOTE]
> 透明的視覺物件也可以進行點擊測試。  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>使用預設點擊測試  
 您可以使用<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法來指定要測試的視覺物件和點座標值, 以識別某個點是否在視覺物件的幾何內。 視覺物件參數可在視覺化樹狀結構中識別進行點擊測試搜尋的起點。 如果視覺物件在其幾何包含座標的視覺化樹狀結構中找到, 則會設定為<xref:System.Windows.Media.HitTestResult.VisualHit%2A> <xref:System.Windows.Media.HitTestResult>物件的屬性。 然後<xref:System.Windows.Media.HitTestResult>會<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>從方法傳回。 如果點未包含在您要進行點擊測試的視覺化子樹狀結構中, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> `null`則會傳回。  
  
> [!NOTE]
> 預設點擊測試一定會傳回疊置順序中最上層的物件。 若要識別所有視覺物件，甚至是遭到部分或全部遮蔽的物件，可使用點擊測試結果回呼。  
  
 您當做<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法的 point 參數傳遞的座標值, 必須相對於您進行點擊測試之視覺物件的座標空間。 例如，如果您在父項座標空間的 (100, 100) 定義巢狀視覺物件，然後對位於 (0, 0) 的子視覺物件進行點擊測試，其相當於父項座標空間的 (100, 100)。  
  
 下列程式碼示範如何設定<xref:System.Windows.UIElement>物件的滑鼠事件處理常式, 以用來捕捉用於點擊測試的事件。  
  
 [!code-csharp[HitTestingOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>視覺化樹狀結構如何影響點擊測試  
 視覺化樹狀結構中的起點可決定在物件的點擊測試列舉期間會傳回哪些物件。 如果您有多個想要進行點擊測試的物件，在視覺化樹狀結構中做為起點的視覺物件必須是所有相關物件的通用上階。 例如，如果您想要對下圖中的按鈕元素和繪圖視覺物件進行點擊測試，您必須將視覺樹狀結構中的起點設定為兩者的通用上階。 在此情況下，畫布元素是按鈕元素和繪製視覺物件兩者的通用上階。  
  
 ![視覺化樹狀結構]階層的圖表(./media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
視覺化樹狀階層架構的圖表  
  
> [!NOTE]
> 屬性會取得或設定一個值, 宣告衍生物件<xref:System.Windows.UIElement>是否可以從其呈現內容的某些部分傳回為點擊測試結果。 <xref:System.Windows.UIElement.IsHitTestVisible%2A> 這可讓您選擇性地更改視覺化樹狀結構，以判斷哪一個視覺物件要進行點擊測試。  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>使用點擊測試結果回呼  
 視覺化樹狀結構中的幾何只要包含指定座標值，您就可以列舉所有視覺物件。 這可讓您識別所有視覺物件，甚至是遭到其他視覺物件部分或全部遮蔽的那些物件。 若要在視覺化樹狀結構中列舉視覺物件<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> , 請使用方法搭配點擊測試回呼函數。 當視覺物件中包含您指定的座標值時，系統便會呼叫點擊測試回呼函式。  
  
 在點擊測試結果列舉期間，您不應該執行任何修改視覺化樹狀結構的作業。 在周遊時新增或移除視覺化樹狀結構的物件，可能會導致無法預期的行為。 在<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法傳回之後, 您就可以安全地修改視覺化樹狀結構。 您可能想要提供資料結構 (例如<xref:System.Collections.ArrayList>), 以便在點擊測試結果列舉期間儲存值。  
  
 [!code-csharp[HitTestingOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 點擊測試回呼方法定義您在視覺化樹狀結構中的特定視覺物件上，識別出點擊測試時執行的動作。 執行動作之後, 您會傳回一個<xref:System.Windows.Media.HitTestResultBehavior>值, 決定是否要繼續列舉任何其他視覺物件。  
  
 [!code-csharp[HitTestingOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
> 點擊視覺物件列舉順序是依照疊置順序。 在最上層疊置順序層級的視覺物件是第一個列舉的物件。 任何其他視覺物件都會以遞減的疊置順序層級列舉。 此列舉類型順序對應至視覺效果的轉譯順序。  
  
 您可以藉由<xref:System.Windows.Media.HitTestResultBehavior.Stop>傳回, 在點擊測試回呼函式中隨時停止視覺物件的列舉。  
  
 [!code-csharp[HitTestingOverview#103](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>使用點擊測試篩選回呼  
 您可以使用選用的點擊測試篩選來限制傳遞至點擊測試結果的物件。 這可讓您忽略點擊測試結果中處理時不感興趣的視覺化樹狀結構組件。 若要執行點擊測試篩選器, 您可以定義點擊測試篩選回呼函式, 並在呼叫<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法時, 將它當做參數值傳遞。  
  
 [!code-csharp[HitTestingOverview#104](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 如果您不想要提供選擇性的點擊測試篩選回呼函式, 請傳遞`null`值做為<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法的參數。  
  
 [!code-csharp[HitTestingOverview#105](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![使用點擊測試篩選剪除視覺化樹狀結構](./media/filteredvisualtree-01.png "FilteredVisualTree_01")  
剪除視覺化樹狀結構  
  
 點擊測試篩選回呼函式可讓您列舉呈現內容中包含指定座標的所有視覺效果。 不過，您可能想要忽略點擊測試結果回呼函式中處理時不感興趣的視覺化樹狀結構特定分支。 點擊測試篩選回呼函式的傳回值會決定列舉視覺物件時應採取的動作類型。 例如, 如果您傳回值, <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>則可以從點擊測試結果列舉中移除目前的視覺物件及其子系。 這表示點擊測試結果回呼函式不會在其列舉中看到這些物件。 剪除物件的視覺化樹狀結構會減少在點擊測試結果列舉通過期間的處理量。 在下列程式碼範例中，篩選會略過標籤和其下階並點擊測試所有其他項目。  
  
 [!code-csharp[HitTestingOverview#106](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
> 有時候會呼叫點擊測試篩選回呼，以免未呼叫點擊測試結果回呼。  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>覆寫預設點擊測試  
 您可以藉由覆寫<xref:System.Windows.Media.Visual.HitTestCore%2A>方法來覆寫視覺物件的預設點擊測試支援。 這表示當您<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>叫用方法時, 會呼叫的<xref:System.Windows.Media.Visual.HitTestCore%2A>覆寫執行。 即使座標落在視覺物件的呈現內容外部，還是會在點擊測試落在視覺物件的週框內時呼叫覆寫方法。  
  
 [!code-csharp[HitTestingOverview#107](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 有時候您可能想要對週框和視覺物件的呈現內容進行點擊測試。 藉由使用`PointHitTestParameters`覆寫<xref:System.Windows.Media.Visual.HitTestCore%2A>方法中的參數值做為基底方法<xref:System.Windows.Media.Visual.HitTestCore%2A>的參數, 您可以根據視覺物件的周框矩形來執行動作, 然後對視覺物件的呈現內容。  
  
 [!code-csharp[HitTestingOverview#108](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- <xref:System.Windows.Media.HitTestResult>
- <xref:System.Windows.Media.HitTestResultCallback>
- <xref:System.Windows.Media.HitTestFilterCallback>
- <xref:System.Windows.UIElement.IsHitTestVisible%2A>
- [使用 Drawingvisuals 進行進行點擊測試範例](https://go.microsoft.com/fwlink/?LinkID=159994)
- [使用 Win32 交互操作進行點擊測試範例](https://go.microsoft.com/fwlink/?LinkID=159995)
- [對 Visual 中的幾何進行點擊測試](how-to-hit-test-geometry-in-a-visual.md)
- [使用 Win32 裝載容器進行點擊測試](how-to-hit-test-using-a-win32-host-container.md)
