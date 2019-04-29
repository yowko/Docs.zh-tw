---
title: 圖形和多媒體
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: 58ee58577b9ff71112103abb4d33c8b85d3c806f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786090"
---
# <a name="graphics-and-multimedia"></a>圖形和多媒體

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 支援多媒體、 向量圖形、 動畫和內容的組合，方便開發人員建置有趣的使用者介面和內容。 使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，您可以建立向量圖形或複雜的動畫，並將媒體整合到應用程式中。

本主題介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的圖形、動畫和媒體功能，其可讓您將圖形、轉換效果、音效以及視訊新增至您的應用程式。

> [!NOTE]
> 強烈建議不要在 Windows 服務中使用 WPF 類型。 如果您嘗試在 Windows 服務中使用 WPF 類型，該服務可能無法如預期般運作。

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>WPF 4 中圖形和多媒體的新功能

圖形和動畫有數項相關變更。

- 版面配置進位

  當物件邊緣位於像素裝置中間時，DPI 獨立圖形系統可以建立轉譯成品，例如模糊或半透明的邊緣。 先前的 WPF 版本包含像素貼齊功能來協助處理這種情況。 Silverlight 2 引進版面配置進位，這是另一種移動元素以讓邊緣落在整個像素邊界上的方法。 WPF 現在支援與捨入的版面配置<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>附加屬性上<xref:System.Windows.FrameworkElement>。

- 快取的組合

  使用新<xref:System.Windows.Media.BitmapCache>和<xref:System.Windows.Media.BitmapCacheBrush>類別，您可以快取為點陣圖的視覺化樹狀結構的複雜部分，並大幅改善轉譯時間。 點陣圖仍可持續回應滑鼠點選之類的使用者輸入，您也可以將它繪製在其他元素上，就像筆刷一般。

- 像素著色器 3 支援

  WPF 4 建置的<xref:System.Windows.Media.Effects.ShaderEffect>WPF 3.5 SP1 中導入，藉由使用來撰寫效果使用像素著色器 (PS) 3.0 版的應用程式的支援。 PS 3.0 著色器模型比 PS 2.0 更為複雜，其在支援的硬體上允許使用更多效果。

- Easing 函式

  您可以利用 Easing 函式讓您進一步控制動畫的行為來美化動畫。 例如，您可以套用<xref:System.Windows.Media.Animation.ElasticEase>至動畫，讓動畫產生彈力。 如需詳細資訊，請參閱中的加/減速類型<xref:System.Windows.Media.Animation>命名空間。

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>圖形和轉譯

WPF 可支援高品質的 2D 圖形。 這些功能包括筆刷、幾何、影像、圖形及轉換。 如需詳細資訊，請參閱[圖形](graphics.md)。 轉譯圖形化的項目根據<xref:System.Windows.Media.Visual>類別。 螢幕上視覺物件的結構是由視覺化樹狀結構描繪。 如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)。

### <a name="2-d-shapes"></a>2D 圖案

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供以向量繪製的常用 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 圖形圖庫，例如下圖所示的矩形和橢圓形。

![圖表顯示橢圓形和矩形。](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

這些內建 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 圖形不只是圖形︰它們也是可程式化元素，能實作許多最常見控制項的功能，包括鍵盤和滑鼠輸入。 下列範例示範如何處理<xref:System.Windows.UIElement.MouseUp>事件引發按一下<xref:System.Windows.Shapes.Ellipse>項目。

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="Window1" >
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />
</Window>
```

```csharp
public partial class Window1  : Window
{
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)
    {
        MessageBox.Show("You clicked the ellipse!");
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)
        MessageBox.Show("You clicked the ellipse!")
    End Sub
End Class
```

下圖顯示上述 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記和程式碼後置的輸出。

![訊息方塊，指出 「 您已經按一下這個橢圓形 ！ 」](./media/index/messagebox-text-output.png)

如需詳細資訊，請參閱 [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)。 如需簡介範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。

### <a name="2-d-geometries"></a>2D 幾何

當 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供的 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 圖形不敷使用時，您可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 來支援您自己建立的幾何和路徑。 下圖示範如何使用幾何來建立圖形，當做繪圖筆刷並裁剪其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 元素。

![螢幕擷取畫面顯示如何使用幾何來建立圖形。](./media/index/use-geometries-create-shapes.png)

如需詳細資訊，請參閱[幾何概觀](geometry-overview.md)。 如需簡介範例，請參閱[幾何範例](https://go.microsoft.com/fwlink/?LinkID=159989)。

### <a name="2-d-effects"></a>2D 效果

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 類別的程式庫可讓您建立各種不同的效果。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 轉譯功能可讓您繪製具有漸層的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 元素、點陣圖、繪圖和影片，以及使用旋轉、縮放和傾斜來操作。 下圖提供您可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 筆刷達到許多效果的範例。

![圖例中顯示不同的 WPF 筆刷和 [小畫家] 項目。](./media/index/brushes-paint-elements.png)

如需詳細資訊，請參閱 [WPF 筆刷概觀](wpf-brushes-overview.md)。 如需簡介範例，請參閱[筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。

<a name="rendering"></a>

## <a name="3-d-rendering"></a>3D 轉譯

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供一組 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 轉譯功能，和 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 圖形支援整合，讓您建立更有趣的版面配置、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 及資料視覺效果。 另一方面，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可讓您將 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 影像轉譯到 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 圖形的表面上，如下圖所示範。

![示範以不同的紋理 3d 圖形的範例螢幕擷取畫面。](./media/index/visual-three-dimensional-shape.png)

如需詳細資訊，請參閱 [3D 圖形診斷](3-d-graphics-overview.md)。 如需簡介範例，請參閱 [3D 單色範例](https://go.microsoft.com/fwlink/?LinkID=159964)。

<a name="animation"></a>

## <a name="animation"></a>動畫

使用動畫讓控制項和元素放大、搖晃、旋轉和淡出，以及建立有趣的網頁切換及執行其他工作。 因為 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可讓您以動畫顯示大部分屬性，您不只可以動畫顯示大部分 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 物件，也可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 以動畫顯示您所建立的自訂物件。

![立方體動畫的螢幕擷取畫面。](./media/index/animate-custom-objects.png)

如需詳細資訊，請參閱 [動畫概觀](animation-overview.md)。 如需簡介範例，請參閱[動畫範例圖庫](https://go.microsoft.com/fwlink/?LinkID=159969)。

<a name="media"></a>

## <a name="media"></a>媒體

影像、視訊和音訊都是以媒體功能豐富的方式傳達資訊和使用者體驗。

### <a name="images"></a>影像

包括圖示、背景，甚至動畫組件的影像，是大部分應用程式的核心組件。 因為您經常需要使用影像，所以 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 公開能以各種不同方式處理的功能。 下圖顯示眾多方式的其中之一。

![樣式設定範例螢幕擷取畫面](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

如需詳細資訊，請參閱 [影像處理概觀](imaging-overview.md)。

### <a name="video-and-audio"></a>視訊和音訊

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 圖形功能的核心功能就是提供原生支援，以用於處理多媒體，包括視訊和音訊。 下列範例示範如何將媒體播放程式插入至應用程式。

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement> 是可播放視訊和音訊，而是可延伸，足以讓您輕鬆建立自訂[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]。

如需詳細資訊，請參閱[多媒體概觀](multimedia-overview.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
- [動畫和計時 how to 主題](animation-and-timing-how-to-topics.md)
- [立體圖形概觀](3-d-graphics-overview.md)
- [多媒體概觀](multimedia-overview.md)
