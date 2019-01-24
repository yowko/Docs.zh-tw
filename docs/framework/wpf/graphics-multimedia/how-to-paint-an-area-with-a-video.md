---
title: HOW TO：繪製含有視訊的區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
ms.openlocfilehash: c5995359486bcc415b048256c772ec5012b066f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580196"
---
# <a name="how-to-paint-an-area-with-a-video"></a>HOW TO：繪製含有視訊的區域
此範例示範如何使用媒體繪製區域。 若要使用媒體繪製區域的一個方式是使用<xref:System.Windows.Controls.MediaElement>搭配<xref:System.Windows.Media.VisualBrush>。 使用 <xref:System.Windows.Controls.MediaElement>載入及播放媒體，並接著使用它來設定<xref:System.Windows.Media.VisualBrush.Visual%2A>屬性<xref:System.Windows.Media.VisualBrush>。 您可以接著使用<xref:System.Windows.Media.VisualBrush>來繪製區域載入的媒體。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Controls.MediaElement>並<xref:System.Windows.Media.VisualBrush>繪製<xref:System.Windows.Controls.TextBlock.Foreground%2A>的<xref:System.Windows.Controls.TextBlock>與 video 搭配運作的控制項。 此範例會設定<xref:System.Windows.Controls.MediaElement.IsMuted%2A>的屬性<xref:System.Windows.Controls.MediaElement>到`true`以便所不產生的任何聲音。  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a>範例  
 因為<xref:System.Windows.Media.VisualBrush>繼承自<xref:System.Windows.Media.TileBrush>類別，它會提供數個並排顯示模式。 藉由設定<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性<xref:System.Windows.Media.VisualBrush>要<xref:System.Windows.Media.TileMode.Tile>並且將其<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性的值小於您所繪製的區域，您可以建立並排顯示的圖樣。  
  
 下列範例等同於上述範例中，不同之處在於<xref:System.Windows.Media.VisualBrush>會產生從視訊的模式。  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 如需如何將內容檔案，例如媒體檔案新增至您的應用程式，請參閱[WPF 應用程式資源、 內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)。 當您新增的媒體檔案時，您必須將它新增為內容檔案，而非資源檔。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.VisualBrush>
- [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [TileBrush 概觀](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)
- [多媒體概觀](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)
