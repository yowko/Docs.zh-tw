---
title: HOW TO：使用 PointAnimation 建立物件位置的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
ms.openlocfilehash: 1ef3f77e551affaa7e61d2aabf95f10c29275417
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111302"
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a>HOW TO：使用 PointAnimation 建立物件位置的動畫
此範例示範如何使用<xref:System.Windows.Media.Animation.PointAnimation>類別以動畫顯示物件沿著<xref:System.Windows.Shapes.Path>。  
  
## <a name="example"></a>範例  
 下列範例會沿著移動橢圓形<xref:System.Windows.Shapes.Path>從另一個畫面上的一個點。 此範例以動畫顯示的位置<xref:System.Windows.Media.EllipseGeometry>利用<xref:System.Windows.Media.Animation.PointAnimation>來以動畫顯示<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性。  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.PointAnimation>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.EllipseGeometry>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A>
- [動畫概觀](animation-overview.md)
- [圖形和多媒體](index.md)
- [圖形 HOW TO 主題](graphics-how-to-topics.md)
- [動畫和計時 HOW TO 主題](animation-and-timing-how-to-topics.md)
