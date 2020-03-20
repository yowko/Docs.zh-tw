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
# <a name="graphics-and-multimedia"></a><span data-ttu-id="4d4a9-102">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="4d4a9-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="4d4a9-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 支援多媒體、向量圖形、動畫和內容組合，方便開發人員建置有趣的使用者介面和內容。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="4d4a9-104">使用 Visual Studio，您可以創建向量圖形或複雜動畫，並將媒體集成到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-104">Using Visual Studio, you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="4d4a9-105">本主題介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的圖形、動畫和媒體功能，其可讓您將圖形、轉換效果、音效以及視訊新增至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="4d4a9-106">強烈建議不要在 Windows 服務中使用 WPF 類型。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="4d4a9-107">如果您嘗試在 Windows 服務中使用 WPF 類型，該服務可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="4d4a9-108">WPF 4 中圖形和多媒體的新功能</span><span class="sxs-lookup"><span data-stu-id="4d4a9-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="4d4a9-109">圖形和動畫有數項相關變更。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="4d4a9-110">版面配置進位</span><span class="sxs-lookup"><span data-stu-id="4d4a9-110">Layout Rounding</span></span>

  <span data-ttu-id="4d4a9-111">當物件邊緣位於像素裝置中間時，DPI 獨立圖形系統可以建立轉譯成品，例如模糊或半透明的邊緣。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="4d4a9-112">先前的 WPF 版本包含像素貼齊功能來協助處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="4d4a9-113">Silverlight 2 引進版面配置進位，這是另一種移動元素以讓邊緣落在整個像素邊界上的方法。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="4d4a9-114">WPF 現在支援佈局舍入，<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>在 上<xref:System.Windows.FrameworkElement>附加屬性。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="4d4a9-115">快取的組合</span><span class="sxs-lookup"><span data-stu-id="4d4a9-115">Cached Composition</span></span>

  <span data-ttu-id="4d4a9-116">通過使用 new<xref:System.Windows.Media.BitmapCache>和<xref:System.Windows.Media.BitmapCacheBrush>類，可以將視覺化樹的複雜部分緩存為點陣圖，並極大地縮短渲染時間。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="4d4a9-117">點陣圖仍可持續回應滑鼠點選之類的使用者輸入，您也可以將它繪製在其他元素上，就像筆刷一般。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="4d4a9-118">像素著色器 3 支援</span><span class="sxs-lookup"><span data-stu-id="4d4a9-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="4d4a9-119">WPF 4 基於 WPF 3.5 SP1 中引入<xref:System.Windows.Media.Effects.ShaderEffect>的支援，允許應用程式使用圖元分片 （PS） 版本 3.0 寫入效果。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="4d4a9-120">PS 3.0 著色器模型比 PS 2.0 更為複雜，其在支援的硬體上允許使用更多效果。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="4d4a9-121">Easing 函式</span><span class="sxs-lookup"><span data-stu-id="4d4a9-121">Easing Functions</span></span>

  <span data-ttu-id="4d4a9-122">您可以利用 Easing 函式讓您進一步控制動畫的行為來美化動畫。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="4d4a9-123">例如，可以將 對<xref:System.Windows.Media.Animation.ElasticEase>動畫應用，為動畫提供彈簧行為。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="4d4a9-124">有關詳細資訊，請參閱命名空間中的<xref:System.Windows.Media.Animation>緩動類型。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="4d4a9-125">圖形和轉譯</span><span class="sxs-lookup"><span data-stu-id="4d4a9-125">Graphics and Rendering</span></span>

<span data-ttu-id="4d4a9-126">WPF 可支援高品質的 2D 圖形。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-126">WPF includes support for high quality 2-D graphics.</span></span> <span data-ttu-id="4d4a9-127">這些功能包括筆刷、幾何、影像、圖形及轉換。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="4d4a9-128">如需詳細資訊，請參閱[圖形](graphics.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="4d4a9-129">圖形元素的呈現基於類<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="4d4a9-130">螢幕上視覺物件的結構是由視覺化樹狀結構描繪。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="4d4a9-131">如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2-d-shapes"></a><span data-ttu-id="4d4a9-132">2D 圖案</span><span class="sxs-lookup"><span data-stu-id="4d4a9-132">2-D Shapes</span></span>

