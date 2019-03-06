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
ms.openlocfilehash: 8089c857d2406f8cfb357ba2efe188ad84605541
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377021"
---
# <a name="the-ink-threading-model"></a>筆墨執行緒模型
Tablet PC 上的好處之一是筆墨的，覺得有許多撰寫使用一般紙筆。  若要這麼做，tablet 畫筆會收集在更高的速率比滑鼠，並為使用者寫入會轉譯筆跡輸入的資料。  應用程式的使用者介面 (UI) 執行緒不足，無法用來收集畫筆資料和呈現筆墨，因為它可能會被封鎖。  若要解決，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時使用者寫入筆跡，應用程式會使用兩個額外的執行緒。  
  
 下列清單描述參與收集和呈現數位筆跡執行緒：  
  
-   畫筆執行緒的執行緒，會將手寫筆的輸入。  （事實上，這是執行緒集區，但本主題會將它稱為畫筆執行緒）。  
  
-   應用程式使用者介面執行緒控制的應用程式的使用者介面執行緒。  
  
-   動態呈現執行緒-之執行緒的轉譯筆跡時使用者繪製筆劃。 動態呈現執行緒會呈現其他 UI 項目，應用程式執行緒以外的不同視窗 Presentation Foundation 中所述[執行緒模型](threading-model.md)。  
  
 筆跡的模型是相同的應用程式使用是否<xref:System.Windows.Controls.InkCanvas>或自訂控制項中的一個類似[建立筆墨輸入控制項](creating-an-ink-input-control.md)。  雖然本主題討論執行緒的形式<xref:System.Windows.Controls.InkCanvas>，當您建立自訂控制項時，適用相同的概念。  
  
## <a name="threading-overview"></a>執行緒處理概觀  
 下圖說明執行緒模型，當使用者繪製筆劃時：  
  
 ![繪製筆觸期間的執行緒模型。](./media/inkthreading-drawingink.png "InkThreading_DrawingInk")  
  
1.  發生使用者繪製筆劃時的動作  
  
    1.  當使用者繪製筆劃時，手寫筆點有畫筆執行緒上。  手寫筆外掛程式，包括<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>，接受畫筆執行緒上的手寫筆點，並有機會修改它們之前<xref:System.Windows.Controls.InkCanvas>接收它們。  
  
    2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>呈現的動態呈現執行緒上的手寫筆點。 這會發生於與上一個步驟相同的時間。  
  
    3.  <xref:System.Windows.Controls.InkCanvas>接收在 UI 執行緒上的手寫筆點。  
  
2.  使用者結束筆劃後發生的動作  
  
    1.  當使用者完成繪製的筆劃<xref:System.Windows.Controls.InkCanvas>會建立<xref:System.Windows.Ink.Stroke>物件，並將它加入至<xref:System.Windows.Controls.InkPresenter>，會以靜態方式呈現。  
  
    2.  UI 執行緒警示<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>靜態轉譯筆劃，因此<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>筆劃其視覺表示法中移除。  
  
## <a name="ink-collection-and-stylus-plug-ins"></a>筆跡收集和手寫筆外掛程式  
 每個<xref:System.Windows.UIElement>具有<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>中的物件<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>接收，且可修改的畫筆執行緒上的手寫筆點。 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>物件接收根據其順序中的手寫筆點<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。  
  
 下圖說明假設性情況其中<xref:System.Windows.UIElement.StylusPlugIns%2A>的集合<xref:System.Windows.UIElement>包含`stylusPlugin1`，則<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>，和`stylusPlugin2`，依此順序。  
  
 ![手寫筆外掛程式的順序會影響輸出。](./media/inkthreading-pluginorder.png "InkThreading_PluginOrder")  
  
 在上圖中，會發生下列行為：  
  
1.  `StylusPlugin1` 修改 x 值和 y。  
  
2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 接收已修改的手寫筆的點，並轉譯成動態呈現執行緒上。  
  
3.  `StylusPlugin2` 接收已修改的手寫筆的點，並進一步修改 x 值和 y。  
  
4.  應用程式會收集手寫筆的點，並當使用者完成筆劃，靜態轉譯筆劃。  
  
 假設`stylusPlugin1`限制的矩形的手寫筆的點和`stylusPlugin2`轉譯右邊的手寫筆點。  在前一個案例中，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>接收限制的手寫筆的點，但未翻譯的手寫筆的點。  當使用者繪製筆劃時，筆劃轉譯的矩形界限內，但筆劃不會出現轉譯，直到使用者拿起畫筆。  
  
### <a name="performing-operations-with-a-stylus-plug-in-on-the-ui-thread"></a>使用手寫筆外掛程式在 UI 執行緒上執行作業  
 畫筆執行緒上無法執行精確的點擊測試，因為有些項目偶爾可能會收到其他項目的手寫筆輸入。 如果您需要確定輸入執行作業之前已正確傳遞，訂閱，並執行中的作業<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>， <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>，或<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A>方法。 執行精確的點擊測試之後，應用程式執行緒會叫用這些方法。 若要訂閱這些方法，呼叫<xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A>發生於畫筆執行緒的方法中的方法。  
  
 下圖說明畫筆執行緒與 UI 執行緒相關的手寫筆事件之間的關係<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>。  
  
 ![筆墨執行緒模型&#40;UI 和 Pen&#41;](./media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")  
  
## <a name="rendering-ink"></a>呈現筆墨  
 當使用者繪製筆劃，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>會轉譯在個別執行緒上的筆墨，因此 「 順著 」 從畫筆甚至是在 UI 執行緒忙碌時顯示的筆墨。  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>動態呈現執行緒上建置視覺化樹狀結構，因為它會收集手寫筆點。  當使用者完成筆劃，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>會要求應用程式會在下一步 的轉譯階段時收到通知。  應用程式完成下一步 的呈現階段之後,<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>清除其視覺化樹狀結構。  下圖說明此程序。  
  
 ![筆跡執行緒圖表](./media/inkthreading-visualtree.png "InkThreading_VisualTree")  
  
1.  使用者會開始筆劃。  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>建立視覺化樹狀結構。  
  
2.  使用者繪製筆劃。  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>建置視覺化樹狀結構。  
  
3.  筆劃端點使用者。  
  
    1.  <xref:System.Windows.Controls.InkPresenter>將其視覺化樹狀結構中的筆劃。  
  
    2.  媒體整合層 (.MIL) 靜態轉譯筆劃。  
  
    3.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>清除視覺效果。
