---
title: HOW TO：建立 SolidColorBrush 色彩或不透明效果的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: e440cf49b8b16051361650f9659dc6006c2e7b56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789242"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>HOW TO：建立 SolidColorBrush 色彩或不透明效果的動畫
此範例示範如何建立動畫<xref:System.Windows.Media.SolidColorBrush.Color%2A>並<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.SolidColorBrush>。  
  
## <a name="example"></a>範例  
 下列範例會使用三個動畫以動畫顯示<xref:System.Windows.Media.SolidColorBrush.Color%2A>並<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.SolidColorBrush>。  
  
- 第一次的動畫<xref:System.Windows.Media.Animation.ColorAnimation>，將筆刷的色彩變更為<xref:System.Windows.Media.Colors.Gray%2A>當滑鼠進入矩形。  
  
- 下一個動畫為另一個<xref:System.Windows.Media.Animation.ColorAnimation>，將筆刷的色彩變更為<xref:System.Windows.Media.Colors.Orange%2A>當滑鼠離開矩形。  
  
- 最終的動畫， <xref:System.Windows.Media.Animation.DoubleAnimation>，筆刷的不透明度變更為 0.0，當按下滑鼠左鍵時。  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 如需更完整的範例，示範如何以動畫顯示不同類型的筆刷，請參閱[筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。 如需動畫的詳細資訊，請參閱[動畫概觀](animation-overview.md)。  
  
 為了和其他動畫範例保持一致，此範例中的程式碼版本使用<xref:System.Windows.Media.Animation.Storyboard>來套用其動畫的物件。 不過，套用單一動畫的程式碼中，時，使用的工作變得更容易<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法，而不是使用<xref:System.Windows.Media.Animation.Storyboard>。 如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [分鏡腳本概觀](storyboards-overview.md)
- [筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)
