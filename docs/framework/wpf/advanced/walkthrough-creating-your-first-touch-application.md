---
title: 逐步解說：建立您的第一個觸控應用程式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
ms.openlocfilehash: a915b8e238550eb3d9c1bcbe72d0d05a83a8312c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605811"
---
# <a name="walkthrough-creating-your-first-touch-application"></a>逐步解說：建立您的第一個觸控應用程式
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 讓應用程式回應觸控。 比方說，您可以使用其中一個互動應用程式或更多根手指觸控感應裝置，例如本逐步解說中建立的應用程式，可讓使用者移動觸控螢幕上調整大小，或使用觸控旋轉單一物件。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
- Visual Studio。  
  
- 接受輸入，例如觸控螢幕，可支援 Windows Touch 的觸控裝置。  
  
 此外，您應該有基本的了解如何建立應用程式中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，尤其是如何訂閱和處理事件。 如需詳細資訊，請參閱[逐步解說：我第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
## <a name="creating-the-application"></a>建立應用程式  
  
#### <a name="to-create-the-application"></a>若要建立應用程式  
  
1. 在 Visual Basic 或 Visual C# 中，建立名為 `BasicManipulation` 的新 WPF 應用程式專案。 如需詳細資訊，請參閱[逐步解說：我第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
2. MainWindow.xaml 的內容取代為下列 XAML。  
  
     此標記會建立簡單的應用程式，其中包含紅色<xref:System.Windows.Shapes.Rectangle>上<xref:System.Windows.Controls.Canvas>。 <xref:System.Windows.UIElement.IsManipulationEnabled%2A>屬性<xref:System.Windows.Shapes.Rectangle>設為 true，因此它會接收操作事件。 應用程式訂閱<xref:System.Windows.UIElement.ManipulationStarting>， <xref:System.Windows.UIElement.ManipulationDelta>，和<xref:System.Windows.UIElement.ManipulationInertiaStarting>事件。 這些事件包含邏輯來移動<xref:System.Windows.Shapes.Rectangle>使用者時操作它。  
  
     [!code-xaml[BasicManipulation#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3. 如果您使用 Visual Basic 中，在 MainWindow.xaml 的第一行中，取代`x:Class="BasicManipulation.MainWindow"`與`x:Class="MainWindow"`。  
  
4. 在 `MainWindow`類別中，新增下列<xref:System.Windows.UIElement.ManipulationStarting>事件處理常式。  
  
     <xref:System.Windows.UIElement.ManipulationStarting>就會發生事件時[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]偵測到該觸控輸入開始操作的物件。 程式碼會指定操作位置應該是相對於<xref:System.Windows.Window>藉由設定<xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>屬性。  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]

5. 在 `MainWindow`類別中，新增下列<xref:System.Windows.Input.ManipulationDelta>事件處理常式。

     <xref:System.Windows.Input.ManipulationDelta>觸控輸入變更位置，並可於操作期間發生多次時，就會發生事件。 手指引發之後，也會發生此事件。 例如，如果使用者的螢幕上拖曳手指<xref:System.Windows.Input.ManipulationDelta>手指移事件會發生一次。 當使用者引發從畫面中，手指<xref:System.Windows.Input.ManipulationDelta>事件持續發生，模擬慣性。

     程式碼會套用<xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A>要<xref:System.Windows.UIElement.RenderTransform%2A>的<xref:System.Windows.Shapes.Rectangle>移動它，當使用者移動觸控輸入。 它也會檢查是否<xref:System.Windows.Shapes.Rectangle>超出範圍<xref:System.Windows.Window>在慣性期間的事件發生時。 因此，應用程式呼叫如果<xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType>方法以結束操作。

     [!code-csharp[BasicManipulation#ManipulationDelta](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]

6. 在 `MainWindow`類別中，新增下列<xref:System.Windows.UIElement.ManipulationInertiaStarting>事件處理常式。

     <xref:System.Windows.UIElement.ManipulationInertiaStarting>事件發生於使用者引發從畫面的所有根手指。 程式碼設定的初始速度和移動、 擴充和旋轉該矩形的減速。

     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]

7. 建置並執行專案。

     您應該會看到視窗中顯示為紅色方形。

## <a name="testing-the-application"></a>測試應用程式
 若要測試應用程式，請嘗試下列操作。 請注意，您可以多個下列其中之一在相同的時間。

- 若要移動<xref:System.Windows.Shapes.Rectangle>，將手指放<xref:System.Windows.Shapes.Rectangle>並將手指移動螢幕上。

- 若要調整大小<xref:System.Windows.Shapes.Rectangle>，將兩隻手指放在<xref:System.Windows.Shapes.Rectangle>，然後將手指，更接近手指或分開彼此。

- 若要旋轉<xref:System.Windows.Shapes.Rectangle>，將兩隻手指放在<xref:System.Windows.Shapes.Rectangle>並旋轉手指。

 若要使慣性，快速將引發手指已離開螢幕當您執行先前的操作。 <xref:System.Windows.Shapes.Rectangle>會繼續移動、 調整大小或旋轉幾秒鐘的時間之前就會停止。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>