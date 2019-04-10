---
title: HOW TO：使用 TileBrush 建立不同的拼貼模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
ms.openlocfilehash: c1051b234961eee9ae740af2abac3d64c523656c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227401"
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a>HOW TO：使用 TileBrush 建立不同的拼貼模式
此範例示範如何使用<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性<xref:System.Windows.Media.TileBrush>建立模式。  
  
 <xref:System.Windows.Media.TileBrush.TileMode%2A>屬性可讓您指定了內容<xref:System.Windows.Media.TileBrush>重複，也就是，並排顯示以填滿輸出區域。 若要建立的模式，您設定<xref:System.Windows.Media.TileBrush.TileMode%2A>要<xref:System.Windows.Media.TileMode.Tile>， <xref:System.Windows.Media.TileMode.FlipX>， <xref:System.Windows.Media.TileMode.FlipY>，或<xref:System.Windows.Media.TileMode.FlipXY>。 您也必須設定<xref:System.Windows.Media.TileBrush.Viewport%2A>的<xref:System.Windows.Media.TileBrush>，讓它小於您所繪製; 區域，否則為單一並排顯示已產生，而不論其<xref:System.Windows.Media.TileBrush.TileMode%2A>您所使用的設定。  
  
## <a name="example"></a>範例  
 下列範例會建立五<xref:System.Windows.Media.DrawingBrush>物件，並讓他們每個不同<xref:System.Windows.Media.TileBrush.TileMode%2A>設定，並使用它們來繪製五個矩形。 雖然此範例使用<xref:System.Windows.Media.DrawingBrush>類別來示範<xref:System.Windows.Media.TileBrush.TileMode%2A>行為，<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性適用於所有的相同<xref:System.Windows.Media.TileBrush>物件，也就是如<xref:System.Windows.Media.ImageBrush>， <xref:System.Windows.Media.VisualBrush>，和<xref:System.Windows.Media.DrawingBrush>。  
  
 下圖顯示的是這個範例產生的輸出。  
  
 ![TileBrush 並排顯示範例輸出](./media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")  
在建立時 TileMode 屬性的並排顯示模式  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a>另請參閱

- [設定 TileBrush 的拼貼大小](how-to-set-the-tile-size-for-a-tilebrush.md)
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
