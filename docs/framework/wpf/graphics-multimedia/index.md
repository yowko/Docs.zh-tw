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
ms.openlocfilehash: be8dcfce44347e8099e8cfa693bcee341514de2b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291436"
---
# <a name="graphics-and-multimedia"></a>圖形和多媒體

<a name="introduction"></a>
 @ no__t-2 提供多媒體、向量圖形、動畫和內容撰寫的支援，讓開發人員輕鬆建立有趣的使用者介面和內容。 使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，您可以建立向量圖形或複雜的動畫，並將媒體整合到應用程式中。

本主題介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的圖形、動畫和媒體功能，其可讓您將圖形、轉換效果、音效以及視訊新增至您的應用程式。

> [!NOTE]
> 強烈建議不要在 Windows 服務中使用 WPF 類型。 如果您嘗試在 Windows 服務中使用 WPF 類型，該服務可能無法如預期般運作。

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>WPF 4 中圖形和多媒體的新功能

圖形和動畫有數項相關變更。

- 版面配置進位

  當物件邊緣位於像素裝置中間時，DPI 獨立圖形系統可以建立轉譯成品，例如模糊或半透明的邊緣。 先前的 WPF 版本包含像素貼齊功能來協助處理這種情況。 Silverlight 2 引進版面配置進位，這是另一種移動元素以讓邊緣落在整個像素邊界上的方法。 WPF 現在支援在 <xref:System.Windows.FrameworkElement> 上使用 @no__t 0 附加屬性進行版面配置舍入。

- 快取的組合

  藉由使用新的 <xref:System.Windows.Media.BitmapCache> 和 @no__t 1 類別，您可以將視覺化樹狀結構的複雜部分快取為點陣圖，並大幅改善轉譯時間。 點陣圖仍可持續回應滑鼠點選之類的使用者輸入，您也可以將它繪製在其他元素上，就像筆刷一般。

- 像素著色器 3 支援

  WPF 4 是以 WPF 3.5 SP1 中所引進的 @no__t 0 支援為基礎，藉由允許應用程式使用圖元著色器（PS）3.0 版來寫入效果。 PS 3.0 著色器模型比 PS 2.0 更為複雜，其在支援的硬體上允許使用更多效果。

- Easing 函式

  您可以利用 Easing 函式讓您進一步控制動畫的行為來美化動畫。 例如，您可以將 <xref:System.Windows.Media.Animation.ElasticEase> 套用至動畫，為動畫提供 springy 的行為。 如需詳細資訊，請參閱 <xref:System.Windows.Media.Animation> 命名空間中的緩動類型。

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>圖形和轉譯

WPF 可支援高品質的 2D 圖形。 這些功能包括筆刷、幾何、影像、圖形及轉換。 如需詳細資訊，請參閱[圖形](graphics.md)。 圖形元素的轉譯是以 @no__t 0 類別為基礎。 螢幕上視覺物件的結構是由視覺化樹狀結構描繪。 如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)。

### <a name="2-d-shapes"></a>2D 圖案

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供常用的向量繪製2D 圖形的程式庫，例如矩形和橢圓形，如下圖所示。

![顯示橢圓形和矩形的圖表。](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

這些內建 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 圖形不只是圖形︰它們也是可程式化元素，能實作許多最常見控制項的功能，包括鍵盤和滑鼠輸入。 下列範例示範如何處理藉由按一下 <xref:System.Windows.Shapes.Ellipse> 元素所引發的 <xref:System.Windows.UIElement.MouseUp> 事件。

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

![指出「您已按下橢圓形！」的訊息方塊](./media/index/messagebox-text-output.png)

如需詳細資訊，請參閱 [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)。 如需簡介範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。

### <a name="2-d-geometries"></a>2D 幾何

當 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供的2D 圖形不足時，您可以使用幾何和路徑的 @no__t 1 支援來建立自己的 geometry 和 path。 下圖示範如何使用幾何來建立圖形，當做繪圖筆刷並裁剪其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 元素。

![螢幕擷取畫面：顯示如何使用幾何來建立圖形。](./media/index/use-geometries-create-shapes.png)

如需詳細資訊，請參閱[幾何概觀](geometry-overview.md)。 如需簡介範例，請參閱[幾何範例](https://go.microsoft.com/fwlink/?LinkID=159989)。

### <a name="2-d-effects"></a>2D 效果

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供2D 類別的程式庫，可讓您用來建立各種效果。 @No__t-0 的2-d 轉譯功能可讓您繪製具有漸層、點陣圖、繪圖和影片的 @no__t 1 專案;並使用旋轉、縮放和扭曲來操作這些專案。 下圖提供您可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 筆刷達到許多效果的範例。

![此圖顯示不同的 WPF 筆刷和油漆元素。](./media/index/brushes-paint-elements.png)

如需詳細資訊，請參閱 [WPF 筆刷概觀](wpf-brushes-overview.md)。 如需簡介範例，請參閱[筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。

<a name="rendering"></a>

## <a name="3-d-rendering"></a>3D 轉譯

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供一組3D 轉譯功能，可與 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的2D 圖形支援整合，讓您能夠建立更棒的版面配置、@no__t 2 和資料視覺效果。 在頻譜的一端，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可讓您將2D 影像轉譯到立體圖形的表面，如下圖所示。

![顯示具有不同材質之3D 圖形的範例螢幕擷取畫面。](./media/index/visual-three-dimensional-shape.png)

如需詳細資訊，請參閱 [3D 圖形診斷](3-d-graphics-overview.md)。 如需簡介範例，請參閱 [3D 單色範例](https://go.microsoft.com/fwlink/?LinkID=159964)。

<a name="animation"></a>

## <a name="animation"></a>動畫

使用動畫讓控制項和元素放大、搖晃、旋轉和淡出，以及建立有趣的網頁切換及執行其他工作。 因為 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可讓您以動畫顯示大部分屬性，您不只可以動畫顯示大部分 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 物件，也可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 以動畫顯示您所建立的自訂物件。

![動畫 cube 的螢幕擷取畫面。](./media/index/animate-custom-objects.png)

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

<xref:System.Windows.Controls.MediaElement> 能夠同時播放影片和音訊，而且可以進行擴充，讓自訂 Ui 的建立變得輕鬆。

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
