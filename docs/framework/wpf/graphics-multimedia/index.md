---
title: "圖形和多媒體"
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
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e212de5f1f92a2a797da7f2534d28ff8b6dbdd12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="25737-102">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="25737-102">Graphics and Multimedia</span></span>
<a name="introduction"></a>
<span data-ttu-id="25737-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供支援多媒體、 向量圖形、 動畫和內容的組合，方便開發人員建置有趣的使用者介面和內容。</span><span class="sxs-lookup"><span data-stu-id="25737-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="25737-104">使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，您可以建立向量圖形或複雜的動畫，並將媒體整合到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="25737-104">Using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], you can create vector graphics or complex animations and integrate media into your applications.</span></span>  
  
 <span data-ttu-id="25737-105">本主題介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的圖形、動畫和媒體功能，其可讓您將圖形、轉換效果、音效以及視訊新增至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="25737-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25737-106">強烈建議不要在 Windows 服務中使用 WPF 類型。</span><span class="sxs-lookup"><span data-stu-id="25737-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="25737-107">如果您嘗試在 Windows 服務中使用 WPF 類型，該服務可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="25737-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="25737-108">WPF 4 中圖形和多媒體的新功能</span><span class="sxs-lookup"><span data-stu-id="25737-108">What's New with Graphics and Multimedia in WPF 4</span></span>  
 <span data-ttu-id="25737-109">圖形和動畫有數項相關變更。</span><span class="sxs-lookup"><span data-stu-id="25737-109">Several changes have been made related to graphics and animations.</span></span>  
  
-   <span data-ttu-id="25737-110">版面配置進位</span><span class="sxs-lookup"><span data-stu-id="25737-110">Layout Rounding</span></span>  
  
     <span data-ttu-id="25737-111">當物件邊緣位於像素裝置中間時，DPI 獨立圖形系統可以建立轉譯成品，例如模糊或半透明的邊緣。</span><span class="sxs-lookup"><span data-stu-id="25737-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="25737-112">先前的 WPF 版本包含像素貼齊功能來協助處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="25737-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="25737-113">Silverlight 2 引進版面配置進位，這是另一種移動元素以讓邊緣落在整個像素邊界上的方法。</span><span class="sxs-lookup"><span data-stu-id="25737-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="25737-114">WPF 現在支援版面配置進位與<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>附加屬性上<xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="25737-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>  
  
-   <span data-ttu-id="25737-115">快取的組合</span><span class="sxs-lookup"><span data-stu-id="25737-115">Cached Composition</span></span>  
  
     <span data-ttu-id="25737-116">使用新<xref:System.Windows.Media.BitmapCache>和<xref:System.Windows.Media.BitmapCacheBrush>類別，您可以快取複雜為點陣圖的視覺化樹狀結構的一部分，並大幅改善轉譯時間。</span><span class="sxs-lookup"><span data-stu-id="25737-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="25737-117">點陣圖仍可持續回應滑鼠點選之類的使用者輸入，您也可以將它繪製在其他元素上，就像筆刷一般。</span><span class="sxs-lookup"><span data-stu-id="25737-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>  
  
-   <span data-ttu-id="25737-118">像素著色器 3 支援</span><span class="sxs-lookup"><span data-stu-id="25737-118">Pixel Shader 3 Support</span></span>  
  
     <span data-ttu-id="25737-119">WPF 4 根據<xref:System.Windows.Media.Effects.ShaderEffect>WPF 3.5 SP1 中導入，藉由使用應用程式撰寫效果使用像素著色器 (PS) 3.0 版的支援。</span><span class="sxs-lookup"><span data-stu-id="25737-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="25737-120">PS 3.0 著色器模型比 PS 2.0 更為複雜，其在支援的硬體上允許使用更多效果。</span><span class="sxs-lookup"><span data-stu-id="25737-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>  
  
