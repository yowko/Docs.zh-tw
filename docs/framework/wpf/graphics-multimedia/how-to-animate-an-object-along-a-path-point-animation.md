---
title: HOW TO：沿著路徑建立物件的動畫 (點動畫)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: 13cf583277b4e105da01c5ab56111123cf03038c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351613"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>HOW TO：沿著路徑建立物件的動畫 (點動畫)
此範例示範如何使用<xref:System.Windows.Media.Animation.PointAnimationUsingPath>物件來以動畫顯示<xref:System.Windows.Point>沿著曲線路徑。  
  
## <a name="example"></a>範例  
 下列範例會移動<xref:System.Windows.Media.EllipseGeometry>沿著路徑所定義<xref:System.Windows.Media.PathGeometry>。 橢圓形幾何<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性，以採用<xref:System.Windows.Point>值，指定其位置; 若要移動橢圓形幾何，您以動畫顯示其<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性。 此範例會使用<xref:System.Windows.Media.Animation.PointAnimationUsingPath>來建立動畫<xref:System.Windows.Media.EllipseGeometry>物件的<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性。  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 如需完整的範例，請參閱[路徑動畫範例](https://go.microsoft.com/fwlink/?LinkID=160028)。  
  
 上述範例中使用的程式碼版本<xref:System.Windows.Media.Animation.Storyboard>來以動畫顯示<xref:System.Windows.Media.EllipseGeometry>，即使只有一張動畫已套用。 A<xref:System.Windows.Media.Animation.Storyboard>通常是最簡單的方式套用多個動畫，因為這些動畫可以控制由相同<xref:System.Windows.Media.Animation.Storyboard>。 不過，若要將單一動畫套用至屬性，使用程式碼時更簡單的方法是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法。 如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>另請參閱
- [路徑動畫範例](https://go.microsoft.com/fwlink/?LinkID=160028)
- [動畫概觀](animation-overview.md)
- [路徑動畫操作說明主題](path-animation-how-to-topics.md)
