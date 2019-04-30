---
title: HOW TO：建立複合圖形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
ms.openlocfilehash: de9f7972c7a51ea623c3630fe62bb48f6109317e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052894"
---
# <a name="how-to-create-a-composite-shape"></a>HOW TO：建立複合圖形
此範例示範如何建立使用的複合圖案<xref:System.Windows.Media.Geometry>物件，並顯示它們使用<xref:System.Windows.Shapes.Path>項目。 在下列範例中， <xref:System.Windows.Media.LineGeometry>， <xref:System.Windows.Media.EllipseGeometry>，以及<xref:System.Windows.Media.RectangleGeometry>會搭配<xref:System.Windows.Media.GeometryGroup>建立複合圖案。 使用再繪製幾何<xref:System.Windows.Shapes.Path>項目。  
  
## <a name="example"></a>範例  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 下圖顯示上一個範例中所建立的圖案。  
  
 ![使用 GeometryGroup 建立的複合幾何](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
複合幾何  
  
 更複雜的圖形，例如多邊形和圖形與曲線線段，可能會建立使用<xref:System.Windows.Media.PathGeometry>。 如需範例，示範如何使用建立圖形<xref:System.Windows.Media.PathGeometry>，請參閱 <<c2> [ 使用 PathGeometry 建立圖案](how-to-create-a-shape-by-using-a-pathgeometry.md)。  雖然此範例的轉譯到螢幕時使用的圖形<xref:System.Windows.Shapes.Path>項目，<xref:System.Windows.Media.Geometry>物件也可用來描述的內容<xref:System.Windows.Media.GeometryDrawing>或<xref:System.Windows.Media.DrawingContext>。 它們也可用來裁剪及點擊測試。  
  
 這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](https://go.microsoft.com/fwlink/?LinkID=159989)。
