---
title: HOW TO：使用分鏡腳本建立屬性的動畫後對該屬性進行設定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: 2e1389392c6465ed56b2c71e53b2e3c1947acbe2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188307"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a>HOW TO：使用分鏡腳本建立屬性的動畫後對該屬性進行設定
在某些情況下，它可能會出現，您就無法變更屬性的值之後已顯示動畫。  
  
## <a name="example"></a>範例  
 在下列範例中，<xref:System.Windows.Media.Animation.Storyboard>用來以動畫顯示的色彩<xref:System.Windows.Media.SolidColorBrush>。 按一下按鈕時，就會觸發將分鏡腳本。 <xref:System.Windows.Media.Animation.Timeline.Completed>如此，程式會收到通知，處理事件時<xref:System.Windows.Media.Animation.ColorAnimation>完成。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a>範例  
 之後<xref:System.Windows.Media.Animation.ColorAnimation>完成時，程式嘗試變更為藍色的筆刷的色彩。  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 先前的程式碼不採取任何動作會出現： 所提供的筆刷維持黃色，也就是值<xref:System.Windows.Media.Animation.ColorAnimation>，以動畫顯示筆刷。 基礎的屬性值 （基底值） 會實際變更為藍色。 不過，有效，或最新狀態，值仍然維持黃色因為<xref:System.Windows.Media.Animation.ColorAnimation>仍然在覆寫基底值。 如果您想要再次變成有效的值的基底值，您必須停止的動畫屬性的影響。 有三種方式，若要使用分鏡腳本動畫：  
  
-   設定動畫的<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
-   移除整個分鏡腳本。  
  
-   移除個別屬性的動畫。  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a>設定為 停止的動畫的 FillBehavior 屬性  
 藉由設定<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>至<xref:System.Windows.Media.Animation.FillBehavior.Stop>，告訴停止作用期結束後，會影響其目標屬性的動畫。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a>移除整個分鏡腳本  
 藉由使用<xref:System.Windows.Media.Animation.RemoveStoryboard>觸發程序或<xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>方法中，您告訴停止影響其目標屬性的分鏡腳本動畫。 這個方法和設定之間的差異<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性是您可以移除分鏡腳本在任何時候，雖然<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性只有在當動畫到達其使用中週期結尾時。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a>移除個別屬性的動畫  
 若要停止從影響屬性動畫的另一個方法是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>展示動畫之物件的方法。 指定要繪製的第一個參數之屬性和`null`作為第二個。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 這項技術也適用於非分鏡腳本動畫中。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.Animation.RemoveStoryboard>
- [動畫概觀](animation-overview.md)
- [屬性動畫技術概觀](property-animation-techniques-overview.md)
