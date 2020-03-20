---
title: 操作說明：旋轉物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: 02d8144c28b7a4e54fb86fea5abb694cf7af34af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185958"
---
# <a name="how-to-rotate-an-object"></a>操作說明：旋轉物件
此範例會顯示如何旋轉物件。 該示例首先創建<xref:System.Windows.Media.RotateTransform>a，然後指定<xref:System.Windows.Media.RotateTransform.Angle%2A>其以度表示。  
  
 下面的示例圍繞<xref:System.Windows.Shapes.Polyline>其左上角旋轉物件 45 度。  
  
## <a name="example"></a>範例  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 的<xref:System.Windows.Media.RotateTransform.CenterX%2A><xref:System.Windows.Media.RotateTransform.CenterY%2A>和 屬性<xref:System.Windows.Media.RotateTransform>指定物件旋轉的點。 此中心點是以要轉換之元素的座標空間來表示。 根據預設，旋轉會套用到 (0,0)，這是要轉換之物件的左上角。  
  
 下一<xref:System.Windows.Shapes.Polyline>個示例沿點 （25，50） 順時針旋轉物件 45 度。  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 下圖顯示了對兩個物件應用 的結果<xref:System.Windows.Media.Transform>。  
  
 ![採用不同中心點的 45 度旋轉](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
繞不同旋轉中心旋轉 45 度的兩個物件  
  
 前面的<xref:System.Windows.Shapes.Polyline>示例中是 。 <xref:System.Windows.UIElement> 將 應用<xref:System.Windows.Media.Transform>到<xref:System.Windows.UIElement.RenderTransform%2A>的屬性時<xref:System.Windows.UIElement>，可以使用 屬性<xref:System.Windows.UIElement.RenderTransformOrigin%2A>為應用於元素的每個<xref:System.Windows.Media.Transform>屬性指定原點。 由於屬性<xref:System.Windows.UIElement.RenderTransformOrigin%2A>使用相對座標，因此即使不知道元素的大小，也可以對元素的中心應用變換。 有關詳細資訊，請參閱[使用相對值指定變換的原點](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md)。  
  
 如需完整範例，請參閱 [2D 轉換範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Transform>
- [轉換概觀](transforms-overview.md)
- [如何使用主題](transformations-how-to-topics.md)
