---
title: "如何：使用 TileBrush 建立不同的並排顯示模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6247f6a16cd8ab7be683d0d4d33aac021f3a2b32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a>如何：使用 TileBrush 建立不同的並排顯示模式
這個範例示範如何使用<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性<xref:System.Windows.Media.TileBrush>建立模式。  
  
 <xref:System.Windows.Media.TileBrush.TileMode%2A>屬性可讓您指定如何內容的<xref:System.Windows.Media.TileBrush>重複，也就是，並排顯示，以填滿輸出區域。 若要建立的模式，您將設定<xref:System.Windows.Media.TileBrush.TileMode%2A>至<xref:System.Windows.Media.TileMode.Tile>， <xref:System.Windows.Media.TileMode.FlipX>， <xref:System.Windows.Media.TileMode.FlipY>，或<xref:System.Windows.Media.TileMode.FlipXY>。 您也必須設定<xref:System.Windows.Media.TileBrush.Viewport%2A>的<xref:System.Windows.Media.TileBrush>使其小於您所繪製; 區域否則單一磚就是產生，而不論其<xref:System.Windows.Media.TileBrush.TileMode%2A>您使用的設定。  
  
## <a name="example"></a>範例  
 下列範例會建立五個<xref:System.Windows.Media.DrawingBrush>物件資訊，請提供每個不同<xref:System.Windows.Media.TileBrush.TileMode%2A>設定，然後使用它們來繪製五個矩形。 雖然這個範例會使用<xref:System.Windows.Media.DrawingBrush>類別來示範<xref:System.Windows.Media.TileBrush.TileMode%2A>行為，<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性即會相同適用於所有<xref:System.Windows.Media.TileBrush>物件，也就是針對<xref:System.Windows.Media.ImageBrush>， <xref:System.Windows.Media.VisualBrush>，和<xref:System.Windows.Media.DrawingBrush>。  
  
 下圖顯示的是這個範例產生的輸出。  
  
 ![TileBrush 並排顯示範例輸出](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")  
利用 TileMode 屬性建立的並排顯示模式  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a>另請參閱  
 [設定 TileBrush 的並排顯示大小](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)  
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
