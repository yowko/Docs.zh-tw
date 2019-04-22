---
title: HOW TO：設定 TileBrush 的拼貼大小
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: 80b5dfc668464df829db593668bea8a9a4ec09e4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839672"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>HOW TO：設定 TileBrush 的拼貼大小

此範例示範如何設定的並排顯示大小<xref:System.Windows.Media.TileBrush>。 根據預設，<xref:System.Windows.Media.TileBrush>會產生單一並排顯示，以完全填滿您所繪製的區域。 您可以藉由設定覆寫這個行為<xref:System.Windows.Media.TileBrush.Viewport%2A>和<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>屬性。

<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性指定的並排顯示大小<xref:System.Windows.Media.TileBrush>。 根據預設，windows 7<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性是相對於正在繪製之區域的大小。 若要讓<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性指定絕對的並排顯示大小，設定<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>屬性設<xref:System.Windows.Media.BrushMappingMode.Absolute>。

## <a name="example"></a>範例

下列範例會使用<xref:System.Windows.Media.ImageBrush>，一種<xref:System.Windows.Media.TileBrush>、 要繪製的圖格的矩形。 範例會設定為百分之 50 的輸出區域 （矩形） 的 50%的每個圖格。 因此，矩形會以影像的四個投影繪製。

下圖顯示範例所產生的輸出：

![具有四個櫻桃示範影像筆刷的並排顯示的矩形。](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

下一個範例會建立<xref:System.Windows.Media.ImageBrush>，設定其<xref:System.Windows.Media.TileBrush.Viewport%2A>要`0,0,25,25`及其<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>到<xref:System.Windows.Media.BrushMappingMode.Absolute>，並用它來繪製另一個矩形。 因此，筆刷會產生寬度為 25 個像素，且高度為 25 個像素的並排顯示。

下圖顯示範例所產生的輸出：

![40 八櫻桃示範並排顯示的 TileBrush 的 Viewport 矩形。](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

上述範例是某個完整範例的一部分。 如需完整的範例，請參閱[ImageBrush 範例](https://go.microsoft.com/fwlink/?LinkID=160005)。

雖然此範例會使用<xref:System.Windows.Media.ImageBrush>類別，<xref:System.Windows.Media.TileBrush.Viewport%2A>並<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>屬性運作方式完全相同的另<xref:System.Windows.Media.TileBrush>物件，也就是如<xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>。 如需詳細資訊<xref:System.Windows.Media.ImageBrush>和其他<xref:System.Windows.Media.TileBrush>物件，請參閱[使用影像、 繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.TileBrush>
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
- [使用 TileBrush 建立不同的並排顯示模式](how-to-create-different-tile-patterns-with-a-tilebrush.md)
