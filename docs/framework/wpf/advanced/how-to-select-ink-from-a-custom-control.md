---
title: 如何：從自訂控制項選取筆墨
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
ms.openlocfilehash: 6c85855cda4f74d557539ed7aea3f725550512e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-select-ink-from-a-custom-control"></a>如何：從自訂控制項選取筆墨
藉由新增<xref:System.Windows.Ink.IncrementalLassoHitTester>若您的自訂控制項，您可以啟用您的控制項，讓使用者可以選取使用套索工具，其方式類似於筆墨<xref:System.Windows.Controls.InkCanvas>選取使用套索的筆墨。  
  
 這個範例假設您已熟悉如何建立已啟用筆墨的自訂控制項。  若要建立接受筆跡輸入的自訂控制項，請參閱[建立筆跡輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)。  
  
## <a name="example"></a>範例  
 當使用者繪製套索，<xref:System.Windows.Ink.IncrementalLassoHitTester>預測套索使用者後，將會在套索路徑的界限內的筆劃。  判斷套索路徑的界限內的筆劃可以視為被選取。  選取的筆劃可能也會變成未選取。  例如，如果使用者反轉方向繪製套索時<xref:System.Windows.Ink.IncrementalLassoHitTester>可以取消選取一些筆劃。  
  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>引發<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>事件，可讓您自訂控制項，以回應使用者繪製套索時。  例如，您可以變更筆劃的外觀，當使用者選取並取消選取。  
  
## <a name="managing-the-ink-mode"></a>管理筆墨模式  
 如果套索方式不同於您的控制項上的筆墨出現時，就會很有幫助使用者。 若要完成此動作，自訂控制項必須持續追蹤的使用者是寫入，或選取筆墨。 若要這樣做最簡單的方式是宣告的列舉，具有兩個值： 一個用來表示使用者正在寫入筆跡和一個用來表示使用者選取的筆墨。  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 接下來，加入兩個<xref:System.Windows.Ink.DrawingAttributes>類別： 時，使用者撰寫的墨水，一個使用使用者選取的筆墨時所要使用其中一個。  在建構函式，初始化<xref:System.Windows.Ink.DrawingAttributes>和附加兩者<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>至相同的事件處理常式的事件。 然後設定<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>屬性<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>至筆墨<xref:System.Windows.Ink.DrawingAttributes>。  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 加入屬性，以便公開選取模式。 當使用者變更選取模式，設定<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>屬性<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>適當<xref:System.Windows.Ink.DrawingAttributes>物件，然後重新附加<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>屬性<xref:System.Windows.Controls.InkPresenter>。  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 公開<xref:System.Windows.Ink.DrawingAttributes>做為屬性，因此應用程式可以判斷筆墨筆劃與選取項目筆劃的外觀。  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 當屬性<xref:System.Windows.Ink.DrawingAttributes>物件變更，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>必須重新附加至<xref:System.Windows.Controls.InkPresenter>。  中的事件處理常式<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>事件時，重新附加<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>至<xref:System.Windows.Controls.InkPresenter>。  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a>使用 IncrementalLassoHitTester  
 建立和初始化<xref:System.Windows.Ink.StrokeCollection>，其中包含所選取的筆劃。  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 當使用者開始繪製的筆劃時，墨水或套索，取消選取任何選取的筆劃。 然後，如果使用者繪製套索，建立<xref:System.Windows.Ink.IncrementalLassoHitTester>藉由呼叫<xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>，訂閱<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>事件和呼叫<xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>。 這個程式碼可以是不同的方法，並從呼叫<xref:System.Windows.UIElement.OnStylusDown%2A>和<xref:System.Windows.UIElement.OnMouseDown%2A>方法。  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 將手寫筆指向<xref:System.Windows.Ink.IncrementalLassoHitTester>使用者繪製套索時。  呼叫下列方法，從<xref:System.Windows.UIElement.OnStylusMove%2A>， <xref:System.Windows.UIElement.OnStylusUp%2A>， <xref:System.Windows.UIElement.OnMouseMove%2A>，和<xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>方法。  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 處理<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType>時使用者會選取並取消選取筆劃回應事件。  <xref:System.Windows.Ink.LassoSelectionChangedEventArgs>類別具有<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A>和<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A>選取而且未選取，分別取得 strokes 屬性。  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 當使用者完成繪製套索時，取消訂閱<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>事件和呼叫<xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>。  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a>加以整合。  
 下列範例是可讓使用者使用套索選取筆墨的自訂控制項。  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>  
 <xref:System.Windows.Ink.StrokeCollection>  
 <xref:System.Windows.Input.StylusPointCollection>  
 [建立筆墨輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)
