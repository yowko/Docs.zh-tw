---
title: 筆墨執行緒模型
ms.date: 03/30/2017
helpviewer_keywords:
- application user interface thread [WPF]
- stylus plug-in
- ink threading model [WPF]
- ink [WPF], rendering
- pen thread [WPF]
- threading model [WPF]
- rendering ink [WPF]
- dynamic rendering thread [WPF]
- ink collection plug-in
- plug-ins [WPF], for ink
ms.assetid: c85fcad1-cb50-4431-847c-ac4145a35c89
ms.openlocfilehash: cc0ff8a2345bd945dd2fffdfda80f00e1ab99c67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547875"
---
# <a name="the-ink-threading-model"></a>筆墨執行緒模型
其中一個 Tablet PC 上的優點是筆墨的，它感覺更像是撰寫使用一般紙筆。  若要達成此目的，tablet 畫筆會收集輸入的資料，以更高的速率超過沒有滑鼠，而且會筆跡轉譯成使用者寫入。  應用程式的使用者介面 (UI) 執行緒不足，無法收集畫筆資料及呈現筆墨，因為它可能會被封鎖。  若要解決此，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用者撰寫的筆墨時，應用程式會使用兩個額外的執行緒。  
  
 下列清單描述使用的收集和呈現數位筆跡執行緒：  
  
-   畫筆執行緒會將手寫筆的執行緒。  （事實上，這是在執行緒集區中，但本主題是指其畫筆執行緒）。  
  
-   應用程式使用者介面執行緒控制應用程式的使用者介面執行緒。  
  
-   動態呈現執行緒： 呈現時使用者筆墨執行緒繪製筆觸。 視窗 Presentation Foundation 中所述的動態呈現執行緒會呈現其他 UI 項目，應用程式執行緒以外的不同[執行緒模型](../../../../docs/framework/wpf/advanced/threading-model.md)。  
  
 不論應用程式使用筆跡的模型都相同<xref:System.Windows.Controls.InkCanvas>或自訂控制項中的一個類似[建立筆跡輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)。  雖然本主題討論的執行緒<xref:System.Windows.Controls.InkCanvas>，相同的概念適用於當您建立自訂控制項。  
  
## <a name="threading-overview"></a>執行緒處理概觀  
 下圖說明的執行緒模型，當使用者繪製筆觸時：  
  
 ![繪製筆觸期間的執行緒模型。] (../../../../docs/framework/wpf/advanced/media/inkthreading-drawingink.png "InkThreading_DrawingInk")  
  
1.  使用者繪製筆觸時發生的動作  
  
    1.  當使用者繪製筆觸時，手寫筆的點有畫筆執行緒上。  手寫筆外掛程式，包括<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>、 接受手寫筆上的點畫筆執行緒並有機會修改過他們的<xref:System.Windows.Controls.InkCanvas>接收它們。  
  
    2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>呈現手寫筆的點上的動態呈現執行緒。 這會發生在上一個步驟相同的時間。  
  
    3.  <xref:System.Windows.Controls.InkCanvas>接收手寫筆在 UI 執行緒上的點。  
  
2.  發生使用者結束筆觸動作  
  
    1.  當使用者完成繪製筆觸<xref:System.Windows.Controls.InkCanvas>建立<xref:System.Windows.Ink.Stroke>物件，並將它加入至<xref:System.Windows.Controls.InkPresenter>，它以靜態方式呈現。  
  
    2.  UI 執行緒警示<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>筆觸以靜態方式轉譯，所以<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>筆劃其視覺表示法中移除。  
  
## <a name="ink-collection-and-stylus-plug-ins"></a>集合筆跡和手寫筆外掛程式  
 每個<xref:System.Windows.UIElement>具有<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>中的物件<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>接收且可修改手寫筆上的點畫筆執行緒。 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>物件接收的順序根據手寫筆的點<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。  
  
 下列圖表說明在假設性的情況下其中<xref:System.Windows.UIElement.StylusPlugIns%2A>集合<xref:System.Windows.UIElement>包含`stylusPlugin1`、 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>，和`stylusPlugin2`，依此順序。  
  
 ![Stylusplugin 效果順序會影響輸出。] (../../../../docs/framework/wpf/advanced/media/inkthreading-pluginorder.png "InkThreading_PluginOrder")  
  
 在上圖中，會發生下列行為：  
  
1.  `StylusPlugin1` 修改的值，x 和 y。  
  
2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 接收已修改的手寫筆的點，並呈現它們的動態呈現執行緒上。  
  
3.  `StylusPlugin2` 接收已修改的手寫筆的點，並進一步修改的 x 值和 y。  
  
4.  應用程式收集手寫筆的點，並當使用者完成筆劃，以靜態方式呈現筆觸。  
  
 假設`stylusPlugin1`將手寫筆的點限制為矩形和`stylusPlugin2`轉譯手寫筆右邊的點。  在前述案例中，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>接收受限制的手寫筆的點，但未翻譯的手寫筆的點。  當使用者繪製筆觸時，筆劃轉譯矩形界限內，但看起來轉譯直到使用者取消畫筆筆觸。  
  
### <a name="performing-operations-with-a-stylus-plug-in-on-the-ui-thread"></a>使用手寫筆外掛程式在 UI 執行緒上執行作業  
 無法在畫筆的執行緒上執行精確的點擊測試，因為某些項目可能有時會接收其他項目的手寫筆輸入。 如果您需要確定輸入執行作業之前已正確傳遞，訂閱，並執行中的作業<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>， <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>，或<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A>方法。 執行精確的點擊測試之後，這些方法會叫用由應用程式執行緒。 若要訂閱這些方法，請呼叫<xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A>發生於畫筆執行緒的方法中的方法。  
  
 下圖說明畫筆執行緒與 UI 執行緒，相對於的手寫筆事件之間的關聯性<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>。  
  
 ![筆跡執行緒模型&#40;UI 和 Pen&#41;](../../../../docs/framework/wpf/advanced/media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")  
  
## <a name="rendering-ink"></a>呈現筆墨  
 當使用者繪製筆觸，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>讓筆跡出現 「 資料流程 」 畫筆從 UI 執行緒忙碌，即使呈現不同的執行緒上的筆墨。  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>視覺化樹狀結構建置動態呈現執行緒上，因為它會收集手寫筆的點。  當使用者完成筆劃<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>詢問應用程式會在下一步的轉譯階段會收到通知。  應用程式完成下一步的呈現階段之後<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>清除其視覺化樹狀結構。  下圖說明此程序。  
  
 ![筆跡執行緒圖表](../../../../docs/framework/wpf/advanced/media/inkthreading-visualtree.png "InkThreading_VisualTree")  
  
1.  使用者開始筆觸。  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>建立的視覺化樹狀結構。  
  
2.  使用者繪製筆觸。  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>建置的視覺化樹狀。  
  
3.  在使用者結束筆觸。  
  
    1.  <xref:System.Windows.Controls.InkPresenter>筆劃將其視覺化樹狀結構。  
  
    2.  媒體整合層級 （軍事） 以靜態方式呈現筆劃。  
  
    3.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>清除視覺效果。
