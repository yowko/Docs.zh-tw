---
title: HOW TO：建立矩形動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], rectangles
- rectangles [WPF], animating
ms.assetid: 572ffb95-790d-4ace-adbf-b2ea8a90e75b
ms.openlocfilehash: d164a6ecc64c1a4e78be41304cace7515684b488
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530097"
---
# <a name="how-to-animate-a-rectangle"></a>HOW TO：建立矩形動畫
這個範例示範如何以動畫顯示矩形的大小和位置變更。  
  
## <a name="example"></a>範例  
 下列範例使用的執行個體<xref:System.Windows.Media.Animation.RectAnimation>類別以動畫顯示<xref:System.Windows.Media.RectangleGeometry.Rect%2A>屬性<xref:System.Windows.Media.RectangleGeometry>，其中以動畫顯示矩形的位置和大小的變更。  
  
 [!code-csharp[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/RectAnimationExample.cs#rectanimationwholepage)]
 [!code-vb[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/RectAnimationExample.vb#rectanimationwholepage)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.Animation.RectAnimation>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.RectangleGeometry>
- [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)
- [動畫和計時](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
