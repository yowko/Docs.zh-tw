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
ms.openlocfilehash: b3dc71182b7553a429bb17e1888a4108ceb3e286
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="creating-an-ink-input-control"></a>建立筆墨輸入控制項
您可以建立的自訂控制項，動態及靜態呈現筆墨。 這就是，轉譯為使用者繪製筆觸，導致出現 「 資料流程 」 從 tablet 畫筆，並後顯示筆墨會加入至控制項，透過 tablet 畫筆，從剪貼簿 貼上或從檔案載入的筆墨的筆墨。 若要以動態方式呈現筆墨，必須使用您的控制項<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。 若要以靜態方式轉譯筆墨，您必須覆寫手寫筆事件方法 (<xref:System.Windows.UIElement.OnStylusDown%2A>， <xref:System.Windows.UIElement.OnStylusMove%2A>，和<xref:System.Windows.UIElement.OnStylusUp%2A>) 來收集<xref:System.Windows.Input.StylusPoint>資料，建立筆觸，並將其新增<xref:System.Windows.Controls.InkPresenter>（呈現在控制項上的筆墨）。  
  
 本主題包含下列子章節：  
  
-   [如何： 收集手寫筆點資料，並建立筆墨筆劃](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [如何： 啟用您的控制項為接受來自滑鼠輸入](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [將它放在一起](#PuttingItTogether)  
  
-   [使用額外的外掛程式和 DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [結論](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>如何： 收集手寫筆點資料，並建立筆墨筆劃  
 若要建立控制項，收集和管理筆墨筆劃執行下列作業：  
  
1.  自<xref:System.Windows.Controls.Control>或其中一個類別衍生自<xref:System.Windows.Controls.Control>，例如<xref:System.Windows.Controls.Label>。  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2.  新增<xref:System.Windows.Controls.InkPresenter>至類別，並將<xref:System.Windows.Controls.ContentControl.Content%2A>屬性至新<xref:System.Windows.Controls.InkPresenter>。  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3.  附加<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>的<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>至<xref:System.Windows.Controls.InkPresenter>藉由呼叫<xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A>方法，並加入<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>至<xref:System.Windows.UIElement.StylusPlugIns%2A>集合。 這可讓<xref:System.Windows.Controls.InkPresenter>顯示筆墨手寫筆點資料會收集您的控制項。  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4.  覆寫 <xref:System.Windows.UIElement.OnStylusDown%2A> 方法。  在這種方法，擷取手寫筆呼叫<xref:System.Windows.Input.Stylus.Capture%2A>。 擷取手寫筆，您的控制項將會繼續接收<xref:System.Windows.UIElement.StylusMove>和<xref:System.Windows.UIElement.StylusUp>事件即使手寫筆離開控制項的界限。 這不是絕對必要，但可以很好的使用者經驗。 建立新<xref:System.Windows.Input.StylusPointCollection>收集<xref:System.Windows.Input.StylusPoint>資料。 最後，會加入一組初始的<xref:System.Windows.Input.StylusPoint>資料<xref:System.Windows.Input.StylusPointCollection>。  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5.  覆寫<xref:System.Windows.UIElement.OnStylusMove%2A>方法並加入<xref:System.Windows.Input.StylusPoint>資料<xref:System.Windows.Input.StylusPointCollection>您稍早建立的物件。  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6.  覆寫<xref:System.Windows.UIElement.OnStylusUp%2A>方法並建立新<xref:System.Windows.Ink.Stroke>與<xref:System.Windows.Input.StylusPointCollection>資料。 加入新<xref:System.Windows.Ink.Stroke>您建立以<xref:System.Windows.Controls.InkPresenter.Strokes%2A>集合<xref:System.Windows.Controls.InkPresenter>放開手寫筆擷取。  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>如何： 啟用您的控制項為接受來自滑鼠輸入  
 如果將上述的控制項加入至您的應用程式，請執行時，使用滑鼠，做為輸入裝置，您會發現的筆劃不會保存。 保存筆劃滑鼠做的輸入裝置時執行下列作業：  
  
1.  覆寫<xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A>並建立新<xref:System.Windows.Input.StylusPointCollection>發生事件時取得的滑鼠位置，並建立<xref:System.Windows.Input.StylusPoint>使用點資料，然後新增<xref:System.Windows.Input.StylusPoint>至<xref:System.Windows.Input.StylusPointCollection>。  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2.  覆寫 <xref:System.Windows.UIElement.OnMouseMove%2A> 方法。 取得滑鼠位置的事件發生時，並建立<xref:System.Windows.Input.StylusPoint>使用點資料。  新增<xref:System.Windows.Input.StylusPoint>至<xref:System.Windows.Input.StylusPointCollection>您稍早建立的物件。  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3.  覆寫 <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> 方法。  建立新<xref:System.Windows.Ink.Stroke>與<xref:System.Windows.Input.StylusPointCollection>資料，並加入新<xref:System.Windows.Ink.Stroke>您建立以<xref:System.Windows.Controls.InkPresenter.Strokes%2A>集合<xref:System.Windows.Controls.InkPresenter>。  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>將它放在一起  
 下列範例是當使用者使用滑鼠或畫筆收集筆墨的自訂控制項。  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>使用額外的外掛程式和 DynamicRenderers  
 InkCanvas，例如您的自訂控制項可以有自訂<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>和其他<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>物件。 將這些新增到<xref:System.Windows.UIElement.StylusPlugIns%2A>集合。 順序<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>中的物件<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>呈現時，會影響的筆墨外觀。 假設您有<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>呼叫`dynamicRenderer`和自訂<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>呼叫`translatePlugin`，位移的 tablet 畫筆筆墨。 如果`translatePlugin`是第一個<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>中<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>，和`dynamicRenderer`是第二個，當使用者移動畫筆將位移 「 流 」 的筆墨。 如果`dynamicRenderer`這是第一次，並`translatePlugin`是第二，直到使用者取消畫筆筆墨將位移。  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>結論  
 您可以建立會收集並呈現筆墨藉由覆寫手寫筆事件方法的控制項。 藉由建立您自己的控制項，衍生您自己<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類別，並將它們插入到<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>，您可以實作幾乎任何想像數位筆跡與行為。 您可以存取<xref:System.Windows.Input.StylusPoint>產生做為它的資料，讓您有機會自訂<xref:System.Windows.Input.Stylus>輸入，並轉譯為適合您的應用程式畫面上。 因為這類低層級存取<xref:System.Windows.Input.StylusPoint>資料，您可以實作筆墨收集及呈現它以獲得最佳效能，您的應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [筆跡進階處理](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [存取和管理畫筆輸入](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