-   <span data-ttu-id="25737-121">Easing 函式</span><span class="sxs-lookup"><span data-stu-id="25737-121">Easing Functions</span></span>  
  
     <span data-ttu-id="25737-122">您可以利用 Easing 函式讓您進一步控制動畫的行為來美化動畫。</span><span class="sxs-lookup"><span data-stu-id="25737-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="25737-123">例如，您可以套用<xref:System.Windows.Media.Animation.ElasticEase>來提供彈性的行為動畫的動畫。</span><span class="sxs-lookup"><span data-stu-id="25737-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="25737-124">如需詳細資訊，請參閱中的加/減速類型<xref:System.Windows.Media.Animation>命名空間。</span><span class="sxs-lookup"><span data-stu-id="25737-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>  
  
<a name="graphics_and_rendering"></a>   
## <a name="graphics-and-rendering"></a><span data-ttu-id="25737-125">圖形和轉譯</span><span class="sxs-lookup"><span data-stu-id="25737-125">Graphics and Rendering</span></span>  
 <span data-ttu-id="25737-126">WPF 可支援高品質的 2D 圖形。</span><span class="sxs-lookup"><span data-stu-id="25737-126">WPF includes support for high quality 2-D graphics.</span></span> <span data-ttu-id="25737-127">這些功能包括筆刷、幾何、影像、圖形及轉換。</span><span class="sxs-lookup"><span data-stu-id="25737-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="25737-128">如需詳細資訊，請參閱[圖形](../../../../docs/framework/wpf/graphics-multimedia/graphics.md)。</span><span class="sxs-lookup"><span data-stu-id="25737-128">For more information, see [Graphics](../../../../docs/framework/wpf/graphics-multimedia/graphics.md).</span></span> <span data-ttu-id="25737-129">轉譯圖形化的項目根據<xref:System.Windows.Media.Visual>類別。</span><span class="sxs-lookup"><span data-stu-id="25737-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="25737-130">螢幕上視覺物件的結構是由視覺化樹狀結構描繪。</span><span class="sxs-lookup"><span data-stu-id="25737-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="25737-131">如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="25737-131">For more information, see [WPF Graphics Rendering Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span></span>  
  
