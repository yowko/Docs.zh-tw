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
ms.openlocfilehash: 2eb528127c8aa66976788ec1f4e5362ca3a1ef26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>如何：建立漸層停駐點位置或色彩的動畫
此範例示範如何以動畫方式顯示<xref:System.Windows.Media.GradientStop.Color%2A>和<xref:System.Windows.Media.GradientStop.Offset%2A>的<xref:System.Windows.Media.GradientStop>物件。  
  
## <a name="example"></a>範例  
 下列範例以動畫方式顯示在三個漸層停駐<xref:System.Windows.Media.LinearGradientBrush>。 此範例會使用三個動畫，其中每個不同的漸層停駐以動畫方式顯示：  
  
-   第一次的動畫， <xref:System.Windows.Media.Animation.DoubleAnimation>，以動畫方式顯示第一個漸層停駐<xref:System.Windows.Media.GradientStop.Offset%2A>是介於 0.0 到 1.0 之間，然後再回到 0.0。 如此一來，第一個色彩在右側，即矩形的漸層從左邊算起排班中，然後再變回左側。  
  
-   第二個動畫<xref:System.Windows.Media.Animation.ColorAnimation>，以動畫方式顯示第二個漸層停駐<xref:System.Windows.Media.GradientStop.Color%2A>從<xref:System.Windows.Media.Colors.Purple%2A>至<xref:System.Windows.Media.Colors.Yellow%2A>然後再設回<xref:System.Windows.Media.Colors.Purple%2A>。 如此一來，漸層中間色彩從變更紫色顯示為黃色，並返回紫色。  
  
-   第三個動畫，另一個<xref:System.Windows.Media.Animation.ColorAnimation>，以動畫方式顯示的第三個漸層停駐的不透明度<xref:System.Windows.Media.GradientStop.Color%2A>-1，然後重新開機。 如此一來，第三個的色彩漸層中消失，再變成 不透明。  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 雖然這個範例會使用<xref:System.Windows.Media.LinearGradientBrush>，處理程序是相同的動畫<xref:System.Windows.Media.GradientStop>物件內<xref:System.Windows.Media.RadialGradientBrush>。  
  
 如需其他範例，請參閱[筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.GradientStop>  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
