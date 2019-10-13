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
# <a name="graphics-and-multimedia"></a><span data-ttu-id="348e0-102">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="348e0-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
 <span data-ttu-id="348e0-103">@ no__t-2 提供多媒體、向量圖形、動畫和內容撰寫的支援，讓開發人員輕鬆建立有趣的使用者介面和內容。</span><span class="sxs-lookup"><span data-stu-id="348e0-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="348e0-104">使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，您可以建立向量圖形或複雜的動畫，並將媒體整合到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="348e0-104">Using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="348e0-105">本主題介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的圖形、動畫和媒體功能，其可讓您將圖形、轉換效果、音效以及視訊新增至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="348e0-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="348e0-106">強烈建議不要在 Windows 服務中使用 WPF 類型。</span><span class="sxs-lookup"><span data-stu-id="348e0-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="348e0-107">如果您嘗試在 Windows 服務中使用 WPF 類型，該服務可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="348e0-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="348e0-108">WPF 4 中圖形和多媒體的新功能</span><span class="sxs-lookup"><span data-stu-id="348e0-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="348e0-109">圖形和動畫有數項相關變更。</span><span class="sxs-lookup"><span data-stu-id="348e0-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="348e0-110">版面配置進位</span><span class="sxs-lookup"><span data-stu-id="348e0-110">Layout Rounding</span></span>

  <span data-ttu-id="348e0-111">當物件邊緣位於像素裝置中間時，DPI 獨立圖形系統可以建立轉譯成品，例如模糊或半透明的邊緣。</span><span class="sxs-lookup"><span data-stu-id="348e0-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="348e0-112">先前的 WPF 版本包含像素貼齊功能來協助處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="348e0-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="348e0-113">Silverlight 2 引進版面配置進位，這是另一種移動元素以讓邊緣落在整個像素邊界上的方法。</span><span class="sxs-lookup"><span data-stu-id="348e0-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="348e0-114">WPF 現在支援在 <xref:System.Windows.FrameworkElement> 上使用 @no__t 0 附加屬性進行版面配置舍入。</span><span class="sxs-lookup"><span data-stu-id="348e0-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="348e0-115">快取的組合</span><span class="sxs-lookup"><span data-stu-id="348e0-115">Cached Composition</span></span>

  <span data-ttu-id="348e0-116">藉由使用新的 <xref:System.Windows.Media.BitmapCache> 和 @no__t 1 類別，您可以將視覺化樹狀結構的複雜部分快取為點陣圖，並大幅改善轉譯時間。</span><span class="sxs-lookup"><span data-stu-id="348e0-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="348e0-117">點陣圖仍可持續回應滑鼠點選之類的使用者輸入，您也可以將它繪製在其他元素上，就像筆刷一般。</span><span class="sxs-lookup"><span data-stu-id="348e0-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="348e0-118">像素著色器 3 支援</span><span class="sxs-lookup"><span data-stu-id="348e0-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="348e0-119">WPF 4 是以 WPF 3.5 SP1 中所引進的 @no__t 0 支援為基礎，藉由允許應用程式使用圖元著色器（PS）3.0 版來寫入效果。</span><span class="sxs-lookup"><span data-stu-id="348e0-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="348e0-120">PS 3.0 著色器模型比 PS 2.0 更為複雜，其在支援的硬體上允許使用更多效果。</span><span class="sxs-lookup"><span data-stu-id="348e0-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="348e0-121">Easing 函式</span><span class="sxs-lookup"><span data-stu-id="348e0-121">Easing Functions</span></span>

  <span data-ttu-id="348e0-122">您可以利用 Easing 函式讓您進一步控制動畫的行為來美化動畫。</span><span class="sxs-lookup"><span data-stu-id="348e0-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="348e0-123">例如，您可以將 <xref:System.Windows.Media.Animation.ElasticEase> 套用至動畫，為動畫提供 springy 的行為。</span><span class="sxs-lookup"><span data-stu-id="348e0-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="348e0-124">如需詳細資訊，請參閱 <xref:System.Windows.Media.Animation> 命名空間中的緩動類型。</span><span class="sxs-lookup"><span data-stu-id="348e0-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="348e0-125">圖形和轉譯</span><span class="sxs-lookup"><span data-stu-id="348e0-125">Graphics and Rendering</span></span>

