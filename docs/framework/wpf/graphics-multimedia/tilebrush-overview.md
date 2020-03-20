---
title: TileBrush 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF]
- brushes [WPF], TileBrush
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
ms.openlocfilehash: 99bcc8695206030a381d71df2dda495867d3e9c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187103"
---
# <a name="tilebrush-overview"></a>TileBrush 概觀
<xref:System.Windows.Media.TileBrush>物件可對圖像或<xref:System.Windows.Media.Drawing>的<xref:System.Windows.Media.Visual>區域如何繪製具有很大的控制。 本主題介紹<xref:System.Windows.Media.TileBrush>如何使用功能來控制<xref:System.Windows.Media.ImageBrush>如何<xref:System.Windows.Media.DrawingBrush><xref:System.Windows.Media.VisualBrush>繪製 區域。  

<a name="prerequisite"></a>
## <a name="prerequisites"></a>必要條件  
 要理解本主題，瞭解如何使用<xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush>或<xref:System.Windows.Media.VisualBrush>類的基本功能很有説明。 有關這些類型的介紹，請參閱[具有圖像、繪圖和視覺功能的繪畫](painting-with-images-drawings-and-visuals.md)。  
  
<a name="tilebrush"></a>
## <a name="painting-an-area-with-tiles"></a>以並排顯示繪製區域  
 <xref:System.Windows.Media.ImageBrush><xref:System.Windows.Media.DrawingBrush>是<xref:System.Windows.Media.VisualBrush>物件的類型<xref:System.Windows.Media.TileBrush>。 拼貼筆刷讓您對使用影像、繪圖或視覺效果繪製區域的方式擁有更多的控制。 例如，您可以用構成圖樣的一系列影像並排顯示來繪製區域，而不是只以單一自動縮放的影像來繪製區域。  
  
 使用拼貼筆刷繪製區域會牽涉到三個元件：內容、基底並排顯示及輸出區域。  
  
 ![TileBrush 元件](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
具有單一並排顯示之 TileBrush 的元件  
  
 ![區塊式 TileBrush 的元件](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
TileMode 為 Tile 之 TileBrush 的元件  
  
 輸出區域是要繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的區域，如 的<xref:System.Windows.Shapes.Ellipse>或<xref:System.Windows.Controls.Control.Background%2A><xref:System.Windows.Controls.Button>。 接下來的部分將介紹 的其他兩個<xref:System.Windows.Media.TileBrush>元件。  
  
<a name="brushcontent"></a>
## <a name="brush-content"></a>筆刷內容  
 有三種<xref:System.Windows.Media.TileBrush>不同類型的和每種塗料具有不同類型的內容。  
  
- 如果畫筆為<xref:System.Windows.Media.ImageBrush>，則此內容是圖像 屬性<xref:System.Windows.Media.ImageBrush.ImageSource%2A>指定 的內容。 <xref:System.Windows.Media.ImageBrush>  
  
- 如果畫筆為 ，<xref:System.Windows.Media.DrawingBrush>則此內容為繪圖。 屬性<xref:System.Windows.Media.DrawingBrush.Drawing%2A>指定 的內容<xref:System.Windows.Media.DrawingBrush>。  
  
- 如果畫筆是 ，<xref:System.Windows.Media.VisualBrush>則此內容是可視內容。 屬性<xref:System.Windows.Media.VisualBrush.Visual%2A>指定 的內容<xref:System.Windows.Media.VisualBrush>。  
  
 可以使用<xref:System.Windows.Media.TileBrush><xref:System.Windows.Media.TileBrush.Viewbox%2A>屬性指定內容的位置和尺寸，儘管通常將<xref:System.Windows.Media.TileBrush.Viewbox%2A>集保留為其預設值。 預設情況下，<xref:System.Windows.Media.TileBrush.Viewbox%2A>配置為完全包含畫筆的內容。 有關配置 的詳細資訊，<xref:System.Windows.Controls.Viewbox>請參閱<xref:System.Windows.Controls.Viewbox>屬性頁。  
  
<a name="thebasetile"></a>
## <a name="the-base-tile"></a>基底並排顯示  
 將<xref:System.Windows.Media.TileBrush>其內容投射到基磁貼上。 屬性<xref:System.Windows.Media.TileBrush.Stretch%2A>控制如何<xref:System.Windows.Media.TileBrush>拉伸內容以填充基本磁貼。 屬性<xref:System.Windows.Media.TileBrush.Stretch%2A>接受以下值，由<xref:System.Windows.Media.Stretch>枚舉定義：  
  
- <xref:System.Windows.Media.Stretch.None>：畫筆的內容不會拉伸以填充磁貼。  
  
- <xref:System.Windows.Media.Stretch.Fill>： 畫筆的內容將縮放以適合磁貼。 因為內容的高度和寬度會分開縮放，所以可能不會保留內容的原始外觀比例。 也就是說，筆刷的內容可能會變形以完全填滿輸出並排顯示。  
  
- <xref:System.Windows.Media.Stretch.Uniform>： 畫筆的內容被縮放，以便完全適合磁貼。 這會維持內容的外觀比例。  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>：畫筆的內容被縮放，以便它完全填充輸出區域，同時保持內容的原始縱橫比。  
  
 下圖說明瞭不同的<xref:System.Windows.Media.TileBrush.Stretch%2A>設置。  
  
 ![不同的 TileBrush Stretch 設定](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 在下面的示例中，將設置 的內容<xref:System.Windows.Media.ImageBrush>，以便它不拉伸以填充輸出區域。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 預設情況下，生成<xref:System.Windows.Media.TileBrush>單個磁貼（基本磁貼）並拉伸該磁貼以完全填充輸出區域。 您可以通過設置<xref:System.Windows.Media.TileBrush.Viewport%2A>和 屬性來更改基本磁貼的大小和<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>位置。  
  
<a name="basetilesize"></a>
### <a name="base-tile-size"></a>基底並排顯示大小  
 屬性<xref:System.Windows.Media.TileBrush.Viewport%2A>確定基本磁貼的大小和位置，<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>該屬性確定是使用絕對座標還是相對座標<xref:System.Windows.Media.TileBrush.Viewport%2A>指定 。 如果是相對座標，則它們會相對於輸出區域的大小。 (0,0) 這個點表示輸出區域的左上角，而 (1,1) 則表示輸出區域的右下角。 要指定<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性使用絕對座標，請將<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>屬性設置為<xref:System.Windows.Media.BrushMappingMode.Absolute>。  
  
 下圖顯示了<xref:System.Windows.Media.TileBrush>相對與絕對<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>之間的輸出差異。 請注意，每個圖例都會顯示並排顯示圖樣，下一節會說明如何指定並排顯示圖樣。  
  
 ![絕對和相對檢視區單位](./media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 在下列範例中，會使用影像建立 50% 寬度和高度的並排顯示。 基底並排顯示位於輸出區域的 (0,0)。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 下一個示例將 a<xref:System.Windows.Media.ImageBrush>的切片設置為 25 x 25 個獨立于設備的圖元。 由於<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>是絕對的，因此<xref:System.Windows.Media.ImageBrush>無論所繪製的區域大小如何，切片始終為 25 x 25 圖元。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>
### <a name="tiling-behavior"></a>並排顯示行為  
 當<xref:System.Windows.Media.TileBrush>基鋪未完全填充輸出區域，並指定其他<xref:System.Windows.Media.TileMode.None>切片模式時，將生成平鋪模式。 當磁貼畫筆的磁貼未完全填充輸出區域時，其<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性指定是否應複製基圖以填充輸出區域，如果是，則指定基圖應如何複製。 屬性<xref:System.Windows.Media.TileBrush.TileMode%2A>接受以下值，由<xref:System.Windows.Media.TileMode>枚舉定義：  
  
- <xref:System.Windows.Media.TileMode.None>：僅繪製基本磁貼。  
  
- <xref:System.Windows.Media.TileMode.Tile>： 繪製基本磁貼，通過重複基磁貼填充剩餘區域，以便一個磁貼的右邊緣與下一個磁貼的左邊緣相鄰，與底部和頂部類似。  
  
- <xref:System.Windows.Media.TileMode.FlipX>： 與<xref:System.Windows.Media.TileMode.Tile>相同，但切片的替代列是水準翻轉的。  
  
- <xref:System.Windows.Media.TileMode.FlipY>： 與<xref:System.Windows.Media.TileMode.Tile>相同，但其他切片行垂直翻轉。  
  
- <xref:System.Windows.Media.TileMode.FlipXY>： 和<xref:System.Windows.Media.TileMode.FlipY><xref:System.Windows.Media.TileMode.FlipX>的組合。  
  
 下列影像說明不同的並排顯示模式。  
  
 ![不同的 TileBrush TileMode 設定](./media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 在下列範例中，會使用影像繪製 100 像素寬及 100 像素高的矩形。 通過將畫筆<xref:System.Windows.Media.TileBrush.Viewport%2A>設置為 0，0，0.25，0.25，使畫筆的基磁貼設置為輸出區域的 1/4。 畫筆<xref:System.Windows.Media.TileBrush.TileMode%2A>設置為<xref:System.Windows.Media.TileMode.FlipXY>。 所以會以並排顯示列填滿矩形。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
- [如何使用主題](brushes-how-to-topics.md)
- [Freezable 物件概觀](../advanced/freezable-objects-overview.md)
- [ImageBrush 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [VisualBrush 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