<span data-ttu-id="4d4a9-133">WPF 提供了常用的向量繪製的二維形狀（如矩形和橢圓）的庫，下圖顯示了這些形狀。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-133">WPF provides a library of commonly used, vector-drawn 2-D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![顯示橢圓和矩形的圖表。](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="4d4a9-135">這些固有的 WPF 形狀不僅僅是形狀：它們是可程式設計元素，它們實現了您期望從最常見的控制項（包括鍵盤和滑鼠輸入）中實現的許多功能。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-135">These intrinsic WPF shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="4d4a9-136">下面的示例演示如何處理通過按一下<xref:System.Windows.UIElement.MouseUp><xref:System.Windows.Shapes.Ellipse>元素引發的事件。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="4d4a9-137">下圖顯示上述 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記和程式碼後置的輸出。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![一個留言框，上面寫著"你點擊了橢圓！](./media/index/messagebox-text-output.png)

<span data-ttu-id="4d4a9-139">有關詳細資訊，請參閱[WPF 概述中的形狀和基本圖形](shapes-and-basic-drawing-in-wpf-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="4d4a9-140">如需簡介範例，請參閱[圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-140">For an introductory sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>

### <a name="2-d-geometries"></a><span data-ttu-id="4d4a9-141">2D 幾何</span><span class="sxs-lookup"><span data-stu-id="4d4a9-141">2-D Geometries</span></span>

<span data-ttu-id="4d4a9-142">當 WPF 提供的二維形狀不足時，可以使用 WPF 支援幾何體和路徑創建自己的形狀和路徑。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-142">When the 2-D shapes that WPF provides are not sufficient, you can use WPF support for geometries and paths to create your own.</span></span> <span data-ttu-id="4d4a9-143">下圖顯示了如何使用幾何圖形創建形狀（作為繪圖畫筆）和剪輯其他 WPF 元素。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other WPF elements.</span></span>

![顯示如何使用幾何圖形創建形狀的螢幕截圖。](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="4d4a9-145">有關詳細資訊，請參閱[幾何概述](geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="4d4a9-146">如需簡介範例，請參閱[幾何範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-146">For an introductory sample, see [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

### <a name="2-d-effects"></a><span data-ttu-id="4d4a9-147">2D 效果</span><span class="sxs-lookup"><span data-stu-id="4d4a9-147">2-D Effects</span></span>

<span data-ttu-id="4d4a9-148">WPF 提供了一個二維類庫，可用於創建各種效果。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-148">WPF provides a library of 2-D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="4d4a9-149">WPF 的二維渲染功能提供了繪製[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]具有漸變、點陣圖、繪圖和視頻的元素的能力;並使用旋轉、縮放和傾斜來操作它們。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-149">The 2-D rendering capability of WPF provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="4d4a9-150">下圖舉例說明了使用 WPF 畫筆可以實現的許多效果。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-150">The following illustration gives an example of the many effects you can achieve by using WPF brushes.</span></span>

![顯示不同 WPF 畫筆和油漆元素的插圖。](./media/index/brushes-paint-elements.png)

<span data-ttu-id="4d4a9-152">有關詳細資訊，請參閱[WPF 畫筆概述](wpf-brushes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="4d4a9-153">如需簡介範例，請參閱[筆刷範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-153">For an introductory sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>

<a name="rendering"></a>

## <a name="3-d-rendering"></a><span data-ttu-id="4d4a9-154">3D 轉譯</span><span class="sxs-lookup"><span data-stu-id="4d4a9-154">3-D Rendering</span></span>

<span data-ttu-id="4d4a9-155">WPF 提供一組三維渲染功能，這些功能與 WPF 中的二維圖形支援集成，以便創建更令人興奮的佈局、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]和資料視覺化。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-155">WPF provides a set of 3-D rendering capabilities that integrate with 2-D graphics support in WPF in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="4d4a9-156">在頻譜的一端，WPF 使您能夠將二維圖像渲染到三維形狀的表面上，下圖演示了這一點。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-156">At one end of the spectrum, WPF enables you to render 2-D images onto the surfaces of 3-D shapes, which the following illustration demonstrates.</span></span>

![顯示具有不同紋理的三維形狀的示例螢幕截圖。](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="4d4a9-158">有關詳細資訊，請參閱[三維圖形概述](3-d-graphics-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-158">For more information, see [3-D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="4d4a9-159">如需簡介範例，請參閱 [3D 單色範例](https://go.microsoft.com/fwlink/?LinkID=159964)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-159">For an introductory sample, see [3-D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="4d4a9-160">動畫</span><span class="sxs-lookup"><span data-stu-id="4d4a9-160">Animation</span></span>

<span data-ttu-id="4d4a9-161">使用動畫讓控制項和元素放大、搖晃、旋轉和淡出，以及建立有趣的網頁切換及執行其他工作。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="4d4a9-162">由於 WPF 使您能夠為大多數屬性設置動畫，因此不僅可以為大多數 WPF 物件設置動畫，還可以使用 WPF 為創建的自訂物件設置動畫。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-162">Because WPF enables you to animate most properties, not only can you animate most WPF objects, you can also use WPF to animate custom objects that you create.</span></span>

![動畫立方體的螢幕截圖。](./media/index/animate-custom-objects.png)

<span data-ttu-id="4d4a9-164">有關詳細資訊，請參閱[動畫概述](animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="4d4a9-165">如需簡介範例，請參閱[動畫範例圖庫](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-165">For an introductory sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="4d4a9-166">媒體</span><span class="sxs-lookup"><span data-stu-id="4d4a9-166">Media</span></span>

<span data-ttu-id="4d4a9-167">影像、視訊和音訊都是以媒體功能豐富的方式傳達資訊和使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="4d4a9-168">影像</span><span class="sxs-lookup"><span data-stu-id="4d4a9-168">Images</span></span>

<span data-ttu-id="4d4a9-169">包括圖示、背景，甚至動畫組件的影像，是大部分應用程式的核心組件。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="4d4a9-170">由於您經常需要使用圖像，WPF 公開了以各種方式使用它們的能力。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-170">Because you frequently need to use images, WPF exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="4d4a9-171">下圖顯示眾多方式的其中之一。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="4d4a9-172">![樣式示例螢幕截圖](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="4d4a9-172">![Styling sample screenshot](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="4d4a9-173">有關詳細資訊，請參閱[映射概述](imaging-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="4d4a9-174">視訊和音訊</span><span class="sxs-lookup"><span data-stu-id="4d4a9-174">Video and Audio</span></span>

<span data-ttu-id="4d4a9-175">WPF 圖形功能的核心功能是提供用於多媒體（包括視頻和音訊）的本機支援。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-175">A core feature of the graphics capabilities of WPF is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="4d4a9-176">下列範例示範如何將媒體播放程式插入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="4d4a9-177"><xref:System.Windows.Controls.MediaElement>能夠同時播放視頻和音訊，並且可擴展到足以輕鬆創建自訂 UIs。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="4d4a9-178">如需詳細資訊，請參閱[多媒體概觀](multimedia-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4a9-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d4a9-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d4a9-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="4d4a9-180">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="4d4a9-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="4d4a9-181">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="4d4a9-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="4d4a9-182">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="4d4a9-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="4d4a9-183">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="4d4a9-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="4d4a9-184">動畫和計時 HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="4d4a9-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="4d4a9-185">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="4d4a9-185">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="4d4a9-186">多媒體概觀</span><span class="sxs-lookup"><span data-stu-id="4d4a9-186">Multimedia Overview</span></span>](multimedia-overview.md)
