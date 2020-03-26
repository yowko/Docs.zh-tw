---
title: 如何：使項目就地旋轉
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a1b515822391de08ec8ed8ff0ff1f0086874dc02
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112072"
---
# <a name="how-to-make-an-element-spin-in-place"></a>如何：使項目就地旋轉
此示例演示如何使用 和<xref:System.Windows.Media.RotateTransform>使元素旋轉。 <xref:System.Windows.Media.Animation.DoubleAnimation>  
  
 下面的示例將 應用於<xref:System.Windows.Media.RotateTransform><xref:System.Windows.UIElement.RenderTransform%2A>元素的屬性。 該示例使用<xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform> 要使元素就位旋轉，該示例將元素的屬性設置<xref:System.Windows.UIElement.RenderTransformOrigin%2A>到點 （0.5， 0.5）。  
  
## <a name="example"></a>範例  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 有關包含更多變換示例的完整示例，請參閱[2D 變換示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [轉換概觀](transforms-overview.md)
