---
title: "自訂呈現筆墨"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 481990acdf2f5b8f798144d36434569b9e2cd481
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="custom-rendering-ink"></a>自訂呈現筆墨
<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>屬性為筆劃的端點可讓您指定的外觀為筆劃的端點，例如其大小、 色彩和形狀，但有時可能會想要自訂外觀以外的視野<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>允許。 您可能想要自訂筆跡外觀，轉譯具噴槍、油畫及許多其他效果的外觀。 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]可讓您自訂要實作自訂轉譯筆墨<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>和<xref:System.Windows.Ink.Stroke>物件。  
  
 本主題包含下列子章節：  
  
-   [架構](#Architecture)  
  
-   [實作動態轉譯器](#ImplementingADynamicRenderer)  
  
-   [實作自訂筆劃](#ImplementingCustomStrokes)  
  
-   [實作自訂 InkCanvas](#ImplementingACustomInkCanvas)  
  
-   [結論](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>架構  
 當使用者在筆跡介面寫入筆跡，且在筆劃再次新增至啟用手寫功能的介面之後，筆跡轉譯出現兩次。 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>呈現筆墨，當使用者將 tablet 畫筆在數位板，而<xref:System.Windows.Ink.Stroke>加入的項目之後呈現其本身。  
  
 動態轉譯筆跡時有三個類別要實作。  
  
1.  **DynamicRenderer**： 實作的類別，衍生自<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。 這個類別是特製化<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>它是繪製呈現筆觸。 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>進行個別的執行緒上轉譯，讓筆跡介面出現收集筆墨，即使應用程式使用者介面 (UI) 執行緒會封鎖。 如需執行緒模型的詳細資訊，請參閱[筆跡執行緒模型](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md)。 若要自訂以動態方式呈現筆觸，覆寫<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>方法。  
  
2.  **筆觸**： 實作的類別，衍生自<xref:System.Windows.Ink.Stroke>。 這個類別會負責的靜態轉譯<xref:System.Windows.Input.StylusPoint>資料轉換成之後<xref:System.Windows.Ink.Stroke>物件。 覆寫<xref:System.Windows.Ink.Stroke.DrawCore%2A>方法，以確保該靜態轉譯筆劃部分是一致的動態呈現。  
  
3.  **InkCanvas:**實作的類別，衍生自<xref:System.Windows.Controls.InkCanvas>。 指派自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>至<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>屬性。 覆寫<xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A>方法並加入至自訂筆觸<xref:System.Windows.Controls.InkCanvas.Strokes%2A>屬性。 這可確保筆跡外觀的一致。  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a>實作動態轉譯器  
 雖然<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>類別是標準的一部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、 執行多個特殊的轉譯，您必須建立自訂的動態轉譯器，衍生自<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>並覆寫<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>方法。  
  
 下列範例會示範自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>繪製以線性漸層筆刷效果的筆墨。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a>實作自訂筆劃  
 實作衍生自 <xref:System.Windows.Ink.Stroke> 的類別。 這個類別會負責轉譯<xref:System.Windows.Input.StylusPoint>資料轉換成之後<xref:System.Windows.Ink.Stroke>物件。 覆寫<xref:System.Windows.Ink.Stroke.DrawCore%2A>類別以進行實際的繪圖。  
  
 筆觸類別也可以使用儲存自訂資料<xref:System.Windows.Ink.Stroke.AddPropertyData%2A>方法。 保存此資料時會與筆劃資料一起儲存。  
  
 <xref:System.Windows.Ink.Stroke>類別也可以執行點擊測試。 您也可以實作您自己的點擊測試演算法藉由覆寫<xref:System.Windows.Ink.Stroke.HitTest%2A>目前類別中的方法。  
  
 下列 C# 程式碼會示範自訂<xref:System.Windows.Ink.Stroke>呈現類別<xref:System.Windows.Input.StylusPoint>資料當做 3d 筆觸。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a>實作自訂 InkCanvas  
 最簡單的方式使用您自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>筆觸是實作衍生自的類別和<xref:System.Windows.Controls.InkCanvas>，並使用這些類別。 <xref:System.Windows.Controls.InkCanvas>具有<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>屬性，指定當使用者繪製筆觸的呈現方式。  
  
 若要自訂轉譯筆劃上<xref:System.Windows.Controls.InkCanvas>執行下列動作：  
  
-   建立衍生自類別<xref:System.Windows.Controls.InkCanvas>。  
  
-   指定您自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>至<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType>屬性。  
  
-   覆寫 <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> 方法。 在此方法中，移除已新增至 InkCanvas 的原始筆劃。 然後建立自訂筆觸、 將它加入<xref:System.Windows.Controls.InkCanvas.Strokes%2A>屬性，並呼叫基底類別的新<xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs>，其中包含自訂筆觸。  
  
 下列 C# 程式碼會示範自訂<xref:System.Windows.Controls.InkCanvas>使用自訂類別<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>並收集自訂筆觸。  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <xref:System.Windows.Controls.InkCanvas>可以有一個以上<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。 您可以加入多個<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>物件加入至<xref:System.Windows.Controls.InkCanvas>藉由加入<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性。  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>結論  
 您可以藉由衍生您自己自訂的筆墨外觀<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>， <xref:System.Windows.Ink.Stroke>，和<xref:System.Windows.Controls.InkCanvas>類別。 當使用者繪製並收集筆劃後，這些類別可合力確保筆劃外觀的一致。  
  
## <a name="see-also"></a>請參閱  
 [筆跡進階處理](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)
