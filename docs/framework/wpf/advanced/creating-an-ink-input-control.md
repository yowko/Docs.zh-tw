---
title: "建立筆墨輸入控制項 | Microsoft Docs"
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
  - "收集筆墨筆劃"
  - "DynamicRenderer 物件"
  - "筆墨輸入控制項"
  - "筆墨筆劃, 收集"
  - "筆墨筆劃, 管理"
  - "筆墨, 呈現"
  - "從滑鼠輸入, 接受"
  - "管理筆墨筆劃"
  - "滑鼠輸入, 接受"
  - "呈現筆墨"
  - "StylusPlugIn 物件"
ms.assetid: c31f3a67-cb3f-4ded-af9e-ed21f6575b26
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 建立筆墨輸入控制項
您可以建立可動態及靜態呈現筆墨的自訂控制項。  也就是，當使用者繪製筆劃時立即呈現筆墨，使筆墨看起來像是「順著」Tablet 畫筆出現一樣，然後再透過 Tablet 畫筆、從 \[剪貼簿\] 貼上或從檔案載入的方式，將筆墨新增至控制項後顯示筆墨。  如果要動態呈現筆墨，您的控制項必須使用 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。  如果要靜態呈現筆墨，必須覆寫手寫筆事件方法 \(<xref:System.Windows.UIElement.OnStylusDown%2A>、<xref:System.Windows.UIElement.OnStylusMove%2A> 及 <xref:System.Windows.UIElement.OnStylusUp%2A>\) 以收集 <xref:System.Windows.Input.StylusPoint> 資料、建立筆劃並新增至 <xref:System.Windows.Controls.InkPresenter> \(會在控制項上呈現筆墨\)。  
  
 本主題包含下列子章節：  
  
-   [HOW TO：收集手寫筆的點資料以及建立筆墨筆劃](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [HOW TO：讓控制項接受由滑鼠輸入](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [整合在一起](#PuttingItTogether)  
  
-   [使用其他外掛程式及 DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [結論](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## HOW TO：收集手寫筆的點資料以及建立筆墨筆劃  
 如果要建立控制項以收集和管理筆墨筆劃，請執行下列步驟：  
  
1.  從 <xref:System.Windows.Controls.Control> 中衍生一個類別，或從 <xref:System.Windows.Controls.Control> 所衍生的類別中衍生一個類別，例如 <xref:System.Windows.Controls.Label>。  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2.  將 <xref:System.Windows.Controls.InkPresenter> 新增至類別，然後將 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性設定為新的 <xref:System.Windows.Controls.InkPresenter>。  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3.  呼叫 <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> 方法，將 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> 附加至 <xref:System.Windows.Controls.InkPresenter>，然後將 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 新增至 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合。  這麼做可讓 <xref:System.Windows.Controls.InkPresenter> 在控制項收集手寫筆的點資料時顯示筆墨。  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4.  覆寫 <xref:System.Windows.UIElement.OnStylusDown%2A> 方法。  這個方法是呼叫 <xref:System.Windows.Input.Stylus.Capture%2A> 以擷取手寫筆。  擷取手寫筆時，即使手寫筆離開控制項的邊界，控制項仍會繼續接收 <xref:System.Windows.UIElement.StylusMove> 和 <xref:System.Windows.UIElement.StylusUp> 事件。  這並不是強制的，但可以提供良好的使用者經驗。  建立新的 <xref:System.Windows.Input.StylusPointCollection> 以收集 <xref:System.Windows.Input.StylusPoint> 資料。  最後，將一組初始的 <xref:System.Windows.Input.StylusPoint> 資料加入至 <xref:System.Windows.Input.StylusPointCollection>。  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5.  覆寫 <xref:System.Windows.UIElement.OnStylusMove%2A> 方法，然後將 <xref:System.Windows.Input.StylusPoint> 資料加入您稍早所建立的 <xref:System.Windows.Input.StylusPointCollection> 物件。  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6.  覆寫 <xref:System.Windows.UIElement.OnStylusUp%2A> 方法並使用 <xref:System.Windows.Input.StylusPointCollection> 資料建立一個新的 <xref:System.Windows.Ink.Stroke>。  將您建立的新 <xref:System.Windows.Ink.Stroke> 加入至 <xref:System.Windows.Controls.InkPresenter> 的 <xref:System.Windows.Controls.InkPresenter.Strokes%2A> 集合，然後釋放手寫筆擷取。  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## HOW TO：讓控制項接受由滑鼠輸入  
 如果您將上述控制項加入至應用程式、執行控制項並使用滑鼠做為輸入裝置，就會發現筆劃沒有保留。  如果要當滑鼠做為輸入裝置時持續顯示筆劃，請執行下列步驟：  
  
1.  覆寫 <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> 並建立新的 <xref:System.Windows.Input.StylusPointCollection>。發生事件時會取得滑鼠的位置，並使用點資料建立一個 <xref:System.Windows.Input.StylusPoint>，然後將 <xref:System.Windows.Input.StylusPoint> 加入至 <xref:System.Windows.Input.StylusPointCollection>。  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2.  覆寫 <xref:System.Windows.UIElement.OnMouseMove%2A> 方法。  發生事件時會取得滑鼠的位置，並使用點資料建立 <xref:System.Windows.Input.StylusPoint>。  將 <xref:System.Windows.Input.StylusPoint> 加入至您稍早建立的 <xref:System.Windows.Input.StylusPointCollection> 物件。  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3.  覆寫 <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> 方法。  使用 <xref:System.Windows.Input.StylusPointCollection> 資料建立新的 <xref:System.Windows.Ink.Stroke>，然後將您建立的新 <xref:System.Windows.Ink.Stroke> 加入至 <xref:System.Windows.Controls.InkPresenter> 的 <xref:System.Windows.Controls.InkPresenter.Strokes%2A> 集合。  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## 整合在一起  
 下列範例中的自訂控制項，會在使用者使用滑鼠或畫筆時收集筆墨。  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## 使用其他外掛程式及 DynamicRenderers  
 您的自訂控制項和 InkCanvas 一樣，也可以有自訂的 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 及其他的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 物件。  將這些加入 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合中。  呈現筆墨時，<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> 中的 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 物件順序會影響筆墨的顯示。  假設您有一個名稱為 `dynamicRenderer` 的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>，而名稱為 `translatePlugin` 的 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 會位移 Tablet 畫筆的筆墨。  如果 `translatePlugin` 是 <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> 中的第一個 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>，`dynamicRenderer` 是第二個，則當使用者移動畫筆時，「流動」的筆墨就會位移。  如果 `dynamicRenderer` 是第一個而 `translatePlugin` 是第二個，則直到使用者提起畫筆時，筆墨才會位移。  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## 結論  
 您可以建立一個控制項，以覆寫手寫筆事件方法來收集並呈現筆墨。  您可以建立自訂控制項、衍生自訂 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 類別，以及將類別插入 <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> 中，就可以利用數位筆墨實作您所能想像的任何行為。  <xref:System.Windows.Input.StylusPoint> 資料產生時您具有存取權，可以自訂 <xref:System.Windows.Input.Stylus> 輸入，並以適合應用程式的方式將輸入呈現在畫面上。  因為您對 <xref:System.Windows.Input.StylusPoint> 資料的存取權限非常低，所以您可以實作筆墨收集並呈現筆墨卻不會影響應用程式的效能。  
  
## 請參閱  
 [筆墨進階處理](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)   
 [存取及管理畫筆輸入](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)