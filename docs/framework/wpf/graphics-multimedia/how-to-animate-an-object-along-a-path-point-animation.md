---
title: 操作說明：沿著路徑建立物件的動畫 (點動畫)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: eff0c24a9369ffaa0cfca1cc46af4eff39f58a38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452892"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>操作說明：沿著路徑建立物件的動畫 (點動畫)
這個範例示範如何使用 <xref:System.Windows.Media.Animation.PointAnimationUsingPath> 物件，沿著彎曲的路徑建立 <xref:System.Windows.Point> 的動畫。  
  
## <a name="example"></a>範例  
 下列範例會沿著 <xref:System.Windows.Media.PathGeometry>所定義的路徑移動 <xref:System.Windows.Media.EllipseGeometry>。 橢圓形幾何的 <xref:System.Windows.Media.EllipseGeometry.Center%2A> 屬性（採用 <xref:System.Windows.Point> 值）會指定其位置;若要移動橢圓形幾何，您可以建立其 <xref:System.Windows.Media.EllipseGeometry.Center%2A> 屬性的動畫。 這個範例會使用 <xref:System.Windows.Media.Animation.PointAnimationUsingPath>，以動畫顯示 <xref:System.Windows.Media.EllipseGeometry> 物件的 <xref:System.Windows.Media.EllipseGeometry.Center%2A> 屬性。  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 如需完整範例，請參閱[路徑動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)。  
  
 上述範例的程式碼版本使用 <xref:System.Windows.Media.Animation.Storyboard> 來建立 <xref:System.Windows.Media.EllipseGeometry>的動畫，即使只套用了一個動畫也一樣。 <xref:System.Windows.Media.Animation.Storyboard> 通常是套用多個動畫的最簡單方式，因為這些動畫可以透過相同的 <xref:System.Windows.Media.Animation.Storyboard>來控制。 不過，使用程式碼時，將單一動畫套用至屬性的更簡單方法是使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法。 如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>另請參閱

- [路徑動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [動畫概觀](animation-overview.md)
- [路徑動畫操作說明主題](path-animation-how-to-topics.md)
