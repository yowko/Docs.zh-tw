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
ms.openlocfilehash: 94a97c30179f7a8231426e31b8cacc364629ffc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548347"
---
# <a name="walkthrough-creating-your-first-touch-application"></a>逐步解說：建立您的第一個觸控應用程式
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓應用程式要碰觸的回應。 例如，您可以使用其中一個應用程式與互動或觸控式裝置，例如本逐步解說建立的應用程式，可讓使用者移動，觸控螢幕上的多個指調整大小或旋轉使用觸控的單一物件。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].  
  
-   Windows 7。  
  
-   接受觸控輸入，例如觸控螢幕，可支援 Windows 觸控裝置。  
  
 此外，您應該有基本了解如何建立應用程式中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，特別是如何訂閱和處理事件。 如需詳細資訊，請參閱[逐步解說： 第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
## <a name="creating-the-application"></a>建立應用程式  
  
#### <a name="to-create-the-application"></a>若要建立應用程式  
  
1.  在 Visual Basic 或 Visual C# 中，建立名為 `BasicManipulation` 的新 WPF 應用程式專案。 如需詳細資訊，請參閱[如何：建立新的 WPF 應用程式專案](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。  
  
2.  以下列 XAML 取代 MainWindow.xaml 的內容。  
  
     這個標記會建立簡單的應用程式，其中包含紅色<xref:System.Windows.Shapes.Rectangle>上<xref:System.Windows.Controls.Canvas>。 <xref:System.Windows.UIElement.IsManipulationEnabled%2A>屬性<xref:System.Windows.Shapes.Rectangle>設為 true，使其將接收管理事件。 應用程式訂閱<xref:System.Windows.UIElement.ManipulationStarting>， <xref:System.Windows.UIElement.ManipulationDelta>，和<xref:System.Windows.UIElement.ManipulationInertiaStarting>事件。 這些事件包含邏輯，以移動<xref:System.Windows.Shapes.Rectangle>使用者時操作它。  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  如果您使用 Visual Basic 中，在 MainWindow.xaml 的第一行中，取代`x:Class="BasicManipulation.MainWindow"`與`x:Class="MainWindow"`。  
  
4.  在`MainWindow`類別，加入下列<xref:System.Windows.UIElement.ManipulationStarting>事件處理常式。  
  
     <xref:System.Windows.UIElement.ManipulationStarting>就會發生事件時[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]偵測到該觸控輸入開始操作的物件。 程式碼會指定位置的操作應該相對於<xref:System.Windows.Window>藉由設定<xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>屬性。  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  在`MainWindow`類別，加入下列<xref:System.Windows.Input.ManipulationDelta>事件處理常式。  
  
     <xref:System.Windows.Input.ManipulationDelta>觸控輸入變更位置，並可以操作期間發生多次時，就會發生事件。 引發手指之後，也會發生此事件。 例如，如果使用者跨 畫面中，拖曳手指<xref:System.Windows.Input.ManipulationDelta>事件與手指移動出現多次。 當使用者引發畫面上，從手指<xref:System.Windows.Input.ManipulationDelta>模擬慣性持續發生的事件。  
  
     程式碼適用於<xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A>至<xref:System.Windows.UIElement.RenderTransform%2A>的<xref:System.Windows.Shapes.Rectangle>來移動它，當使用者移動觸控輸入。 它也會檢查是否<xref:System.Windows.Shapes.Rectangle>超出範圍<xref:System.Windows.Window>慣性期間發生的事件。 因此，應用程式呼叫如果<xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType>方法來中止操作。  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  在`MainWindow`類別，加入下列<xref:System.Windows.UIElement.ManipulationInertiaStarting>事件處理常式。  
  
     <xref:System.Windows.UIElement.ManipulationInertiaStarting>事件發生於使用者引發所有隻手指放在畫面上。 此程式碼設定的初始速度和減速移動、 擴充，以及矩形的旋轉。  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  建置並執行專案。  
  
     您應該會看到在視窗中顯示為紅色方形。  
  
## <a name="testing-the-application"></a>測試應用程式  
 若要測試應用程式，請嘗試下列操作。 請注意，您可以多個下列其中之一在相同的時間。  
  
-   若要移動<xref:System.Windows.Shapes.Rectangle>，打手指<xref:System.Windows.Shapes.Rectangle>和手指移動螢幕上。  
  
-   若要調整大小<xref:System.Windows.Shapes.Rectangle>，兩隻手指放置於<xref:System.Windows.Shapes.Rectangle>，然後將手指接近一起或彼此相距較遠。  
  
-   若要旋轉<xref:System.Windows.Shapes.Rectangle>，兩隻手指放置於<xref:System.Windows.Shapes.Rectangle>和旋轉的指周圍彼此。  
  
 若要使慣性，快速引發從螢幕手指與您執行先前的操作。 <xref:System.Windows.Shapes.Rectangle>移動、 調整大小或旋轉數秒鐘，它會停止之前會繼續。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>
