---
title: "如何：從自訂控制項選取筆墨 | Microsoft Docs"
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
  - "控制項, 筆墨選取"
  - "自訂控制項, 筆墨選取"
  - "筆墨, 從自訂控制項選取"
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：從自訂控制項選取筆墨
將 <xref:System.Windows.Ink.IncrementalLassoHitTester> 加到自訂控制項，便可以啟用控制項，讓使用者得以使用套索工具建立筆墨，使用的方法與 <xref:System.Windows.Controls.InkCanvas> 以套索選取筆墨的方法相似。  
  
 這個範例假設您熟悉建立已啟用筆墨功能之自訂控制項的作業。  若要建立接受筆墨輸入的自訂控制項，請參閱[建立筆墨輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)。  
  
## 範例  
 當使用者繪製套索時，<xref:System.Windows.Ink.IncrementalLassoHitTester> 會預期在使用者完成套索之後，位於套索路徑邊界內的筆劃。  會將判斷為套索路徑邊界內的筆劃視為已選取。  已選取的筆劃也會變成未選取。  例如，如果使用者在繪製套索時反轉方向，<xref:System.Windows.Ink.IncrementalLassoHitTester> 則會取消選取某些筆劃。  
  
 <xref:System.Windows.Ink.IncrementalLassoHitTester> 引發 <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> 事件，讓您的自訂控制項可以在使用者繪製套索時做出回應。  例如，您可以在使用者選取和取消選取筆劃時，改變筆劃的外觀。  
  
## 管理筆墨模式  
 如果套索在您的控制項上顯示的外觀與筆墨不同，則對使用者很有幫助。  若要完成這項作業，您的自訂控制項必須追蹤使用者是在寫入或是選取筆墨。  完成這項作業最簡單的方法是，宣告含有兩個值的列舉：一個值指出使用者正在寫入筆墨，另一個值指出使用者正在選取筆墨。  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 接下來，將兩個 <xref:System.Windows.Ink.DrawingAttributes> 加入至類別：其中一個在使用者寫入筆墨時使用，另一個在使用者選取筆墨時使用。  在建構函式中，初始化 <xref:System.Windows.Ink.DrawingAttributes> 並將兩個 <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> 事件附加至相同的事件處理常式。  然後，將 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> 屬性設定為筆墨 <xref:System.Windows.Ink.DrawingAttributes>。  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 加入公開選取模式的屬性。  當使用者變更選取模式時，將 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 的 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> 屬性設定為適當的 <xref:System.Windows.Ink.DrawingAttributes> 物件，然後重新將 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> 屬性附加至 <xref:System.Windows.Controls.InkPresenter>。  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 將 <xref:System.Windows.Ink.DrawingAttributes> 公開為屬性，如此，應用程式便可以判斷筆墨筆劃的外觀和選取筆劃。  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 當 <xref:System.Windows.Ink.DrawingAttributes> 物件的屬性改變時，就必須將 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> 重新附加至 <xref:System.Windows.Controls.InkPresenter>。  在 <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> 事件的事件處理常式中，將 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> 重新附加至 <xref:System.Windows.Controls.InkPresenter>。  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## 使用 IncrementalLassoHitTester  
 建立和初始化包含所選之筆劃的 <xref:System.Windows.Ink.StrokeCollection>。  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 當使用者開始繪製筆劃 \(筆墨或套索\) 時，請取消選取任何選取的筆劃。  然後，如果使用者是在繪製套索，則請透過呼叫 <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A> 來建立 <xref:System.Windows.Ink.IncrementalLassoHitTester>、訂閱 <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> 事件，以及呼叫 <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>。  這個程式碼可以是個別的方法並從 <xref:System.Windows.UIElement.OnStylusDown%2A> 和 <xref:System.Windows.UIElement.OnMouseDown%2A> 方法進行呼叫。  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 當使用者繪製套索時，將手寫筆的點加入至 <xref:System.Windows.Ink.IncrementalLassoHitTester>。  從 <xref:System.Windows.UIElement.OnStylusMove%2A>、<xref:System.Windows.UIElement.OnStylusUp%2A>、<xref:System.Windows.UIElement.OnMouseMove%2A> 和 <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> 方法呼叫下列方法。  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 處理 <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=fullName> 事件以回應使用者對筆劃的選取和取消選取動作。  <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> 類別具有 <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> 和 <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> 屬性，可個別取得已選取和取消選取的筆劃。  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 當使用者完成繪製套索時，從 <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> 事件取消訂閱並呼叫 <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>。  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## 加以整合。  
 下列自訂控制項示範使用者使用套索選取筆墨。  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>   
 <xref:System.Windows.Ink.StrokeCollection>   
 <xref:System.Windows.Input.StylusPointCollection>   
 [建立筆墨輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)