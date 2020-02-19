---
title: 操作說明：建立 SolidColorBrush 色彩或不透明效果的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 08b85935e0cb1ababd1fb63b9d02518ea3fcfa17
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452879"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>操作說明：建立 SolidColorBrush 色彩或不透明效果的動畫
這個範例示範如何以動畫顯示 <xref:System.Windows.Media.SolidColorBrush>的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 和 <xref:System.Windows.Media.Brush.Opacity%2A>。  
  
## <a name="example"></a>範例  
 下列範例會使用三個動畫，以動畫顯示 <xref:System.Windows.Media.SolidColorBrush>的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 和 <xref:System.Windows.Media.Brush.Opacity%2A>。  
  
- 第一個動畫（<xref:System.Windows.Media.Animation.ColorAnimation>）會在滑鼠進入矩形時，將筆刷的色彩變更為 [<xref:System.Windows.Media.Colors.Gray%2A>]。  
  
- 下一個動畫（另一個 <xref:System.Windows.Media.Animation.ColorAnimation>）會在滑鼠離開矩形時，將筆刷的色彩變更為 [<xref:System.Windows.Media.Colors.Orange%2A>]。  
  
- 當按下滑鼠左鍵時，最後一個動畫（<xref:System.Windows.Media.Animation.DoubleAnimation>）會將筆刷的不透明度變更為0.0。  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 如需更完整的範例，示範如何以動畫顯示不同類型的筆刷，請參閱[筆刷範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。 如需動畫的詳細資訊，請參閱[動畫總覽](animation-overview.md)。  
  
 為了與其他動畫範例保持一致，此範例的程式碼版本會使用 <xref:System.Windows.Media.Animation.Storyboard> 物件來套用其動畫。 不過，在程式碼中套用單一動畫時，使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法比較簡單，而不使用 <xref:System.Windows.Media.Animation.Storyboard>。 如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [分鏡腳本概觀](storyboards-overview.md)
- [筆刷範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
