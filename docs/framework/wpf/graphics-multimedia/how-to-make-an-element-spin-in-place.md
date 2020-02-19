---
title: 如何：使項目就地旋轉
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 2e72389a11e48629c2763fcbd9f7b1945ffff5dd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452788"
---
# <a name="how-to-make-an-element-spin-in-place"></a>如何：使項目就地旋轉
這個範例示範如何使用 <xref:System.Windows.Media.RotateTransform> 和 <xref:System.Windows.Media.Animation.DoubleAnimation>，讓元素微調。  
  
 下列範例會將 <xref:System.Windows.Media.RotateTransform> 套用至元素的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性。 此範例會使用 <xref:System.Windows.Media.Animation.DoubleAnimation> 來建立 <xref:System.Windows.Media.RotateTransform><xref:System.Windows.Media.RotateTransform.Angle%2A> 的動畫。 為了讓元素就地旋轉，此範例會將元素的 <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 屬性設定為點（0.5、0.5）。  
  
## <a name="example"></a>範例  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 如需包含更多轉換範例的完整範例，請參閱[2D 轉換範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [轉換概觀](transforms-overview.md)
