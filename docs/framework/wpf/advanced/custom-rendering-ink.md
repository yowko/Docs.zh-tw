---
title: 自訂呈現筆墨
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
ms.openlocfilehash: 0ceb831057a9a92aa7319d2004f04d7cf5ac820e
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111825"
---
# <a name="custom-rendering-ink"></a>自訂呈現筆墨
描<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>邊的屬性允許您指定描邊的外觀，例如其大小、顏色和形狀，但有時可能需要自訂超出<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>允許的外觀。 您可能想要自訂筆跡外觀，轉譯具噴槍、油畫及許多其他效果的外觀。 Windows 演示文稿基礎 （WPF） 允許您通過實現自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>和<xref:System.Windows.Ink.Stroke>物件來自訂渲染墨蹟。  
  
 本主題包含下列子章節：  
  
- [建築](#Architecture)  
  
- [實作動態轉譯器](#ImplementingADynamicRenderer)  
  
- [實作自訂筆劃](#ImplementingCustomStrokes)  
  
- [實作自訂 InkCanvas](#ImplementingACustomInkCanvas)  
  
- [結論](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>架構  
 當使用者在筆跡介面寫入筆跡，且在筆劃再次新增至啟用手寫功能的介面之後，筆跡轉譯出現兩次。 當使用者<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>在數位化器上移動 Tablet 筆時，渲<xref:System.Windows.Ink.Stroke>染墨蹟，並在將 Tablet 筆添加到元素後渲染。  
  
 動態轉譯筆跡時有三個類別要實作。  
  
1. **動態呈現器**：實現派生自<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>的類。 此類是專門<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>化的，用於在繪製描邊時呈現筆劃。 在<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>單獨的執行緒上執行渲染，因此，即使應用程式使用者介面 （UI） 執行緒被阻止，墨蹟表面也會顯示收集墨蹟。 如需執行緒模型的詳細資訊，請參閱[筆跡執行緒模型](the-ink-threading-model.md)。 要自訂動態渲染描邊，請重寫<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>方法。  
  
2. **描邊**：實現派生自<xref:System.Windows.Ink.Stroke>的類。 此類負責<xref:System.Windows.Input.StylusPoint>將資料轉換為<xref:System.Windows.Ink.Stroke>物件後靜態呈現資料。 重寫<xref:System.Windows.Ink.Stroke.DrawCore%2A>方法以確保描邊的靜態呈現與動態渲染一致。  
  
3. **墨水畫布：** 實現派生自<xref:System.Windows.Controls.InkCanvas>的類。 將自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>屬性分配給<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>屬性。 重寫<xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A>方法並將自訂描邊添加到<xref:System.Windows.Controls.InkCanvas.Strokes%2A>屬性。 這可確保筆跡外觀的一致。  
  
<a name="ImplementingADynamicRenderer"></a>
## <a name="implementing-a-dynamic-renderer"></a>實作動態轉譯器  
 儘管<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>類是 的標準部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，但要執行更專用的渲染，則必須創建從 派生<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>並重寫<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>方法的自訂動態渲染器。  
  
 下面的示例演示了使用線性<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>漸層筆刷效果繪製墨蹟的自訂。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>
## <a name="implementing-custom-strokes"></a>實作自訂筆劃  
 實作衍生自 <xref:System.Windows.Ink.Stroke> 的類別。 此類負責將資料轉換為<xref:System.Windows.Input.StylusPoint><xref:System.Windows.Ink.Stroke>物件後呈現資料。 重寫類<xref:System.Windows.Ink.Stroke.DrawCore%2A>以執行實際繪圖。  
  
 筆劃類還可以使用 方法<xref:System.Windows.Ink.Stroke.AddPropertyData%2A>存儲自訂資料。 保存此資料時會與筆劃資料一起儲存。  
  
 該<xref:System.Windows.Ink.Stroke>類還可以執行點擊測試。 您還可以通過重寫當前類中<xref:System.Windows.Ink.Stroke.HitTest%2A>的方法來實現您自己的點擊測試演算法。  
  
 以下 C# 代碼演示了<xref:System.Windows.Ink.Stroke>將<xref:System.Windows.Input.StylusPoint>資料呈現為 3D 描邊的自訂類。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>
## <a name="implementing-a-custom-inkcanvas"></a>實作自訂 InkCanvas  
 使用自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>和描邊的最簡單方法是實現派生並<xref:System.Windows.Controls.InkCanvas>使用這些類的類。 具有<xref:System.Windows.Controls.InkCanvas>一個<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>屬性，用於指定在使用者繪製描邊時如何呈現筆劃。  
  
 要在 操作<xref:System.Windows.Controls.InkCanvas>上自訂渲染描邊，可以執行以下操作：  
  
- 創建派生自 的<xref:System.Windows.Controls.InkCanvas>類。  
  
- 將自訂屬性<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>分配給屬性<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType>。  
  
- 覆寫 <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> 方法。 在此方法中，移除已新增至 InkCanvas 的原始筆劃。 然後創建自訂描邊，將其添加到屬性，<xref:System.Windows.Controls.InkCanvas.Strokes%2A>然後用包含自訂描邊的新項<xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs>調用基類。  
  
 以下 C# 代碼演示了<xref:System.Windows.Controls.InkCanvas>使用自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>和收集自訂描邊的自訂類。  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 可以<xref:System.Windows.Controls.InkCanvas>有多個<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。 通過將多個物件添加到<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer><xref:System.Windows.UIElement.StylusPlugIns%2A>屬性，<xref:System.Windows.Controls.InkCanvas>可以向 添加多個物件。  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>結論  
 您可以通過派生自己的<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>和<xref:System.Windows.Ink.Stroke><xref:System.Windows.Controls.InkCanvas>類來自訂墨蹟的外觀。 當使用者繪製並收集筆劃後，這些類別可合力確保筆劃外觀的一致。  
  
## <a name="see-also"></a>另請參閱

- [筆墨進階處理](advanced-ink-handling.md)
