---
title: "如何：使用腳本建立屬性的動畫後進行設定"
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
helpviewer_keywords: animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ffc534549f5b114a07f09326be72c1968d178a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a>如何：使用腳本建立屬性的動畫後進行設定
在某些情況下，它可能會出現，動畫之後，您無法變更屬性的值。  
  
## <a name="example"></a>範例  
 在下列範例中，<xref:System.Windows.Media.Animation.Storyboard>用來建立動畫的色彩<xref:System.Windows.Media.SolidColorBrush>。 按一下按鈕時，會觸發分鏡腳本。 <xref:System.Windows.Media.Animation.Timeline.Completed>如此，程式會收到通知，處理事件時<xref:System.Windows.Media.Animation.ColorAnimation>完成。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a>範例  
 之後<xref:System.Windows.Media.Animation.ColorAnimation>完成，則程式會嘗試變更為藍色的筆刷的色彩。  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 先前的程式碼看起來並沒有任何項目： 所提供的筆刷會維持為黃色，也就是值<xref:System.Windows.Media.Animation.ColorAnimation>所繪製的筆刷。 基礎的屬性值 （基底值） 會實際變更為藍色。 不過，有效，或最新的該值會維持黃色因為<xref:System.Windows.Media.Animation.ColorAnimation>仍然會覆寫基底值。 如果您想要再次變成有效的值的基底值，您必須停止動畫屬性的影響。 有三種方法可以使用分鏡腳本動畫達到此目的：  
  
-   設定此動畫的<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性<xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
-   移除整個分鏡腳本。  
  
-   移除個別屬性的動畫。  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a>動畫的 FillBehavior 屬性設定為 停止  
 藉由設定<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>至<xref:System.Windows.Media.Animation.FillBehavior.Stop>，告訴停止作用期結束後，會影響其目標屬性的動畫。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a>移除整個分鏡腳本  
 使用<xref:System.Windows.Media.Animation.RemoveStoryboard>觸發程序或<xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>方法，您可告知停止影響其目標屬性的分鏡腳本動畫。 這個方法與設定之間的差異<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性是您可以移除分鏡腳本在任何時候，雖然<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性只有在動畫達到作用期結束時。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a>移除個別屬性的動畫  
 若要停止動畫影響屬性的另一個技術是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>正在顯示動畫之物件的方法。 指定要繪製的第一個參數之屬性和`null`做為第二個。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 這項技術也適用於非分鏡腳本動畫。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.Animation.RemoveStoryboard>  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
