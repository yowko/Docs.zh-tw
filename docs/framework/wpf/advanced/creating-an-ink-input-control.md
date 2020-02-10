---
title: 建立筆墨輸入控制項
ms.date: 03/30/2017
helpviewer_keywords:
- ink strokes [WPF], managing
- managing ink strokes [WPF]
- ink input control [WPF]
- input from mouse [WPF], accepting
- mouse input [WPF], accepting
- ink [WPF], rendering
- ink strokes [WPF], collecting
- rendering ink [WPF]
- collecting ink strokes [WPF]
- DynamicRenderer objects [WPF]
- StylusPlugIn objects [WPF]
ms.assetid: c31f3a67-cb3f-4ded-af9e-ed21f6575b26
ms.openlocfilehash: 98b2abf813a232e36b80683254174b12b97659bb
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095212"
---
# <a name="creating-an-ink-input-control"></a>建立筆墨輸入控制項
您可以建立動態和靜態呈現筆墨的自訂控制項。 也就是說，當使用者繪製筆劃時，會呈現筆墨，使筆墨從 tablet 畫筆顯示為「flow」，並在新增至控制項之後，透過 tablet 畫筆、從剪貼簿貼上或從檔案載入來顯示筆墨。 若要以動態方式呈現筆墨，您的控制項必須使用 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。 若要以靜態方式轉譯筆墨，您必須覆寫手寫筆事件方法（<xref:System.Windows.UIElement.OnStylusDown%2A>、<xref:System.Windows.UIElement.OnStylusMove%2A>和 <xref:System.Windows.UIElement.OnStylusUp%2A>）以收集 <xref:System.Windows.Input.StylusPoint> 資料、建立筆觸，並將其加入至 <xref:System.Windows.Controls.InkPresenter> （這會在控制項上呈現筆墨）。  
  
 本主題包含下列各小節：  
  
- [如何：收集手寫筆點資料並建立筆墨筆劃](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [如何：讓您的控制項接受來自滑鼠的輸入](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [將它放在一起](#PuttingItTogether)  
  
- [使用其他外掛程式和 DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [結論](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>如何：收集手寫筆點資料並建立筆墨筆劃  
 若要建立可收集和管理筆墨筆觸的控制項，請執行下列動作：  
  
1. 從 <xref:System.Windows.Controls.Control> 或衍生自 <xref:System.Windows.Controls.Control>的其中一個類別（例如 <xref:System.Windows.Controls.Label>），衍生一個類別。  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. 將 <xref:System.Windows.Controls.InkPresenter> 新增至類別，並將 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性設定為新的 <xref:System.Windows.Controls.InkPresenter>。  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. 藉由呼叫 <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> 方法，將 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> 附加至 <xref:System.Windows.Controls.InkPresenter>，並將 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 新增至 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合。 這可讓 <xref:System.Windows.Controls.InkPresenter> 在您的控制項收集手寫筆點資料時顯示筆墨。  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. 覆寫 <xref:System.Windows.UIElement.OnStylusDown%2A> 方法。  在此方法中，使用 <xref:System.Windows.Input.Stylus.Capture%2A>的呼叫來捕捉手寫筆。 藉由捕捉手寫筆，即使手寫筆離開控制項的界限，您的控制項仍會繼續接收 <xref:System.Windows.UIElement.StylusMove> 和 <xref:System.Windows.UIElement.StylusUp> 事件。 這並不是絕對必要，但幾乎總是希望獲得良好的使用者體驗。 建立新的 <xref:System.Windows.Input.StylusPointCollection> 以收集 <xref:System.Windows.Input.StylusPoint> 的資料。 最後，將一組初始的 <xref:System.Windows.Input.StylusPoint> 資料新增至 <xref:System.Windows.Input.StylusPointCollection>。  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. 覆寫 <xref:System.Windows.UIElement.OnStylusMove%2A> 方法，並將 <xref:System.Windows.Input.StylusPoint> 資料新增至您稍早建立的 <xref:System.Windows.Input.StylusPointCollection> 物件。  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. 覆寫 <xref:System.Windows.UIElement.OnStylusUp%2A> 方法，並使用 <xref:System.Windows.Input.StylusPointCollection> 資料建立新的 <xref:System.Windows.Ink.Stroke>。 將您建立的新 <xref:System.Windows.Ink.Stroke> 新增至 <xref:System.Windows.Controls.InkPresenter> 的 <xref:System.Windows.Controls.InkPresenter.Strokes%2A> 集合，併發行手寫筆捕捉。  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>如何：讓您的控制項接受來自滑鼠的輸入  
 如果您將上述控制項新增至應用程式、加以執行，並使用滑鼠做為輸入裝置，您會注意到筆觸不會保存。 若要在使用滑鼠作為輸入裝置時保存筆劃，請執行下列動作：  
  
1. 覆寫 <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> 並建立新 <xref:System.Windows.Input.StylusPointCollection> 取得事件發生時的滑鼠位置，並使用點資料建立 <xref:System.Windows.Input.StylusPoint>，並將 <xref:System.Windows.Input.StylusPoint> 新增至 <xref:System.Windows.Input.StylusPointCollection>。  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. 覆寫 <xref:System.Windows.UIElement.OnMouseMove%2A> 方法。 取得事件發生時的滑鼠位置，並使用點資料建立 <xref:System.Windows.Input.StylusPoint>。  將 <xref:System.Windows.Input.StylusPoint> 新增至您稍早建立的 <xref:System.Windows.Input.StylusPointCollection> 物件。  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. 覆寫 <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> 方法。  建立具有 <xref:System.Windows.Input.StylusPointCollection> 資料的新 <xref:System.Windows.Ink.Stroke>，並將您建立的新 <xref:System.Windows.Ink.Stroke> 新增至 <xref:System.Windows.Controls.InkPresenter>的 <xref:System.Windows.Controls.InkPresenter.Strokes%2A> 集合。  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>將它放在一起  
 下列範例是自訂控制項，會在使用者使用滑鼠或畫筆時收集筆跡。  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>使用其他外掛程式和 DynamicRenderers  
 如同 InkCanvas，您的自訂控制項可以有自訂 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 和額外的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 物件。 將這些新增至 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合。 在 <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> 中，<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 物件的順序會影響筆跡呈現時的外觀。 假設您有一個稱為 `dynamicRenderer` 的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>，以及一個自訂 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>，稱為 `translatePlugin`，它會從 tablet 畫筆中位移筆跡。 如果 `translatePlugin` 是 <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>中的第一個 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>，而 `dynamicRenderer` 是第二個，則「流程」的筆墨會隨著使用者移動畫筆而位移。 如果 `dynamicRenderer` 是第一個，而 `translatePlugin` 是第二個，則在使用者提起畫筆之前，筆跡不會位移。  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>結論  
 您可以藉由覆寫手寫筆事件方法，建立可收集和呈現筆墨的控制項。 藉由建立您自己的控制項、衍生您自己的 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 類別，並將它們插入 <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>，您就可以使用數位筆跡來執行幾乎所有的行為想像得到。 您可以存取所產生的 <xref:System.Windows.Input.StylusPoint> 資料，讓您有機會自訂 <xref:System.Windows.Input.Stylus> 輸入，並在畫面上將其轉譯為適用于您的應用程式。 因為您有 <xref:System.Windows.Input.StylusPoint> 資料的低層級存取權，所以您可以執行筆墨集合，並以最佳的應用程式效能來呈現它。  
  
## <a name="see-also"></a>另請參閱

- [筆跡進階處理](advanced-ink-handling.md)
- [存取和操作手寫筆輸入](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))
