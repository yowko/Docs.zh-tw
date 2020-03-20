---
title: 畫筆概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 7a9474b392052900952f5b677ad94b16025de8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186569"
---
# <a name="wpf-brushes-overview"></a><span data-ttu-id="f63d2-102">WPF 筆刷概觀</span><span class="sxs-lookup"><span data-stu-id="f63d2-102">WPF Brushes Overview</span></span>
<span data-ttu-id="f63d2-103">螢幕上可見的一切可見，因為它是由畫筆繪製的。</span><span class="sxs-lookup"><span data-stu-id="f63d2-103">Everything visible on your screen is visible because it was painted by a brush.</span></span> <span data-ttu-id="f63d2-104">例如，畫筆用於描述按鈕的背景、文本的前景和形狀的填充。</span><span class="sxs-lookup"><span data-stu-id="f63d2-104">For example, a brush is used to describe the background of a button, the foreground of text, and the fill of a shape.</span></span> <span data-ttu-id="f63d2-105">本主題介紹使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]畫筆繪畫的概念，並提供示例。</span><span class="sxs-lookup"><span data-stu-id="f63d2-105">This topic introduces the concepts of painting with [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] brushes and provides examples.</span></span> <span data-ttu-id="f63d2-106">筆刷可讓您以任何項目 (從簡單的純色到複雜的圖樣和影像集) 繪製 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 物件。</span><span class="sxs-lookup"><span data-stu-id="f63d2-106">Brushes enable you to paint [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] objects with anything from simple, solid colors to complex sets of patterns and images.</span></span>  
  
<a name="paintingwithbrush"></a>
## <a name="painting-with-a-brush"></a><span data-ttu-id="f63d2-107">用畫筆繪畫</span><span class="sxs-lookup"><span data-stu-id="f63d2-107">Painting with a Brush</span></span>  
 <span data-ttu-id="f63d2-108">具有<xref:System.Windows.Media.Brush>輸出的區域的"繪製"。</span><span class="sxs-lookup"><span data-stu-id="f63d2-108">A <xref:System.Windows.Media.Brush> "paints" an area with its output.</span></span> <span data-ttu-id="f63d2-109">不同的筆刷有不同類型的輸出。</span><span class="sxs-lookup"><span data-stu-id="f63d2-109">Different brushes have different types of output.</span></span> <span data-ttu-id="f63d2-110">有些畫筆用純色繪製區域，其他畫筆使用漸變、圖案、圖像或繪圖繪製區域。</span><span class="sxs-lookup"><span data-stu-id="f63d2-110">Some brushes paint an area with a solid color, others with a gradient, pattern, image, or drawing.</span></span> <span data-ttu-id="f63d2-111">下圖顯示了每種不同<xref:System.Windows.Media.Brush>類型的示例。</span><span class="sxs-lookup"><span data-stu-id="f63d2-111">The following illustration shows examples of each of the different <xref:System.Windows.Media.Brush> types.</span></span>  
  
 <span data-ttu-id="f63d2-112">![筆刷類型](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")</span><span class="sxs-lookup"><span data-stu-id="f63d2-112">![Brush types](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")</span></span>  
<span data-ttu-id="f63d2-113">畫筆示例</span><span class="sxs-lookup"><span data-stu-id="f63d2-113">Brush examples</span></span>  
  
 <span data-ttu-id="f63d2-114">大多數可視物件都允許您指定繪製它們的方式。</span><span class="sxs-lookup"><span data-stu-id="f63d2-114">Most visual objects enable you to specify how they are painted.</span></span> <span data-ttu-id="f63d2-115">下表列出了可以使用 的<xref:System.Windows.Media.Brush>一些常見物件和屬性。</span><span class="sxs-lookup"><span data-stu-id="f63d2-115">The following table lists some common objects and properties with which you can use a <xref:System.Windows.Media.Brush>.</span></span>  
  