### <a name="2-d-shapes"></a><span data-ttu-id="25737-132">2D 圖案</span><span class="sxs-lookup"><span data-stu-id="25737-132">2-D Shapes</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="25737-133"> 提供以向量繪製的常用 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 圖形圖庫，例如下圖所示的矩形和橢圓形。</span><span class="sxs-lookup"><span data-stu-id="25737-133"> provides a library of commonly used, vector-drawn [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>  
  
 <span data-ttu-id="25737-134">![橢圓形和矩形](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")</span><span class="sxs-lookup"><span data-stu-id="25737-134">![Ellipses and rectangles](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")</span></span>  
  
 <span data-ttu-id="25737-135">這些內建 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 圖形不只是圖形︰它們也是可程式化元素，能實作許多最常見控制項的功能，包括鍵盤和滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="25737-135">These intrinsic [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="25737-136">下列範例示範如何處理<xref:System.Windows.UIElement.MouseUp>按一下引發的事件<xref:System.Windows.Shapes.Ellipse>項目。</span><span class="sxs-lookup"><span data-stu-id="25737-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>  
  
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
  
 <span data-ttu-id="25737-137">下圖顯示上述 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記和程式碼後置的輸出。</span><span class="sxs-lookup"><span data-stu-id="25737-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>  
  
 <span data-ttu-id="25737-138">![包含 "you clicked the ellipse&#33;" 文字的視窗](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")</span><span class="sxs-lookup"><span data-stu-id="25737-138">![A window with the text "you clicked the ellipse&#33;"](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")</span></span>  
  
 <span data-ttu-id="25737-139">如需詳細資訊，請參閱 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="25737-139">For more information, see [Shapes and Basic Drawing in WPF Overview](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="25737-140">如需簡介範例，請參閱[圖形元素範例](http://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="25737-140">For an introductory sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
### <a name="2-d-geometries"></a><span data-ttu-id="25737-141">2D 幾何</span><span class="sxs-lookup"><span data-stu-id="25737-141">2-D Geometries</span></span>  
 <span data-ttu-id="25737-142">當 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供的 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 圖形不敷使用時，您可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 來支援您自己建立的幾何和路徑。</span><span class="sxs-lookup"><span data-stu-id="25737-142">When the [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes that [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides are not sufficient, you can use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] support for geometries and paths to create your own.</span></span> <span data-ttu-id="25737-143">下圖示範如何使用幾何來建立圖形，當做繪圖筆刷並裁剪其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 元素。</span><span class="sxs-lookup"><span data-stu-id="25737-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elements.</span></span>  
  
 <span data-ttu-id="25737-144">![Path 的各種用法](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")</span><span class="sxs-lookup"><span data-stu-id="25737-144">![Various uses of a Path](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")</span></span>  
  
 <span data-ttu-id="25737-145">如需詳細資訊，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="25737-145">For more information, see [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span> <span data-ttu-id="25737-146">如需簡介範例，請參閱[幾何範例](http://go.microsoft.com/fwlink/?LinkID=159989)。</span><span class="sxs-lookup"><span data-stu-id="25737-146">For an introductory sample, see [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
### <a name="2-d-effects"></a><span data-ttu-id="25737-147">2D 效果</span><span class="sxs-lookup"><span data-stu-id="25737-147">2-D Effects</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="25737-148"> 提供 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 類別的程式庫可讓您建立各種不同的效果。</span><span class="sxs-lookup"><span data-stu-id="25737-148"> provides a library of [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="25737-149">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 轉譯功能可讓您繪製具有漸層的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 元素、點陣圖、繪圖和影片，以及使用旋轉、縮放和傾斜來操作。</span><span class="sxs-lookup"><span data-stu-id="25737-149">The [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] rendering capability of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="25737-150">下圖提供您可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 筆刷達到許多效果的範例。</span><span class="sxs-lookup"><span data-stu-id="25737-150">The following illustration gives an example of the many effects you can achieve by using [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] brushes.</span></span>  
  
 <span data-ttu-id="25737-151">![不同筆刷的圖例](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")</span><span class="sxs-lookup"><span data-stu-id="25737-151">![Illustration of different brushes](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")</span></span>  
  
 <span data-ttu-id="25737-152">如需詳細資訊，請參閱 [WPF 筆刷概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="25737-152">For more information, see [WPF Brushes Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).</span></span> <span data-ttu-id="25737-153">如需簡介範例，請參閱[筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="25737-153">For an introductory sample, see [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
<a name="rendering"></a>   
## <a name="3-d-rendering"></a><span data-ttu-id="25737-154">3D 轉譯</span><span class="sxs-lookup"><span data-stu-id="25737-154">3-D Rendering</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="25737-155"> 提供一組 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 轉譯功能，和 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 圖形支援整合，讓您建立更有趣的版面配置、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 及資料視覺效果。</span><span class="sxs-lookup"><span data-stu-id="25737-155"> provides a set of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] rendering capabilities that integrate with [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] graphics support in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="25737-156">另一方面，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可讓您將 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 影像轉譯到 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 圖形的表面上，如下圖所示範。</span><span class="sxs-lookup"><span data-stu-id="25737-156">At one end of the spectrum, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to render [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] images onto the surfaces of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] shapes, which the following illustration demonstrates.</span></span>  
  
 <span data-ttu-id="25737-157">![Visual3D 範例螢幕擷取畫面](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")</span><span class="sxs-lookup"><span data-stu-id="25737-157">![Visual3D sample screen shot](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")</span></span>  
  
 <span data-ttu-id="25737-158">如需詳細資訊，請參閱 [3D 圖形診斷](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="25737-158">For more information, see [3-D Graphics Overview](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).</span></span> <span data-ttu-id="25737-159">如需簡介範例，請參閱 [3D 單色範例](http://go.microsoft.com/fwlink/?LinkID=159964)。</span><span class="sxs-lookup"><span data-stu-id="25737-159">For an introductory sample, see [3-D Solids Sample](http://go.microsoft.com/fwlink/?LinkID=159964).</span></span>  
  
<a name="animation"></a>   
## <a name="animation"></a><span data-ttu-id="25737-160">動畫</span><span class="sxs-lookup"><span data-stu-id="25737-160">Animation</span></span>  
 <span data-ttu-id="25737-161">使用動畫讓控制項和元素放大、搖晃、旋轉和淡出，以及建立有趣的網頁切換及執行其他工作。</span><span class="sxs-lookup"><span data-stu-id="25737-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="25737-162">因為 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可讓您以動畫顯示大部分屬性，您不只可以動畫顯示大部分 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 物件，也可以使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 以動畫顯示您所建立的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="25737-162">Because [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to animate most properties, not only can you animate most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objects, you can also use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to animate custom objects that you create.</span></span>  
  
 <span data-ttu-id="25737-163">![動畫效果立方體的影像](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")</span><span class="sxs-lookup"><span data-stu-id="25737-163">![Images of an animated cube](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")</span></span>  
  
 <span data-ttu-id="25737-164">如需詳細資訊，請參閱 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="25737-164">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="25737-165">如需簡介範例，請參閱[動畫範例圖庫](http://go.microsoft.com/fwlink/?LinkID=159969)。</span><span class="sxs-lookup"><span data-stu-id="25737-165">For an introductory sample, see [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
<a name="media"></a>   
## <a name="media"></a><span data-ttu-id="25737-166">媒體</span><span class="sxs-lookup"><span data-stu-id="25737-166">Media</span></span>  
 <span data-ttu-id="25737-167">影像、視訊和音訊都是以媒體功能豐富的方式傳達資訊和使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="25737-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>  
  
### <a name="images"></a><span data-ttu-id="25737-168">影像</span><span class="sxs-lookup"><span data-stu-id="25737-168">Images</span></span>  
 <span data-ttu-id="25737-169">包括圖示、背景，甚至動畫組件的影像，是大部分應用程式的核心組件。</span><span class="sxs-lookup"><span data-stu-id="25737-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="25737-170">因為您經常需要使用影像，所以 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 公開能以各種不同方式處理的功能。</span><span class="sxs-lookup"><span data-stu-id="25737-170">Because you frequently need to use images, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="25737-171">下圖顯示眾多方式的其中之一。</span><span class="sxs-lookup"><span data-stu-id="25737-171">The following illustration shows just one of those ways.</span></span>  
  
 <span data-ttu-id="25737-172">![設定樣式範例螢幕擷取畫面](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="25737-172">![Styling sample screen shot](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>  
  
 <span data-ttu-id="25737-173">如需詳細資訊，請參閱 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="25737-173">For more information, see [Imaging Overview](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).</span></span>  
  
### <a name="video-and-audio"></a><span data-ttu-id="25737-174">視訊和音訊</span><span class="sxs-lookup"><span data-stu-id="25737-174">Video and Audio</span></span>  
 <span data-ttu-id="25737-175">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 圖形功能的核心功能就是提供原生支援，以用於處理多媒體，包括視訊和音訊。</span><span class="sxs-lookup"><span data-stu-id="25737-175">A core feature of the graphics capabilities of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="25737-176">下列範例示範如何將媒體播放程式插入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="25737-176">The following example shows how to insert a media player into an application.</span></span>  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <span data-ttu-id="25737-177"><xref:System.Windows.Controls.MediaElement>都能播放視訊和音訊，且夠擴充，以允許自訂讓您輕鬆建立[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="25737-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].</span></span>  
  
 <span data-ttu-id="25737-178">如需詳細資訊，請參閱[多媒體概觀](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="25737-178">For more information, see the [Multimedia Overview](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25737-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25737-179">See Also</span></span>  
 <xref:System.Windows.Media>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Media3D>  
 [<span data-ttu-id="25737-180">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="25737-180">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [<span data-ttu-id="25737-181">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="25737-181">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="25737-182">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="25737-182">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="25737-183">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="25737-183">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="25737-184">動畫和計時</span><span class="sxs-lookup"><span data-stu-id="25737-184">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="25737-185">3d 圖形</span><span class="sxs-lookup"><span data-stu-id="25737-185">3-D Graphics</span></span>](http://msdn.microsoft.com/en-us/565c1f3c-235b-47de-b05b-3b53ed63f1b8)  
 [<span data-ttu-id="25737-186">多媒體</span><span class="sxs-lookup"><span data-stu-id="25737-186">Multimedia</span></span>](http://msdn.microsoft.com/en-us/44a8dcd0-80cb-4db0-a222-87cde68c2fac)
