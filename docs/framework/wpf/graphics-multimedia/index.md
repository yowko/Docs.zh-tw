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
ms.openlocfilehash: 56a69c10a420e399478a0d617d30380ff5217e9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186736"
---
# <a name="graphics-and-multimedia"></a>圖形和多媒體

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 支援多媒體、向量圖形、動畫和內容組合，方便開發人員建置有趣的使用者介面和內容。 使用 Visual Studio，您可以創建向量圖形或複雜動畫，並將媒體集成到應用程式中。

本主題介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的圖形、動畫和媒體功能，其可讓您將圖形、轉換效果、音效以及視訊新增至您的應用程式。

> [!NOTE]
> 強烈建議不要在 Windows 服務中使用 WPF 類型。 如果您嘗試在 Windows 服務中使用 WPF 類型，該服務可能無法如預期般運作。

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>WPF 4 中圖形和多媒體的新功能

圖形和動畫有數項相關變更。

- 版面配置進位

  當物件邊緣位於像素裝置中間時，DPI 獨立圖形系統可以建立轉譯成品，例如模糊或半透明的邊緣。 先前的 WPF 版本包含像素貼齊功能來協助處理這種情況。 Silverlight 2 引進版面配置進位，這是另一種移動元素以讓邊緣落在整個像素邊界上的方法。 WPF 現在支援佈局舍入，<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>在 上<xref:System.Windows.FrameworkElement>附加屬性。

- 快取的組合

  通過使用 new<xref:System.Windows.Media.BitmapCache>和<xref:System.Windows.Media.BitmapCacheBrush>類，可以將視覺化樹的複雜部分緩存為點陣圖，並極大地縮短渲染時間。 點陣圖仍可持續回應滑鼠點選之類的使用者輸入，您也可以將它繪製在其他元素上，就像筆刷一般。

- 像素著色器 3 支援

  WPF 4 基於 WPF 3.5 SP1 中引入<xref:System.Windows.Media.Effects.ShaderEffect>的支援，允許應用程式使用圖元分片 （PS） 版本 3.0 寫入效果。 PS 3.0 著色器模型比 PS 2.0 更為複雜，其在支援的硬體上允許使用更多效果。

- Easing 函式

  您可以利用 Easing 函式讓您進一步控制動畫的行為來美化動畫。 例如，可以將 對<xref:System.Windows.Media.Animation.ElasticEase>動畫應用，為動畫提供彈簧行為。 有關詳細資訊，請參閱命名空間中的<xref:System.Windows.Media.Animation>緩動類型。

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>圖形和轉譯

WPF 可支援高品質的 2D 圖形。 這些功能包括筆刷、幾何、影像、圖形及轉換。 如需詳細資訊，請參閱[圖形](graphics.md)。 圖形元素的呈現基於類<xref:System.Windows.Media.Visual>。 螢幕上視覺物件的結構是由視覺化樹狀結構描繪。 如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)。

### <a name="2-d-shapes"></a>2D 圖案

WPF 提供了常用的向量繪製的二維形狀（如矩形和橢圓）的庫，下圖顯示了這些形狀。

![顯示橢圓和矩形的圖表。](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

這些固有的 WPF 形狀不僅僅是形狀：它們是可程式設計元素，它們實現了您期望從最常見的控制項（包括鍵盤和滑鼠輸入）中實現的許多功能。 下面的示例演示如何處理通過按一下<xref:System.Windows.UIElement.MouseUp><xref:System.Windows.Shapes.Ellipse>元素引發的事件。

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

![一個留言框，上面寫著"你點擊了橢圓！](./media/index/messagebox-text-output.png)

有關詳細資訊，請參閱[WPF 概述中的形狀和基本圖形](shapes-and-basic-drawing-in-wpf-overview.md)。 如需簡介範例，請參閱[圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。

### <a name="2-d-geometries"></a>2D 幾何

當 WPF 提供的二維形狀不足時，可以使用 WPF 支援幾何體和路徑創建自己的形狀和路徑。 下圖顯示了如何使用幾何圖形創建形狀（作為繪圖畫筆）和剪輯其他 WPF 元素。

![顯示如何使用幾何圖形創建形狀的螢幕截圖。](./media/index/use-geometries-create-shapes.png)

有關詳細資訊，請參閱[幾何概述](geometry-overview.md)。 如需簡介範例，請參閱[幾何範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)。

### <a name="2-d-effects"></a>2D 效果

WPF 提供了一個二維類庫，可用於創建各種效果。 WPF 的二維渲染功能提供了繪製[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]具有漸變、點陣圖、繪圖和視頻的元素的能力;並使用旋轉、縮放和傾斜來操作它們。 下圖舉例說明了使用 WPF 畫筆可以實現的許多效果。

![顯示不同 WPF 畫筆和油漆元素的插圖。](./media/index/brushes-paint-elements.png)

有關詳細資訊，請參閱[WPF 畫筆概述](wpf-brushes-overview.md)。 如需簡介範例，請參閱[筆刷範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。

<a name="rendering"></a>

## <a name="3-d-rendering"></a>3D 轉譯

WPF 提供一組三維渲染功能，這些功能與 WPF 中的二維圖形支援集成，以便創建更令人興奮的佈局、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]和資料視覺化。 在頻譜的一端，WPF 使您能夠將二維圖像渲染到三維形狀的表面上，下圖演示了這一點。

![顯示具有不同紋理的三維形狀的示例螢幕截圖。](./media/index/visual-three-dimensional-shape.png)

有關詳細資訊，請參閱[三維圖形概述](3-d-graphics-overview.md)。 如需簡介範例，請參閱 [3D 單色範例](https://go.microsoft.com/fwlink/?LinkID=159964)。

<a name="animation"></a>

## <a name="animation"></a>動畫

使用動畫讓控制項和元素放大、搖晃、旋轉和淡出，以及建立有趣的網頁切換及執行其他工作。 由於 WPF 使您能夠為大多數屬性設置動畫，因此不僅可以為大多數 WPF 物件設置動畫，還可以使用 WPF 為創建的自訂物件設置動畫。

![動畫立方體的螢幕截圖。](./media/index/animate-custom-objects.png)

有關詳細資訊，請參閱[動畫概述](animation-overview.md)。 如需簡介範例，請參閱[動畫範例圖庫](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)。

<a name="media"></a>

## <a name="media"></a>媒體

影像、視訊和音訊都是以媒體功能豐富的方式傳達資訊和使用者體驗。

### <a name="images"></a>影像

包括圖示、背景，甚至動畫組件的影像，是大部分應用程式的核心組件。 由於您經常需要使用圖像，WPF 公開了以各種方式使用它們的能力。 下圖顯示眾多方式的其中之一。

![樣式示例螢幕截圖](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

有關詳細資訊，請參閱[映射概述](imaging-overview.md)。

### <a name="video-and-audio"></a>視訊和音訊

WPF 圖形功能的核心功能是提供用於多媒體（包括視頻和音訊）的本機支援。 下列範例示範如何將媒體播放程式插入至應用程式。

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement>能夠同時播放視頻和音訊，並且可擴展到足以輕鬆創建自訂 UIs。

如需詳細資訊，請參閱[多媒體概觀](multimedia-overview.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
- [動畫和計時 HOW TO 主題](animation-and-timing-how-to-topics.md)
- [立體圖形概觀](3-d-graphics-overview.md)
- [多媒體概觀](multimedia-overview.md)
