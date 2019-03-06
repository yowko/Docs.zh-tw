---
title: HOW TO：使用繪圖繪製區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
ms.openlocfilehash: 6b204ae631912181333e2559ebadcdc37e7693b7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371552"
---
# <a name="how-to-paint-an-area-with-a-drawing"></a>HOW TO：使用繪圖繪製區域
此範例顯示如何使用繪圖繪製區域。 若要繪製含有繪圖區域，您使用<xref:System.Windows.Media.DrawingBrush>和一或多個<xref:System.Windows.Media.Drawing>物件。   下列範例會使用<xref:System.Windows.Media.DrawingBrush>來繪製具有兩個橢圓形繪圖的物件。  
  
## <a name="example"></a>範例  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 下圖顯示範例的輸出。  
  
 ![DrawingBrush 的輸出](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")  
  
 (圖案的中心是白色的如中所述的理由[控制複合圖案的填色](how-to-control-the-fill-of-a-composite-shape.md)。)  
  
 藉由設定<xref:System.Windows.Media.DrawingBrush>物件的<xref:System.Windows.Media.TileBrush.Viewport%2A>和<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性，您可以建立重複的圖樣。 下列範例繪製的物件具有從兩個橢圓形繪圖建立的圖樣。  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 下圖顯示並排<xref:System.Windows.Media.DrawingBrush>輸出。  
  
 ![DrawingBrush 的並排顯示輸出](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")  
  
 如需有關繪圖筆刷的詳細資訊，請參閱[使用影像、 繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。 如需詳細資訊<xref:System.Windows.Media.Drawing>物件，請參閱[繪圖物件概觀](drawing-objects-overview.md)。
