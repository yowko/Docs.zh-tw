---
title: 如何：建立漸層停駐點位置或色彩的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: fcbb546b64810416d3f7dbe052da77b7bc941e7a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395319"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>如何：建立漸層停駐點位置或色彩的動畫
此範例示範如何建立動畫<xref:System.Windows.Media.GradientStop.Color%2A>並<xref:System.Windows.Media.GradientStop.Offset%2A>的<xref:System.Windows.Media.GradientStop>物件。  
  
## <a name="example"></a>範例  
 下列範例以動畫顯示在三個漸層停駐<xref:System.Windows.Media.LinearGradientBrush>。 此範例使用三個動畫，其中每一個以動畫顯示不同的漸層停駐：  
  
-   第一次的動畫<xref:System.Windows.Media.Animation.DoubleAnimation>，以動畫顯示的第一個漸層停駐<xref:System.Windows.Media.GradientStop.Offset%2A>從 0.0 到 1.0，然後再回到 0.0。 如此一來，第一個色彩在左側能漸層停駐會轉移至矩形右側，然後再設回左側。  
  
-   將第二個動畫<xref:System.Windows.Media.Animation.ColorAnimation>，以動畫顯示第二個漸層停駐<xref:System.Windows.Media.GradientStop.Color%2A>從<xref:System.Windows.Media.Colors.Purple%2A>來<xref:System.Windows.Media.Colors.Yellow%2A>，然後再回到<xref:System.Windows.Media.Colors.Purple%2A>。 如此一來，在漸層的中間色彩從變更為紫色為黃色，再回到紫色。  
  
-   第三個的動畫，另一個<xref:System.Windows.Media.Animation.ColorAnimation>，以動畫顯示的第三個漸層停駐的不透明度<xref:System.Windows.Media.GradientStop.Color%2A>-1，然後重新開機。 如此一來，漸層中的第三個色彩或淡出，然後再次不透明。  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 雖然此範例會使用<xref:System.Windows.Media.LinearGradientBrush>，會以動畫顯示相同的程序<xref:System.Windows.Media.GradientStop>物件內<xref:System.Windows.Media.RadialGradientBrush>。  
  
 如需其他範例，請參閱 <<c0> [ 筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.GradientStop>  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
