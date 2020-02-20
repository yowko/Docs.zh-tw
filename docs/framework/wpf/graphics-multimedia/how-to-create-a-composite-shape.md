---
title: 如何：建立複合圖案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
ms.openlocfilehash: c56053f2b07d6055deac5097a68fd7b80ad704ba
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452093"
---
# <a name="how-to-create-a-composite-shape"></a>如何：建立複合圖案
這個範例示範如何使用 <xref:System.Windows.Media.Geometry> 物件建立複合圖案，並使用 <xref:System.Windows.Shapes.Path> 元素來顯示它們。 在下列範例中，會使用 <xref:System.Windows.Media.LineGeometry>、<xref:System.Windows.Media.EllipseGeometry>和 <xref:System.Windows.Media.RectangleGeometry> 搭配 <xref:System.Windows.Media.GeometryGroup> 來建立複合圖形。 接著會使用 <xref:System.Windows.Shapes.Path> 元素繪製幾何。  
  
## <a name="example"></a>範例  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 下圖顯示上一個範例中所建立的圖案。  
  
 ![使用 GeometryGroup 建立的複合幾何](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
複合幾何  
  
 您可以使用 <xref:System.Windows.Media.PathGeometry>，建立更複雜的圖形，例如具有曲線線段的多邊形和圖形。 如需顯示如何使用 <xref:System.Windows.Media.PathGeometry>建立圖形的範例，請參閱[使用 System.windows.media.pathgeometry> 建立圖形](how-to-create-a-shape-by-using-a-pathgeometry.md)。  雖然此範例會使用 <xref:System.Windows.Shapes.Path> 元素將圖形轉譯至螢幕，<xref:System.Windows.Media.Geometry> 物件也可用來描述 <xref:System.Windows.Media.GeometryDrawing> 或 <xref:System.Windows.Media.DrawingContext>的內容。 它們也可以用於裁剪和點擊測試。  
  
 這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)。
