---
title: 操作說明：設定 TileBrush 的並排顯示大小
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: af7bab59a292549b29dad9b6a7417f22b1b84e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186841"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>操作說明：設定 TileBrush 的並排顯示大小

此示例演示如何設置 的<xref:System.Windows.Media.TileBrush>磁貼大小。 預設情況下，生成<xref:System.Windows.Media.TileBrush>一個完全填充要繪製的區域的磁貼。 可以通過設置 和<xref:System.Windows.Media.TileBrush.Viewport%2A><xref:System.Windows.Media.TileBrush.ViewportUnits%2A>屬性來重寫此行為。

屬性<xref:System.Windows.Media.TileBrush.Viewport%2A>指定 的<xref:System.Windows.Media.TileBrush>磁貼大小。 預設情況下，<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性的值與要繪製的區域的大小相關。 要使<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性指定絕對磁貼大小，請將<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>屬性設置為<xref:System.Windows.Media.BrushMappingMode.Absolute>。

## <a name="example"></a>範例

下面的示例使用<xref:System.Windows.Media.ImageBrush>、 的類型<xref:System.Windows.Media.TileBrush>，使用切片繪製矩形。 該示例將每個磁貼按輸出區域（矩形）的 50% 設置為 50%。 因此，矩形會以影像的四個投影繪製。

下圖顯示了示例生成的輸出：

![一個矩形，有四個櫻桃，用影像筆刷演示平鋪。](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

下一個示例創建<xref:System.Windows.Media.ImageBrush>一個<xref:System.Windows.Media.TileBrush.Viewport%2A> `0,0,25,25` ，設置<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>其<xref:System.Windows.Media.BrushMappingMode.Absolute>和 其 到 ，並使用它來繪製另一個矩形。 因此，筆刷會產生寬度為 25 個像素，且高度為 25 個像素的並排顯示。

下圖顯示了示例生成的輸出：

![一個長方形，有四十八個櫻桃，展示一個瓷磚刷與視口。](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

上述範例是某個完整範例的一部分。 有關完整示例，請參閱[影像筆刷示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)。

儘管此示例使用 類<xref:System.Windows.Media.ImageBrush>，<xref:System.Windows.Media.TileBrush.Viewport%2A>但 和<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>屬性對於其他<xref:System.Windows.Media.TileBrush>物件（即 和<xref:System.Windows.Media.DrawingBrush>） 的行為相同。 <xref:System.Windows.Media.VisualBrush> 有關<xref:System.Windows.Media.ImageBrush>和其他<xref:System.Windows.Media.TileBrush>物件的詳細資訊，請參閱[使用圖像、繪圖和視覺物件進行繪製](painting-with-images-drawings-and-visuals.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.TileBrush>
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
- [使用 TileBrush 建立不同的並排顯示模式](how-to-create-different-tile-patterns-with-a-tilebrush.md)
