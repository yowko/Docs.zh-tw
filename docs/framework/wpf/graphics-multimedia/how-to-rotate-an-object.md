---
title: HOW TO：旋轉物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: d1c4700a5dc8f6ed99043552999d8f014116da8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61804155"
---
# <a name="how-to-rotate-an-object"></a>HOW TO：旋轉物件
此範例會顯示如何旋轉物件。 此範例會先建立<xref:System.Windows.Media.RotateTransform>，然後指定其<xref:System.Windows.Media.RotateTransform.Angle%2A>以度為單位。  
  
 下列範例會旋轉<xref:System.Windows.Shapes.Polyline>物件繞其左上角的 45 度。  
  
## <a name="example"></a>範例  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <xref:System.Windows.Media.RotateTransform.CenterX%2A>並<xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性的<xref:System.Windows.Media.RotateTransform>指定哪些物件會旋轉的點。 此中心點是以要轉換之元素的座標空間來表示。 根據預設，旋轉會套用到 (0,0)，這是要轉換之物件的左上角。  
  
 下列範例會<xref:System.Windows.Shapes.Polyline>物件的點 (25，50) 順時針旋轉 45 度。  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 下圖顯示將套用的結果<xref:System.Windows.Media.Transform>兩個物件。  
  
 ![不同中心點的 45 度旋轉](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
繞不同旋轉中心旋轉 45 度的兩個物件  
  
 <xref:System.Windows.Shapes.Polyline>先前的範例中是<xref:System.Windows.UIElement>。 當您套用<xref:System.Windows.Media.Transform>來<xref:System.Windows.UIElement.RenderTransform%2A>屬性<xref:System.Windows.UIElement>，您可以使用<xref:System.Windows.UIElement.RenderTransformOrigin%2A>屬性，以指定的原始主機每<xref:System.Windows.Media.Transform>套用至項目。 因為<xref:System.Windows.UIElement.RenderTransformOrigin%2A>屬性使用相對座標表示，您可以將轉換套用至項目的中心，即使您不知道它的大小。 如需詳細資訊，以及如需範例，請參閱[指定使用相對值轉換的原點](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md)。  
  
 如需完整範例，請參閱 [2D 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Transform>
- [轉換概觀](transforms-overview.md)
- [HOW-TO 主題](transformations-how-to-topics.md)
