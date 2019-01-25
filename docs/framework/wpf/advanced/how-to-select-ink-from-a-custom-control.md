---
title: HOW TO：從自訂控制項選取筆墨
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
ms.openlocfilehash: 02f02dfc3c4086d5b34711eed5eb98fb043ddee8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671833"
---
# <a name="how-to-select-ink-from-a-custom-control"></a>HOW TO：從自訂控制項選取筆墨
藉由新增<xref:System.Windows.Ink.IncrementalLassoHitTester>若您的自訂控制項，您可以啟用您的控制項，讓使用者可以選取使用套索工具，其方式類似於筆墨<xref:System.Windows.Controls.InkCanvas>選取使用套索的筆墨。  
  
 這個範例假設您熟悉建立具備筆墨功能的自訂控制項。  若要建立接受筆跡輸入的自訂控制項，請參閱[建立筆墨輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)。  
  
## <a name="example"></a>範例  
 當使用者繪製套索，<xref:System.Windows.Ink.IncrementalLassoHitTester>預測哪些筆劃套索路徑界限內完成後會使用者套索。  判斷被套索路徑界限內的筆劃可以視為被選取。  選取的筆劃可能也會變成未選取。  例如，如果使用者會反轉繪製套索，時的方向<xref:System.Windows.Ink.IncrementalLassoHitTester>可能取消選取一些筆劃。  
  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>引發<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>事件，可讓您的自訂控制項，以回應使用者繪製套索時。  例如，您可以變更筆劃的外觀，當使用者選取，並取消選取它們。  
  
## <a name="managing-the-ink-mode"></a>管理筆墨模式  
 如果套索出現不同於您的控制項上的筆墨，它是很有幫助使用者。 若要這麼做，您的自訂控制項必須追蹤的使用者是撰寫的還是選取筆墨。 若要這樣做最簡單的方式是將宣告含有兩個值的列舉類型： 一個用來表示使用者正在寫入筆跡，一個用來指出使用者已選取筆墨。  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 接下來，新增兩個<xref:System.Windows.Ink.DrawingAttributes>至類別： 一個用來使用時，使用者撰寫的墨水，使用使用者選取的筆墨另一個。  在建構函式，初始化<xref:System.Windows.Ink.DrawingAttributes>，並附加兩者<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>至相同的事件處理常式的事件。 然後設定<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>的屬性<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>至筆墨<xref:System.Windows.Ink.DrawingAttributes>。  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 新增屬性來公開的選取模式。 當使用者變更選取模式，設定<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>的屬性<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>適當<xref:System.Windows.Ink.DrawingAttributes>物件，並再重新附加<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>屬性設<xref:System.Windows.Controls.InkPresenter>。  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 公開 （expose)<xref:System.Windows.Ink.DrawingAttributes>為屬性，因此應用程式可以判斷筆墨筆劃及選取筆劃的外觀。  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 當屬性<xref:System.Windows.Ink.DrawingAttributes>物件的變更，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>必須再重新附加至<xref:System.Windows.Controls.InkPresenter>。  中的事件處理常式<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>事件時，重新附加<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>至<xref:System.Windows.Controls.InkPresenter>。  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a>使用 IncrementalLassoHitTester  
 建立並初始化<xref:System.Windows.Ink.StrokeCollection>，其中包含所選取的筆劃。  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 當使用者開始所繪製的筆劃時，筆墨或套索，取消選取任何選取的筆劃。 然後，如果使用者繪製套索，建立<xref:System.Windows.Ink.IncrementalLassoHitTester>藉由呼叫<xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>，訂閱<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>事件，並呼叫<xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>。 此程式碼可以是另一個方法，並從呼叫<xref:System.Windows.UIElement.OnStylusDown%2A>和<xref:System.Windows.UIElement.OnMouseDown%2A>方法。  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 新增到的手寫筆點<xref:System.Windows.Ink.IncrementalLassoHitTester>使用者繪製套索時。  呼叫下列方法從<xref:System.Windows.UIElement.OnStylusMove%2A>， <xref:System.Windows.UIElement.OnStylusUp%2A>， <xref:System.Windows.UIElement.OnMouseMove%2A>，和<xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>方法。  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 處理<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType>事件以回應使用者選取，然後取消選取的筆劃。  <xref:System.Windows.Ink.LassoSelectionChangedEventArgs>類別具有<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A>和<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A>已選取取得筆劃的內容，然後將其取消選取，分別。  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 當使用者完成繪製套索時，取消訂閱<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>事件，並呼叫<xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>。  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a>加以整合。  
 下列範例是自訂的控制項，可讓使用者使用套索選取筆墨。  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Ink.IncrementalLassoHitTester>
- <xref:System.Windows.Ink.StrokeCollection>
- <xref:System.Windows.Input.StylusPointCollection>
- [建立筆墨輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)