|<span data-ttu-id="f63d2-116">類別</span><span class="sxs-lookup"><span data-stu-id="f63d2-116">Class</span></span>|<span data-ttu-id="f63d2-117">筆刷屬性</span><span class="sxs-lookup"><span data-stu-id="f63d2-117">Brush properties</span></span>|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<span data-ttu-id="f63d2-118"><xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A></span><span class="sxs-lookup"><span data-stu-id="f63d2-118"><xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A></span></span>|  
|<xref:System.Windows.Controls.Control>|<span data-ttu-id="f63d2-119"><xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A></span><span class="sxs-lookup"><span data-stu-id="f63d2-119"><xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A></span></span>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<span data-ttu-id="f63d2-120"><xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A></span><span class="sxs-lookup"><span data-stu-id="f63d2-120"><xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A></span></span>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 <span data-ttu-id="f63d2-121">以下各節介紹不同類型的<xref:System.Windows.Media.Brush>類型，並提供每種類型的示例。</span><span class="sxs-lookup"><span data-stu-id="f63d2-121">The following sections describe the different <xref:System.Windows.Media.Brush> types and provide an example of each.</span></span>  
  
<a name="paintwithsolidcolorbrush"></a>
## <a name="paint-with-a-solid-color"></a><span data-ttu-id="f63d2-122">純色塗料</span><span class="sxs-lookup"><span data-stu-id="f63d2-122">Paint with a Solid Color</span></span>  
 <span data-ttu-id="f63d2-123">A<xref:System.Windows.Media.SolidColorBrush>用固體<xref:System.Windows.Media.Color>繪製區域。</span><span class="sxs-lookup"><span data-stu-id="f63d2-123">A <xref:System.Windows.Media.SolidColorBrush> paints an area with a solid <xref:System.Windows.Media.Color>.</span></span> <span data-ttu-id="f63d2-124">指定<xref:System.Windows.Media.SolidColorBrush.Color%2A><xref:System.Windows.Media.SolidColorBrush>： 的方法有多種，例如，您可以指定其 Alpha、紅色、藍色和綠色通道或使用<xref:System.Windows.Media.Colors>類提供的預定義顏色之一。</span><span class="sxs-lookup"><span data-stu-id="f63d2-124">There are a variety of ways to specify the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush>: for example, you can specify its alpha, red, blue, and green channels or use one of the predefined color provided by the <xref:System.Windows.Media.Colors> class.</span></span>  
  
 <span data-ttu-id="f63d2-125">下面的示例使用 來<xref:System.Windows.Media.SolidColorBrush>繪製 的<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="f63d2-125">The following example uses a <xref:System.Windows.Media.SolidColorBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="f63d2-126">下圖顯示了繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="f63d2-126">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="f63d2-127">![使用 SolidColorBrush 繪製的矩形](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="f63d2-127">![A rectangle painted using a SolidColorBrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")</span></span>  
<span data-ttu-id="f63d2-128">使用單色筆刷繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="f63d2-128">A Rectangle painted using a SolidColorBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 <span data-ttu-id="f63d2-129">有關該類的詳細資訊，<xref:System.Windows.Media.SolidColorBrush>請參閱[使用純色和漸變概述進行繪畫](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f63d2-129">For more information about the <xref:System.Windows.Media.SolidColorBrush> class, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithlineargradientbrush"></a>
## <a name="paint-with-a-linear-gradient"></a><span data-ttu-id="f63d2-130">使用線性漸層繪製</span><span class="sxs-lookup"><span data-stu-id="f63d2-130">Paint with a Linear Gradient</span></span>  
 <span data-ttu-id="f63d2-131">繪製<xref:System.Windows.Media.LinearGradientBrush>具有線性漸層的區域。</span><span class="sxs-lookup"><span data-stu-id="f63d2-131">A <xref:System.Windows.Media.LinearGradientBrush> paints an area with a linear gradient.</span></span> <span data-ttu-id="f63d2-132">線性漸層會沿著一條線 (漸層軸) 混合兩個或更多色彩。</span><span class="sxs-lookup"><span data-stu-id="f63d2-132">A linear gradient blends two or more colors across a line, the gradient axis.</span></span> <span data-ttu-id="f63d2-133">您可以使用<xref:System.Windows.Media.GradientStop>物件指定漸變中的顏色及其位置。</span><span class="sxs-lookup"><span data-stu-id="f63d2-133">You use <xref:System.Windows.Media.GradientStop> objects to specify the colors in the gradient and their positions.</span></span>  
  
 <span data-ttu-id="f63d2-134">下面的示例使用 來<xref:System.Windows.Media.LinearGradientBrush>繪製 的<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="f63d2-134">The following example uses a <xref:System.Windows.Media.LinearGradientBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="f63d2-135">下圖顯示了繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="f63d2-135">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="f63d2-136">![使用 LinearGradientBrush 繪製的矩形](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")</span><span class="sxs-lookup"><span data-stu-id="f63d2-136">![A rectangle painted using a LinearGradientBrush](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")</span></span>  
<span data-ttu-id="f63d2-137">使用線性漸層畫筆繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="f63d2-137">A Rectangle painted using a LinearGradientBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 <span data-ttu-id="f63d2-138">有關該類的詳細資訊，<xref:System.Windows.Media.LinearGradientBrush>請參閱[使用純色和漸變概述進行繪畫](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f63d2-138">For more information about the <xref:System.Windows.Media.LinearGradientBrush> class, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithradialgradientbrush"></a>
## <a name="paint-with-a-radial-gradient"></a><span data-ttu-id="f63d2-139">使用徑向漸變繪製</span><span class="sxs-lookup"><span data-stu-id="f63d2-139">Paint with a Radial Gradient</span></span>  
 <span data-ttu-id="f63d2-140">繪製<xref:System.Windows.Media.RadialGradientBrush>具有徑向漸變的區域。</span><span class="sxs-lookup"><span data-stu-id="f63d2-140">A <xref:System.Windows.Media.RadialGradientBrush> paints an area with a radial gradient.</span></span> <span data-ttu-id="f63d2-141">徑向漸變在一個圓圈上混合兩種或多種顏色。</span><span class="sxs-lookup"><span data-stu-id="f63d2-141">A radial gradient blends two or more colors across a circle.</span></span> <span data-ttu-id="f63d2-142">與類一<xref:System.Windows.Media.LinearGradientBrush>樣，使用<xref:System.Windows.Media.GradientStop>物件指定漸變中的顏色及其位置。</span><span class="sxs-lookup"><span data-stu-id="f63d2-142">As with the <xref:System.Windows.Media.LinearGradientBrush> class, you use <xref:System.Windows.Media.GradientStop> objects to specify the colors in the gradient and their positions.</span></span>  
  
 <span data-ttu-id="f63d2-143">下面的示例使用 來<xref:System.Windows.Media.RadialGradientBrush>繪製 的<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="f63d2-143">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="f63d2-144">下圖顯示了繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="f63d2-144">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="f63d2-145">![使用 RadialGradientBrush 繪製的矩形](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")</span><span class="sxs-lookup"><span data-stu-id="f63d2-145">![A rectangle painted using a RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")</span></span>  
<span data-ttu-id="f63d2-146">使用徑向漸層筆刷繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="f63d2-146">A Rectangle painted using a RadialGradientBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 <span data-ttu-id="f63d2-147">有關該類的詳細資訊，<xref:System.Windows.Media.RadialGradientBrush>請參閱[使用純色和漸變概述進行繪畫](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f63d2-147">For more information about the <xref:System.Windows.Media.RadialGradientBrush> class, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithimage"></a>
## <a name="paint-with-an-image"></a><span data-ttu-id="f63d2-148">使用圖像繪製</span><span class="sxs-lookup"><span data-stu-id="f63d2-148">Paint with an Image</span></span>  
 <span data-ttu-id="f63d2-149">用<xref:System.Windows.Media.ImageBrush>油漆區域<xref:System.Windows.Media.ImageSource>。</span><span class="sxs-lookup"><span data-stu-id="f63d2-149">An <xref:System.Windows.Media.ImageBrush> paints an area with a <xref:System.Windows.Media.ImageSource>.</span></span>  
  
 <span data-ttu-id="f63d2-150">下面的示例使用<xref:System.Windows.Media.ImageBrush>來繪製 的<xref:System.Windows.Shapes.Shape.Fill%2A>。 <xref:System.Windows.Shapes.Rectangle></span><span class="sxs-lookup"><span data-stu-id="f63d2-150">The following example uses an <xref:System.Windows.Media.ImageBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="f63d2-151">下圖顯示了繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="f63d2-151">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="f63d2-152">![ImageBrush 所繪製的矩形](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")</span><span class="sxs-lookup"><span data-stu-id="f63d2-152">![A Rectangle painted by an ImageBrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")</span></span>  
<span data-ttu-id="f63d2-153">使用圖像繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="f63d2-153">A Rectangle painted using a Image</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 <span data-ttu-id="f63d2-154">有關該類的詳細資訊，<xref:System.Windows.Media.ImageBrush>請參閱[使用圖像、繪圖和視覺物件進行繪畫](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="f63d2-154">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithdrawing"></a>
## <a name="paint-with-a-drawing"></a><span data-ttu-id="f63d2-155">使用繪圖繪製</span><span class="sxs-lookup"><span data-stu-id="f63d2-155">Paint with a Drawing</span></span>  
 <span data-ttu-id="f63d2-156">a<xref:System.Windows.Media.DrawingBrush>用 繪製區域<xref:System.Windows.Media.Drawing>。</span><span class="sxs-lookup"><span data-stu-id="f63d2-156">A <xref:System.Windows.Media.DrawingBrush> paints an area with a <xref:System.Windows.Media.Drawing>.</span></span> <span data-ttu-id="f63d2-157">可以<xref:System.Windows.Media.Drawing>包含形狀、圖像、文本和媒體。</span><span class="sxs-lookup"><span data-stu-id="f63d2-157">A <xref:System.Windows.Media.Drawing> can contain shapes, images, text, and media.</span></span>  
  
 <span data-ttu-id="f63d2-158">下面的示例使用 來<xref:System.Windows.Media.DrawingBrush>繪製 的<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="f63d2-158">The following example uses a <xref:System.Windows.Media.DrawingBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="f63d2-159">下圖顯示了繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="f63d2-159">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="f63d2-160">![使用 DrawingBrush 繪製的矩形](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")</span><span class="sxs-lookup"><span data-stu-id="f63d2-160">![A rectangle painted using a DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")</span></span>  
<span data-ttu-id="f63d2-161">使用繪圖畫筆繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="f63d2-161">A Rectangle painted using a DrawingBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 <span data-ttu-id="f63d2-162">有關該類的詳細資訊，<xref:System.Windows.Media.DrawingBrush>請參閱[使用圖像、繪圖和視覺物件進行繪畫](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="f63d2-162">For more information about the <xref:System.Windows.Media.DrawingBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithvisual"></a>
## <a name="paint-with-a-visual"></a><span data-ttu-id="f63d2-163">使用視覺物件繪製</span><span class="sxs-lookup"><span data-stu-id="f63d2-163">Paint with a Visual</span></span>  
 <span data-ttu-id="f63d2-164">用<xref:System.Windows.Media.VisualBrush><xref:System.Windows.Media.Visual>物件繪製區域。</span><span class="sxs-lookup"><span data-stu-id="f63d2-164">A <xref:System.Windows.Media.VisualBrush> paints an area with a <xref:System.Windows.Media.Visual> object.</span></span> <span data-ttu-id="f63d2-165">Visual 物件的示例包括<xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Page>、<xref:System.Windows.Controls.MediaElement>和 。</span><span class="sxs-lookup"><span data-stu-id="f63d2-165">Examples of Visual objects include <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>, and <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="f63d2-166">還<xref:System.Windows.Media.VisualBrush>使您能夠將應用程式某一部分的內容投影到另一個區域;它對於創建反射效果和放大螢幕部分非常有用。</span><span class="sxs-lookup"><span data-stu-id="f63d2-166">A <xref:System.Windows.Media.VisualBrush> also enables you to project content from one portion of your application into another area; it's very useful for creating reflection effects and magnifying portions of the screen.</span></span>  
  
 <span data-ttu-id="f63d2-167">下面的示例使用 來<xref:System.Windows.Media.VisualBrush>繪製 的<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="f63d2-167">The following example uses a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="f63d2-168">下圖顯示了繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="f63d2-168">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="f63d2-169">![使用 VisualBrush 繪製的矩形](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")</span><span class="sxs-lookup"><span data-stu-id="f63d2-169">![A rectangle painted using a VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")</span></span>  
<span data-ttu-id="f63d2-170">使用視覺筆刷繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="f63d2-170">A Rectangle painted using a VisualBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 <span data-ttu-id="f63d2-171">有關該類的詳細資訊，<xref:System.Windows.Media.VisualBrush>請參閱[使用圖像、繪圖和視覺物件進行繪畫](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="f63d2-171">For more information about the <xref:System.Windows.Media.VisualBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>
## <a name="paint-using-predefined-and-system-brushes"></a><span data-ttu-id="f63d2-172">使用預定義和系統畫筆繪製</span><span class="sxs-lookup"><span data-stu-id="f63d2-172">Paint using Predefined and System Brushes</span></span>  
 <span data-ttu-id="f63d2-173">為方便起見，Windows 演示文稿基礎 （WPF） 提供了一組預定義和系統畫筆，可用於繪製物件。</span><span class="sxs-lookup"><span data-stu-id="f63d2-173">For convenience, Windows Presentation Foundation (WPF) provides a set of predefined and system brushes that you can use to paint objects.</span></span>  
  
- <span data-ttu-id="f63d2-174">有關可用預定義畫筆的清單，請參閱類<xref:System.Windows.Media.Brushes>。</span><span class="sxs-lookup"><span data-stu-id="f63d2-174">For a list of available predefined brushes, see the <xref:System.Windows.Media.Brushes> class.</span></span> <span data-ttu-id="f63d2-175">有關演示如何使用預定義的畫筆的示例，請參閱[使用純色繪製區域](how-to-paint-an-area-with-a-solid-color.md)。</span><span class="sxs-lookup"><span data-stu-id="f63d2-175">For an example showing how to use a predefined brush, see [Paint an Area with a Solid Color](how-to-paint-an-area-with-a-solid-color.md).</span></span>  
  
- <span data-ttu-id="f63d2-176">有關可用系統畫筆的清單，請參閱類<xref:System.Windows.SystemColors>。</span><span class="sxs-lookup"><span data-stu-id="f63d2-176">For a list of available system brushes, see the <xref:System.Windows.SystemColors> class.</span></span> <span data-ttu-id="f63d2-177">例如，請參閱[使用系統畫筆繪製區域](how-to-paint-an-area-with-a-system-brush.md)。</span><span class="sxs-lookup"><span data-stu-id="f63d2-177">For an example, see [Paint an Area with a System Brush](how-to-paint-an-area-with-a-system-brush.md).</span></span>  
  
<a name="commonbrushfeatures"></a>
## <a name="common-brush-features"></a><span data-ttu-id="f63d2-178">常見畫筆功能</span><span class="sxs-lookup"><span data-stu-id="f63d2-178">Common Brush Features</span></span>  
 <span data-ttu-id="f63d2-179"><xref:System.Windows.Media.Brush>物件提供可用於<xref:System.Windows.Media.Brush.Opacity%2A>使畫筆透明或部分透明的屬性。</span><span class="sxs-lookup"><span data-stu-id="f63d2-179"><xref:System.Windows.Media.Brush> objects provide an <xref:System.Windows.Media.Brush.Opacity%2A> property that can be used to make a brush transparent or partially transparent.</span></span> <span data-ttu-id="f63d2-180"><xref:System.Windows.Media.Brush.Opacity%2A>值 0 使畫筆完全透明，而<xref:System.Windows.Media.Brush.Opacity%2A>值 1 使畫筆完全不透明。</span><span class="sxs-lookup"><span data-stu-id="f63d2-180">An <xref:System.Windows.Media.Brush.Opacity%2A> value of 0 makes a brush completely transparent, while an <xref:System.Windows.Media.Brush.Opacity%2A> value of 1 makes a brush completely opaque.</span></span> <span data-ttu-id="f63d2-181">下面的示例使用 屬性<xref:System.Windows.Media.Brush.Opacity%2A>使<xref:System.Windows.Media.SolidColorBrush>25% 不透明。</span><span class="sxs-lookup"><span data-stu-id="f63d2-181">The following example uses the <xref:System.Windows.Media.Brush.Opacity%2A> property to make a <xref:System.Windows.Media.SolidColorBrush> 25 percent opaque.</span></span>  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 <span data-ttu-id="f63d2-182">如果畫筆包含部分透明的顏色，則通過乘法與畫筆的不透明度值組合顏色的不透明度值。</span><span class="sxs-lookup"><span data-stu-id="f63d2-182">If the brush contains colors that are partially transparent, the opacity value of the color is combined through multiplication with the opacity value of the brush.</span></span> <span data-ttu-id="f63d2-183">例如，如果畫筆的不向性值為 0.5，並且畫筆中使用的顏色也具有 0.5 的不連續值，則輸出顏色的不向性值為 0.25。</span><span class="sxs-lookup"><span data-stu-id="f63d2-183">For example, if a brush has an opacity value of 0.5 and a color used in the brush also has an opacity value of 0.5, the output color has an opacity value of 0.25.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f63d2-184">與使用畫筆<xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>屬性更改整個元素的不向性相比，更改畫筆的不向性值更有效。</span><span class="sxs-lookup"><span data-stu-id="f63d2-184">It's more efficient to change the opacity value of a brush than it is to change the opacity of an entire element using its <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="f63d2-185">您可以使用畫筆<xref:System.Windows.Media.Brush.Transform%2A>或<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性旋轉、縮放、傾斜和翻譯畫筆的內容。</span><span class="sxs-lookup"><span data-stu-id="f63d2-185">You can rotate, scale, skew, and translate a brush's content by using its <xref:System.Windows.Media.Brush.Transform%2A> or <xref:System.Windows.Media.Brush.RelativeTransform%2A> properties.</span></span> <span data-ttu-id="f63d2-186">有關詳細資訊，請參閱[筆刷轉換概述](brush-transformation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f63d2-186">For more information, see [Brush Transformation Overview](brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="f63d2-187">因為它們是<xref:System.Windows.Media.Animation.Animatable>物件，<xref:System.Windows.Media.Brush>因此可以對物件進行動畫處理。</span><span class="sxs-lookup"><span data-stu-id="f63d2-187">Because they are <xref:System.Windows.Media.Animation.Animatable> objects, <xref:System.Windows.Media.Brush> objects can be animated.</span></span> <span data-ttu-id="f63d2-188">有關詳細資訊，請參閱[動畫概述](animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f63d2-188">For more information, see [Animation Overview](animation-overview.md).</span></span>  
  
<a name="freezable_features"></a>
### <a name="freezable-features"></a><span data-ttu-id="f63d2-189">Freezable 功能</span><span class="sxs-lookup"><span data-stu-id="f63d2-189">Freezable Features</span></span>  
 <span data-ttu-id="f63d2-190">由於該<xref:System.Windows.Freezable>類從類繼承，因此<xref:System.Windows.Media.Brush>提供了幾個特殊功能：<xref:System.Windows.Media.Brush>物件可以聲明為[資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)、在多個物件之間共用和克隆。</span><span class="sxs-lookup"><span data-stu-id="f63d2-190">Because it inherits from the <xref:System.Windows.Freezable> class, the <xref:System.Windows.Media.Brush> class provides several special features: <xref:System.Windows.Media.Brush> objects can be declared as [resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md), shared among multiple objects, and cloned.</span></span> <span data-ttu-id="f63d2-191">此外，除所有類型<xref:System.Windows.Media.Brush>外<xref:System.Windows.Media.VisualBrush>，還可以唯讀，以提高性能並使執行緒安全。</span><span class="sxs-lookup"><span data-stu-id="f63d2-191">In addition, all the <xref:System.Windows.Media.Brush> types except <xref:System.Windows.Media.VisualBrush> can be made read-only to improve performance and made thread-safe.</span></span>  
  
 <span data-ttu-id="f63d2-192">有關<xref:System.Windows.Freezable>物件提供的不同要素的詳細資訊，請參閱[可凍結物件概述](../advanced/freezable-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f63d2-192">For more information about the different features provided by <xref:System.Windows.Freezable> objects, see [Freezable Objects Overview](../advanced/freezable-objects-overview.md).</span></span>  
  
 <span data-ttu-id="f63d2-193">有關無法凍結物件的原因<xref:System.Windows.Media.VisualBrush>的詳細資訊，請參閱<xref:System.Windows.Media.VisualBrush>類型頁。</span><span class="sxs-lookup"><span data-stu-id="f63d2-193">For more information on why <xref:System.Windows.Media.VisualBrush> objects cannot be frozen, see the <xref:System.Windows.Media.VisualBrush> type page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f63d2-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f63d2-194">See also</span></span>

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [<span data-ttu-id="f63d2-195">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="f63d2-195">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="f63d2-196">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="f63d2-196">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="f63d2-197">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="f63d2-197">Freezable Objects Overview</span></span>](../advanced/freezable-objects-overview.md)
- [<span data-ttu-id="f63d2-198">筆刷範例</span><span class="sxs-lookup"><span data-stu-id="f63d2-198">Brushes Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
- [<span data-ttu-id="f63d2-199">ImageBrush 範例</span><span class="sxs-lookup"><span data-stu-id="f63d2-199">ImageBrush Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [<span data-ttu-id="f63d2-200">VisualBrush 範例</span><span class="sxs-lookup"><span data-stu-id="f63d2-200">VisualBrush Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
- [<span data-ttu-id="f63d2-201">如何使用主題</span><span class="sxs-lookup"><span data-stu-id="f63d2-201">How-to Topics</span></span>](brushes-how-to-topics.md)
- [<span data-ttu-id="f63d2-202">其他效能建議</span><span class="sxs-lookup"><span data-stu-id="f63d2-202">Other Performance Recommendations</span></span>](../advanced/optimizing-performance-other-recommendations.md)
