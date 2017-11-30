---
title: "如何：繪製含有視訊的區域"
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
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 362231bbd1f4e95c260370a99233b7e8c2617ca1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-paint-an-area-with-a-video"></a>如何：繪製含有視訊的區域
這個範例示範如何使用媒體繪製區域。 若要使用媒體繪製區域的一種方式為使用<xref:System.Windows.Controls.MediaElement>搭配<xref:System.Windows.Media.VisualBrush>。 使用<xref:System.Windows.Controls.MediaElement>載入並播放媒體，然後用它來設定<xref:System.Windows.Media.VisualBrush.Visual%2A>屬性<xref:System.Windows.Media.VisualBrush>。 然後您可以使用<xref:System.Windows.Media.VisualBrush>繪製區域載入的媒體。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Controls.MediaElement>和<xref:System.Windows.Media.VisualBrush>來繪製<xref:System.Windows.Controls.TextBlock.Foreground%2A>的<xref:System.Windows.Controls.TextBlock>與視訊控制。 此範例會設定<xref:System.Windows.Controls.MediaElement.IsMuted%2A>屬性<xref:System.Windows.Controls.MediaElement>至`true`，讓它會產生任何聲音。  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a>範例  
 因為<xref:System.Windows.Media.VisualBrush>繼承自<xref:System.Windows.Media.TileBrush>類別，它會提供數個並排顯示模式。 藉由設定<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性<xref:System.Windows.Media.VisualBrush>至<xref:System.Windows.Media.TileMode.Tile>和設定其<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性的值小於您所繪製的區域，您可以建立的並排顯示的模式。  
  
 下列範例等同於上述範例中，不同處在於<xref:System.Windows.Media.VisualBrush>視訊從產生的模式。  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 如需如何將內容檔案，例如媒體檔案新增至您的應用程式，請參閱[WPF 應用程式資源、 內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)。 當您新增的媒體檔案時，您必須將它加入做為內容檔案，而非資源檔。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.VisualBrush>  
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [TileBrush 概觀](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [多媒體概觀](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)
