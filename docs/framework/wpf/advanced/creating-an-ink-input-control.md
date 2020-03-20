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
ms.openlocfilehash: 394318488b0afb8e043389e0abc3f51dce8604c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186287"
---
# <a name="creating-an-ink-input-control"></a>建立筆墨輸入控制項
您可以創建動態和靜態渲染墨蹟的自訂控制項。 也就是說，在使用者繪製筆劃時渲染墨蹟，導致墨蹟從 Tablet 筆中顯示為"流"，並在墨蹟添加到控制項後顯示墨蹟，通過 Tablet 筆、從剪貼簿粘貼或從檔載入。 要動態渲染墨蹟，控制項必須使用<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。 要靜態渲染墨蹟，必須重寫手寫筆事件方法<xref:System.Windows.UIElement.OnStylusDown%2A>（和<xref:System.Windows.UIElement.OnStylusMove%2A> <xref:System.Windows.UIElement.OnStylusUp%2A>） 以收集資料<xref:System.Windows.Input.StylusPoint>、創建描邊並將它們添加到 （<xref:System.Windows.Controls.InkPresenter>該方法在控制項上呈現墨蹟）。  
  
 本主題包含下列子章節：  
  
- [如何：收集手寫筆點資料並創建墨蹟描邊](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [如何：使控制項接受來自滑鼠的輸入](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [將它放在一起](#PuttingItTogether)  
  
- [使用其他外掛程式和動態渲染器](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [結論](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>如何：收集手寫筆點資料並創建墨蹟描邊  
 要創建收集和管理墨蹟描邊的控制項，請執行以下操作：  
  
1. 派生來自<xref:System.Windows.Controls.Control>或 派生自<xref:System.Windows.Controls.Control>的類之一，<xref:System.Windows.Controls.Label>例如 。  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. 將<xref:System.Windows.Controls.InkPresenter>add 添加到 類<xref:System.Windows.Controls.ContentControl.Content%2A>並將 屬性設置為<xref:System.Windows.Controls.InkPresenter>新 。  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. <xref:System.Windows.Controls.InkPresenter>通過調用<xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A>方法將<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer><xref:System.Windows.UIElement.StylusPlugIns%2A><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>的 將 的<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>附加到 ，並將 添加到集合中。 這允許 在<xref:System.Windows.Controls.InkPresenter>控制項收集手寫筆點資料時顯示墨蹟。  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. 覆寫 <xref:System.Windows.UIElement.OnStylusDown%2A> 方法。  在此方法中，使用 調用<xref:System.Windows.Input.Stylus.Capture%2A>捕獲手寫筆。 通過捕獲手寫筆，即使手寫筆離開控制項的邊界，您的控制項仍<xref:System.Windows.UIElement.StylusMove>將繼續<xref:System.Windows.UIElement.StylusUp>接收和事件。 這不是嚴格的強制性，但幾乎總是需要良好的使用者體驗。 創建新資料<xref:System.Windows.Input.StylusPointCollection>以收集資料<xref:System.Windows.Input.StylusPoint>。 最後，將初始資料集<xref:System.Windows.Input.StylusPoint>添加到 。 <xref:System.Windows.Input.StylusPointCollection>  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. 重寫<xref:System.Windows.UIElement.OnStylusMove%2A>方法並將<xref:System.Windows.Input.StylusPoint>資料添加到之前創建<xref:System.Windows.Input.StylusPointCollection>的物件。  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. 重寫方法<xref:System.Windows.UIElement.OnStylusUp%2A>，使用<xref:System.Windows.Ink.Stroke><xref:System.Windows.Input.StylusPointCollection>資料創建新資料。 將您創建<xref:System.Windows.Ink.Stroke>的新樣式添加到<xref:System.Windows.Controls.InkPresenter.Strokes%2A><xref:System.Windows.Controls.InkPresenter>和 釋放手寫筆捕獲的集合中。  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>如何：使控制項接受來自滑鼠的輸入  
 如果將前面的控制項添加到應用程式，運行它，並將滑鼠用作輸入裝置，您會注意到筆劃不會持久化。 要在將滑鼠用作輸入裝置時保留筆劃，請執行以下操作：  
  
1. 重寫<xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A>並創建新<xref:System.Windows.Input.StylusPointCollection>的"在事件發生時獲取滑鼠的位置"，並使用點資料創建<xref:System.Windows.Input.StylusPoint>一個 ，並將 添加到<xref:System.Windows.Input.StylusPoint>。 <xref:System.Windows.Input.StylusPointCollection>  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. 覆寫 <xref:System.Windows.UIElement.OnMouseMove%2A> 方法。 在事件發生時獲取滑鼠的位置，並使用點資料創建一個<xref:System.Windows.Input.StylusPoint>。  將<xref:System.Windows.Input.StylusPoint>添加到之前<xref:System.Windows.Input.StylusPointCollection>創建的物件。  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. 覆寫 <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> 方法。  <xref:System.Windows.Ink.Stroke>使用<xref:System.Windows.Input.StylusPointCollection>資料創建新資料，並將創建<xref:System.Windows.Ink.Stroke><xref:System.Windows.Controls.InkPresenter.Strokes%2A>的新添加到 集合中。 <xref:System.Windows.Controls.InkPresenter>  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>
## <a name="putting-it-together"></a>將它放在一起  
 下面的示例是一個自訂控制項，當使用者使用滑鼠或筆時收集墨蹟。  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>使用其他外掛程式和動態渲染器  
 與 InkCanvas 一樣，自訂控制項可以<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>具有自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>物件和其他物件。 將這些添加到集合中<xref:System.Windows.UIElement.StylusPlugIns%2A>。 中<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>的物件的順序<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>會影響墨蹟在渲染時的外觀。 假設您有一個<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>已`dynamicRenderer`調用的自訂<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>項`translatePlugin`，該調用的自訂項會偏移 Tablet 筆中的墨蹟。 如果`translatePlugin`是第一<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>個，<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>是第`dynamicRenderer`二個，則當使用者移動筆時，"流動"的墨蹟將被偏移。 如果`dynamicRenderer`是第一，是第`translatePlugin`二，則在使用者抬起筆之前，墨蹟不會偏移。  
  
<a name="AdvancedInkHandling_Conclusion"></a>
## <a name="conclusion"></a>結論  
 您可以創建通過重寫手寫筆事件方法收集和呈現墨蹟的控制項。 通過創建自己的控制項、派生自己的<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類並將它們插入 到 中<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>，您可以實現幾乎任何使用數位筆跡可以想像到的行為。 您可以在生成<xref:System.Windows.Input.StylusPoint>資料時訪問資料，從而有機會自訂<xref:System.Windows.Input.Stylus>輸入並在螢幕上根據需要呈現它，以適合您的應用程式。 由於您對<xref:System.Windows.Input.StylusPoint>資料具有如此低級別的訪問，因此可以實現墨蹟收集，並針對應用程式以最佳性能呈現它。  
  
## <a name="see-also"></a>另請參閱

- [筆墨進階處理](advanced-ink-handling.md)
- [訪問和操作筆輸入](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))