<span data-ttu-id="348e0-126">WPF 可支援高品質的 2D 圖形。</span><span class="sxs-lookup"><span data-stu-id="348e0-126">WPF includes support for high quality 2-D graphics.</span></span> <span data-ttu-id="348e0-127">這些功能包括筆刷、幾何、影像、圖形及轉換。</span><span class="sxs-lookup"><span data-stu-id="348e0-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="348e0-128">如需詳細資訊，請參閱[圖形](graphics.md)。</span><span class="sxs-lookup"><span data-stu-id="348e0-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="348e0-129">圖形元素的轉譯是以 @no__t 0 類別為基礎。</span><span class="sxs-lookup"><span data-stu-id="348e0-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="348e0-130">螢幕上視覺物件的結構是由視覺化樹狀結構描繪。</span><span class="sxs-lookup"><span data-stu-id="348e0-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="348e0-131">如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="348e0-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2-d-shapes"></a><span data-ttu-id="348e0-132">2D 圖案</span><span class="sxs-lookup"><span data-stu-id="348e0-132">2-D Shapes</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="348e0-133">提供常用的向量繪製2D 圖形的程式庫，例如矩形和橢圓形，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="348e0-133">provides a library of commonly used, vector-drawn 2-D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![顯示橢圓形和矩形的圖表。](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="348e0-135">這些內建 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 圖形不只是圖形︰它們也是可程式化元素，能實作許多最常見控制項的功能，包括鍵盤和滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="348e0-135">These intrinsic [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="348e0-136">下列範例示範如何處理藉由按一下 <xref:System.Windows.Shapes.Ellipse> 元素所引發的 <xref:System.Windows.UIElement.MouseUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="348e0-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="348e0-137">下圖顯示上述 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記和程式碼後置的輸出。</span><span class="sxs-lookup"><span data-stu-id="348e0-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![指出「您已按下橢圓形！」的訊息方塊](./media/index/messagebox-text-output.png)

<span data-ttu-id="348e0-139">如需詳細資訊，請參閱 [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="348e0-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="348e0-140">如需簡介範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="348e0-140">For an introductory sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>

### <a name="2-d-geometries"></a><span data-ttu-id="348e0-141">2D 幾何</span><span class="sxs-lookup"><span data-stu-id="348e0-141">2-D Geometries</span></span>

<span data-ttu-id="348e0-142">當 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供的2D 圖形不足時，您可以使用幾何和路徑的 @no__t 1 支援來建立自己的 geometry 和 path。</span><span class="sxs-lookup"><span data-stu-id="348e0-142">When the 2-D shapes that [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides are not sufficient, you can use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] support for geometries and paths to create your own.</span></span> <span data-ttu-id="348e0-143">下圖示範如何使用幾何來建立圖形，當做繪圖筆刷並裁剪其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 元素。</span><span class="sxs-lookup"><span data-stu-id="348e0-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elements.</span></span>

![螢幕擷取畫面：顯示如何使用幾何來建立圖形。](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="348e0-145">如需詳細資訊，請參閱[幾何概觀](geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="348e0-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="348e0-146">如需簡介範例，請參閱[幾何範例](https://go.microsoft.com/fwlink/?LinkID=159989)。</span><span class="sxs-lookup"><span data-stu-id="348e0-146">For an introductory sample, see [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>

### <a name="2-d-effects"></a><span data-ttu-id="348e0-147">2D 效果</span><span class="sxs-lookup"><span data-stu-id="348e0-147">2-D Effects</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="348e0-148">提供2D 類別的程式庫，可讓您用來建立各種效果。</span><span class="sxs-lookup"><span data-stu-id="348e0-148">provides a library of 2-D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="348e0-149">@No__t-0 的2-d 轉譯功能可讓您繪製具有漸層、點陣圖、繪圖和影片的 @no__t 1 專案;並使用旋轉、縮放和扭曲來操作這些專案。</span><span class="sxs-lookup"><span data-stu-id="348e0-149">The 2-D rendering capability of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="348e0-150">下圖提供您可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 筆刷達到許多效果的範例。</span><span class="sxs-lookup"><span data-stu-id="348e0-150">The following illustration gives an example of the many effects you can achieve by using [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] brushes.</span></span>

![此圖顯示不同的 WPF 筆刷和油漆元素。](./media/index/brushes-paint-elements.png)

<span data-ttu-id="348e0-152">如需詳細資訊，請參閱 [WPF 筆刷概觀](wpf-brushes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="348e0-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="348e0-153">如需簡介範例，請參閱[筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="348e0-153">For an introductory sample, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>

<a name="rendering"></a>

## <a name="3-d-rendering"></a><span data-ttu-id="348e0-154">3D 轉譯</span><span class="sxs-lookup"><span data-stu-id="348e0-154">3-D Rendering</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="348e0-155">提供一組3D 轉譯功能，可與 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的2D 圖形支援整合，讓您能夠建立更棒的版面配置、@no__t 2 和資料視覺效果。</span><span class="sxs-lookup"><span data-stu-id="348e0-155">provides a set of 3-D rendering capabilities that integrate with 2-D graphics support in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="348e0-156">在頻譜的一端，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可讓您將2D 影像轉譯到立體圖形的表面，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="348e0-156">At one end of the spectrum, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to render 2-D images onto the surfaces of 3-D shapes, which the following illustration demonstrates.</span></span>

![顯示具有不同材質之3D 圖形的範例螢幕擷取畫面。](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="348e0-158">如需詳細資訊，請參閱 [3D 圖形診斷](3-d-graphics-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="348e0-158">For more information, see [3-D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="348e0-159">如需簡介範例，請參閱 [3D 單色範例](https://go.microsoft.com/fwlink/?LinkID=159964)。</span><span class="sxs-lookup"><span data-stu-id="348e0-159">For an introductory sample, see [3-D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="348e0-160">動畫</span><span class="sxs-lookup"><span data-stu-id="348e0-160">Animation</span></span>

<span data-ttu-id="348e0-161">使用動畫讓控制項和元素放大、搖晃、旋轉和淡出，以及建立有趣的網頁切換及執行其他工作。</span><span class="sxs-lookup"><span data-stu-id="348e0-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="348e0-162">因為 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可讓您以動畫顯示大部分屬性，您不只可以動畫顯示大部分 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 物件，也可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 以動畫顯示您所建立的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="348e0-162">Because [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to animate most properties, not only can you animate most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objects, you can also use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to animate custom objects that you create.</span></span>

![動畫 cube 的螢幕擷取畫面。](./media/index/animate-custom-objects.png)

<span data-ttu-id="348e0-164">如需詳細資訊，請參閱 [動畫概觀](animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="348e0-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="348e0-165">如需簡介範例，請參閱[動畫範例圖庫](https://go.microsoft.com/fwlink/?LinkID=159969)。</span><span class="sxs-lookup"><span data-stu-id="348e0-165">For an introductory sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="348e0-166">媒體</span><span class="sxs-lookup"><span data-stu-id="348e0-166">Media</span></span>

<span data-ttu-id="348e0-167">影像、視訊和音訊都是以媒體功能豐富的方式傳達資訊和使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="348e0-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="348e0-168">影像</span><span class="sxs-lookup"><span data-stu-id="348e0-168">Images</span></span>

<span data-ttu-id="348e0-169">包括圖示、背景，甚至動畫組件的影像，是大部分應用程式的核心組件。</span><span class="sxs-lookup"><span data-stu-id="348e0-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="348e0-170">因為您經常需要使用影像，所以 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 公開能以各種不同方式處理的功能。</span><span class="sxs-lookup"><span data-stu-id="348e0-170">Because you frequently need to use images, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="348e0-171">下圖顯示眾多方式的其中之一。</span><span class="sxs-lookup"><span data-stu-id="348e0-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="348e0-172">![樣式設定範例螢幕擷取畫面](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="348e0-172">![Styling sample screenshot](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="348e0-173">如需詳細資訊，請參閱 [影像處理概觀](imaging-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="348e0-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="348e0-174">視訊和音訊</span><span class="sxs-lookup"><span data-stu-id="348e0-174">Video and Audio</span></span>

<span data-ttu-id="348e0-175">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 圖形功能的核心功能就是提供原生支援，以用於處理多媒體，包括視訊和音訊。</span><span class="sxs-lookup"><span data-stu-id="348e0-175">A core feature of the graphics capabilities of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="348e0-176">下列範例示範如何將媒體播放程式插入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="348e0-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="348e0-177"><xref:System.Windows.Controls.MediaElement> 能夠同時播放影片和音訊，而且可以進行擴充，讓自訂 Ui 的建立變得輕鬆。</span><span class="sxs-lookup"><span data-stu-id="348e0-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="348e0-178">如需詳細資訊，請參閱[多媒體概觀](multimedia-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="348e0-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="348e0-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="348e0-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="348e0-180">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="348e0-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="348e0-181">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="348e0-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="348e0-182">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="348e0-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="348e0-183">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="348e0-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="348e0-184">動畫和計時 how to 主題</span><span class="sxs-lookup"><span data-stu-id="348e0-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="348e0-185">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="348e0-185">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="348e0-186">多媒體概觀</span><span class="sxs-lookup"><span data-stu-id="348e0-186">Multimedia Overview</span></span>](multimedia-overview.md)
