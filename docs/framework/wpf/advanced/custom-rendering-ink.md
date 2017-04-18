---
title: "自訂呈現筆墨 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "類別, DynamicRenderer"
  - "類別, InkCanvas"
  - "類別, 筆劃"
  - "自訂呈現筆墨"
  - "DynamicRenderer 類別"
  - "筆墨, 自訂呈現"
  - "InkCanvas 類別"
  - "Stroke 類別"
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 自訂呈現筆墨
筆劃的 <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> 屬性可讓您指定筆劃的外觀，例如大小、色彩和形狀，不過，您有時想要自訂外觀的部分可能超出 <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> 允許的範圍。  您可能會想自訂筆墨的外觀，在呈現的外觀加上噴槍、油畫和其他許多效果。  [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 可讓您實作自訂 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 和 <xref:System.Windows.Ink.Stroke> 物件，藉此方式自訂呈現筆墨。  
  
 本主題包含下列子章節：  
  
-   [架構](#Architecture)  
  
-   [實作動態產生器](#ImplementingADynamicRenderer)  
  
-   [Implementing a Custom Stroke](#ImplementingACustomStroke)  
  
-   [實作自訂 InkCanvas](#ImplementingACustomInkCanvas)  
  
-   [結論](#Conclusion)  
  
<a name="Architecture"></a>   
## 架構  
 筆墨呈現會執行兩次，一是在使用者將筆墨寫到筆墨表面時，另一則是在筆劃加入到啟用筆墨的表面之後。  當使用者在數位板上移動 Tablet 畫筆時，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 會呈現筆墨，而 <xref:System.Windows.Ink.Stroke> 在一加入項目時會呈現本身。  
  
 動態呈現筆墨時，有三個類別要實作。  
  
1.  **DynamicRenderer**：實作衍生自 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 的類別。  此類別是特殊的 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>，會在繪製筆劃時呈現筆劃。  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 會在另外的執行緒上呈現筆墨，所以即使當應用程式使用者介面 \(UI\) 執行緒遭封鎖，筆墨表面也會像是在收集筆墨。  如需執行緒模型的詳細資訊，請參閱[筆墨執行緒模型](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md)。  若要自訂動態呈現筆墨，請覆寫 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> 方法。  
  
2.  **Stroke**：實作衍生自 <xref:System.Windows.Ink.Stroke> 的類別。  此類別負責在 <xref:System.Windows.Input.StylusPoint> 資料轉換成 <xref:System.Windows.Ink.Stroke> 物件之後靜態呈現資料。  請覆寫 <xref:System.Windows.Ink.Stroke.DrawCore%2A> 方法，以確保筆劃的靜態呈現與動態呈現一致。  
  
3.  **InkCanvas**：實作衍生自 <xref:System.Windows.Controls.InkCanvas> 的類別。  將自訂的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 指派給 <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> 屬性。  覆寫 <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> 方法，並將自訂筆劃加入到 <xref:System.Windows.Controls.InkCanvas.Strokes%2A> 屬性。  這可確保筆墨的外觀一致。  
  
<a name="ImplementingADynamicRenderer"></a>   
## 實作動態產生器  
 雖然 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 類別是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的標準組件，但若要執行更特殊的呈現效果，就必須建立衍生自 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 的自訂動態產生器，並覆寫 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> 方法。  
  
 下列範例示範自訂的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>，會以線形漸層筆刷效果繪製筆墨。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## 實作自訂筆劃  
 實作衍生自 <xref:System.Windows.Ink.Stroke> 的類別。  此類別負責在 <xref:System.Windows.Input.StylusPoint> 資料轉換成 <xref:System.Windows.Ink.Stroke> 物件之後呈現資料。  覆寫 <xref:System.Windows.Ink.Stroke.DrawCore%2A> 類別以進行實際繪製。  
  
 Stroke 類別也可以使用 <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> 方法儲存自訂資料。  此資料會在保存時與筆劃資料一起儲存。  
  
 <xref:System.Windows.Ink.Stroke> 類別也可以執行點擊測試。  您也可以覆寫目前類別中的 <xref:System.Windows.Ink.Stroke.HitTest%2A> 方法，實作自己的點擊測試演算法。  
  
 下列 C\# 程式碼示範自訂 <xref:System.Windows.Ink.Stroke> 類別，此類別會將 <xref:System.Windows.Input.StylusPoint> 資料呈現為立體筆劃。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## 實作自訂 InkCanvas  
 使用自訂 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 和筆劃最簡單的方法是實作衍生自 <xref:System.Windows.Controls.InkCanvas> 的類別，並使用這些類別。  <xref:System.Windows.Controls.InkCanvas> 具有 <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> 屬性，會指定使用者在繪製筆劃時，如何呈現筆劃。  
  
 若要自訂 <xref:System.Windows.Controls.InkCanvas> 上的呈現筆墨，請執行下列步驟：  
  
-   建立衍生自 <xref:System.Windows.Controls.InkCanvas> 的類別。  
  
-   將自訂的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 指派給 <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=fullName> 屬性。  
  
-   覆寫 <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> 方法。  在此方法中，移除原本加入到 InkCanvas 的筆劃。  然後建立自訂筆劃，將它加入到 <xref:System.Windows.Controls.InkCanvas.Strokes%2A> 屬性，最後再使用包含自訂筆劃的新 <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> 呼叫基底類別。  
  
 下列 C\# 程式碼示範自訂 <xref:System.Windows.Controls.InkCanvas> 類別，此類別會使用自訂的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 並收集自訂筆劃。  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <xref:System.Windows.Controls.InkCanvas> 可以有一個以上的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。  您可以將多個 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 物件加入到 <xref:System.Windows.Controls.InkCanvas>，方法是將它們加入到 <xref:System.Windows.UIElement.StylusPlugIns%2A> 屬性。  
  
<a name="Conclusion"></a>   
## 結論  
 您可以衍生自己的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>、<xref:System.Windows.Ink.Stroke> 和 <xref:System.Windows.Controls.InkCanvas> 類別，來自訂筆墨的外觀。  在一起使用時，這些類別能確保筆劃的外觀在使用者繪製筆劃時以及在收集之後都是一致的。  
  
## 請參閱  
 [筆墨進階處理](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)