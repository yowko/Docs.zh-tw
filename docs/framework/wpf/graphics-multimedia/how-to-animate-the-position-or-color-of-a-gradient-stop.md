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
ms.openlocfilehash: aeae33f5f3c8016808988f58d61969e9b6f05039
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452840"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>如何：建立漸層停駐點位置或色彩的動畫
這個範例示範如何以動畫顯示 <xref:System.Windows.Media.GradientStop> 物件的 <xref:System.Windows.Media.GradientStop.Color%2A> 和 <xref:System.Windows.Media.GradientStop.Offset%2A>。  
  
## <a name="example"></a>範例  
 下列範例會在 <xref:System.Windows.Media.LinearGradientBrush>內繪製三個漸層停駐的動畫。 此範例使用三個動畫，其中每一個都會以動畫呈現不同的漸層停駐點：  
  
- 第一個動畫是 <xref:System.Windows.Media.Animation.DoubleAnimation>，會將第一個漸層停駐的 <xref:System.Windows.Media.GradientStop.Offset%2A> 從0.0 到1.0，然後回到0.0。 因此，漸層中的第一個色彩會從左邊到矩形的右邊，然後回到左側。  
  
- 第二個動畫（<xref:System.Windows.Media.Animation.ColorAnimation>）會將第二個漸層停駐的 <xref:System.Windows.Media.GradientStop.Color%2A> 從 <xref:System.Windows.Media.Colors.Purple%2A> 繪製到 <xref:System.Windows.Media.Colors.Yellow%2A>，然後再回到 <xref:System.Windows.Media.Colors.Purple%2A>。 如此一來，漸層中的中間色彩就會從紫色變更為黃色，再改回紫色。  
  
- 第三個動畫，另一個 <xref:System.Windows.Media.Animation.ColorAnimation>，會將第三個漸層停駐 <xref:System.Windows.Media.GradientStop.Color%2A> 點的不透明度繪製到-1，然後返回。 因此，漸層中的第三個色彩會淡開，然後再次變成不透明。  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 雖然此範例使用 <xref:System.Windows.Media.LinearGradientBrush>，但在 <xref:System.Windows.Media.RadialGradientBrush>內建立 <xref:System.Windows.Media.GradientStop> 物件動畫的程式是相同的。  
  
 如需其他範例，請參閱[筆刷範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.GradientStop>
- [動畫概觀](animation-overview.md)
- [分鏡腳本概觀](storyboards-overview.md)
