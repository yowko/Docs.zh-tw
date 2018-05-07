---
title: 如何：使項目就地旋轉
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a37952af621c79d231b45a247c92d3576a533580
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-an-element-spin-in-place"></a>如何：使項目就地旋轉
這個範例示範如何讓項目使用微調<xref:System.Windows.Media.RotateTransform>和<xref:System.Windows.Media.Animation.DoubleAnimation>。  
  
 下列範例會套用<xref:System.Windows.Media.RotateTransform>至<xref:System.Windows.UIElement.RenderTransform%2A>元素的屬性。 此範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>以動畫方式顯示<xref:System.Windows.Media.RotateTransform.Angle%2A>的<xref:System.Windows.Media.RotateTransform>。 若要進行微調位置中的項目，範例會設定<xref:System.Windows.UIElement.RenderTransformOrigin%2A>點 （0.5，0.5） 元素的屬性。  
  
## <a name="example"></a>範例  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 如需完整的範例中，包含多個轉換的範例，請參閱[2d 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252)。  
  
## <a name="see-also"></a>另請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
