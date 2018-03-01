---
title: "WPF 筆刷概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ec7e566e6f56c215bbaeafdfb5c5e97cc0add0bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-brushes-overview"></a><span data-ttu-id="999ab-102">WPF 筆刷概觀</span><span class="sxs-lookup"><span data-stu-id="999ab-102">WPF Brushes Overview</span></span>
<span data-ttu-id="999ab-103">螢幕上看見的項目是可見的因為它已繪製的筆刷。</span><span class="sxs-lookup"><span data-stu-id="999ab-103">Everything visible on your screen is visible because it was painted by a brush.</span></span> <span data-ttu-id="999ab-104">例如，筆刷用來描述的按鈕、 文字、 前景和填滿圖形的背景。</span><span class="sxs-lookup"><span data-stu-id="999ab-104">For example, a brush is used to describe the background of a button, the foreground of text, and the fill of a shape.</span></span> <span data-ttu-id="999ab-105">本主題介紹的概念與繪製[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]筆刷，並提供範例。</span><span class="sxs-lookup"><span data-stu-id="999ab-105">This topic introduces the concepts of painting with [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] brushes and provides examples.</span></span> <span data-ttu-id="999ab-106">筆刷可讓您以任何項目 (從簡單的純色到複雜的圖樣和影像集) 繪製 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 物件。</span><span class="sxs-lookup"><span data-stu-id="999ab-106">Brushes enable you to paint [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] objects with anything from simple, solid colors to complex sets of patterns and images.</span></span>  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a><span data-ttu-id="999ab-107">使用筆刷繪製</span><span class="sxs-lookup"><span data-stu-id="999ab-107">Painting with a Brush</span></span>  
 <span data-ttu-id="999ab-108">A <xref:System.Windows.Media.Brush> "」 使用繪製區域其輸出。</span><span class="sxs-lookup"><span data-stu-id="999ab-108">A <xref:System.Windows.Media.Brush> "paints" an area with its output.</span></span> <span data-ttu-id="999ab-109">不同筆刷有不同類型的輸出。</span><span class="sxs-lookup"><span data-stu-id="999ab-109">Different brushes have different types of output.</span></span> <span data-ttu-id="999ab-110">某些筆刷繪製利用純色，其他人使用漸層、 模式、 影像或繪圖區域。</span><span class="sxs-lookup"><span data-stu-id="999ab-110">Some brushes paint an area with a solid color, others with a gradient, pattern, image, or drawing.</span></span> <span data-ttu-id="999ab-111">下圖顯示每個不同的範例<xref:System.Windows.Media.Brush>型別。</span><span class="sxs-lookup"><span data-stu-id="999ab-111">The following illustration shows examples of each of the different <xref:System.Windows.Media.Brush> types.</span></span>  
  
 <span data-ttu-id="999ab-112">![筆刷類型](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")</span><span class="sxs-lookup"><span data-stu-id="999ab-112">![Brush types](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")</span></span>  
<span data-ttu-id="999ab-113">筆刷範例</span><span class="sxs-lookup"><span data-stu-id="999ab-113">Brush examples</span></span>  
  
 <span data-ttu-id="999ab-114">大部分的 visual 物件可讓您指定繪製的方式。</span><span class="sxs-lookup"><span data-stu-id="999ab-114">Most visual objects enable you to specify how they are painted.</span></span> <span data-ttu-id="999ab-115">下表列出一些常見的物件和屬性，您可以使用<xref:System.Windows.Media.Brush>。</span><span class="sxs-lookup"><span data-stu-id="999ab-115">The following table lists some common objects and properties with which you can use a <xref:System.Windows.Media.Brush>.</span></span>  
  
|<span data-ttu-id="999ab-116">類別</span><span class="sxs-lookup"><span data-stu-id="999ab-116">Class</span></span>|<span data-ttu-id="999ab-117">筆刷屬性</span><span class="sxs-lookup"><span data-stu-id="999ab-117">Brush properties</span></span>|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<span data-ttu-id="999ab-118"><xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A></span><span class="sxs-lookup"><span data-stu-id="999ab-118"><xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A></span></span>|  
|<xref:System.Windows.Controls.Control>|<span data-ttu-id="999ab-119"><xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A></span><span class="sxs-lookup"><span data-stu-id="999ab-119"><xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A></span></span>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<span data-ttu-id="999ab-120"><xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A></span><span class="sxs-lookup"><span data-stu-id="999ab-120"><xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A></span></span>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 <span data-ttu-id="999ab-121">下列各節說明不同<xref:System.Windows.Media.Brush>類型，並提供每個範例。</span><span class="sxs-lookup"><span data-stu-id="999ab-121">The following sections describe the different <xref:System.Windows.Media.Brush> types and provide an example of each.</span></span>  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a><span data-ttu-id="999ab-122">使用純色繪製</span><span class="sxs-lookup"><span data-stu-id="999ab-122">Paint with a Solid Color</span></span>  
 <span data-ttu-id="999ab-123">A<xref:System.Windows.Media.SolidColorBrush>使用純色繪製區域<xref:System.Windows.Media.Color>。</span><span class="sxs-lookup"><span data-stu-id="999ab-123">A <xref:System.Windows.Media.SolidColorBrush> paints an area with a solid <xref:System.Windows.Media.Color>.</span></span> <span data-ttu-id="999ab-124">有多種方式來指定<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>： 例如，您可以在 指定其 alpha、 紅、 藍色以及綠色的通道，或使用預先定義的色彩所提供的其中一個<xref:System.Windows.Media.Colors>類別。</span><span class="sxs-lookup"><span data-stu-id="999ab-124">There are a variety of ways to specify the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush>: for example, you can specify its alpha, red, blue, and green channels or use one of the predefined color provided by the <xref:System.Windows.Media.Colors> class.</span></span>  
  
 <span data-ttu-id="999ab-125">下列範例會使用<xref:System.Windows.Media.SolidColorBrush>來繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="999ab-125">The following example uses a <xref:System.Windows.Media.SolidColorBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="999ab-126">下圖顯示繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="999ab-126">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="999ab-127">![使用 SolidColorBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="999ab-127">![A rectangle painted using a SolidColorBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")</span></span>  
<span data-ttu-id="999ab-128">使用 SolidColorBrush 繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="999ab-128">A Rectangle painted using a SolidColorBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 <span data-ttu-id="999ab-129">如需有關<xref:System.Windows.Media.SolidColorBrush>類別，請參閱[使用單色和漸層概觀繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="999ab-129">For more information about the <xref:System.Windows.Media.SolidColorBrush> class, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a><span data-ttu-id="999ab-130">使用線性漸層繪製</span><span class="sxs-lookup"><span data-stu-id="999ab-130">Paint with a Linear Gradient</span></span>  
 <span data-ttu-id="999ab-131">A<xref:System.Windows.Media.LinearGradientBrush>使用線形漸層繪製區域。</span><span class="sxs-lookup"><span data-stu-id="999ab-131">A <xref:System.Windows.Media.LinearGradientBrush> paints an area with a linear gradient.</span></span> <span data-ttu-id="999ab-132">線性漸層混合不同線，漸層軸的兩個以上的色彩。</span><span class="sxs-lookup"><span data-stu-id="999ab-132">A linear gradient blends two or more colors across a line, the gradient axis.</span></span> <span data-ttu-id="999ab-133">您使用<xref:System.Windows.Media.GradientStop>指定的色彩漸層和它們的位置中的物件。</span><span class="sxs-lookup"><span data-stu-id="999ab-133">You use <xref:System.Windows.Media.GradientStop> objects to specify the colors in the gradient and their positions.</span></span>  
  
 <span data-ttu-id="999ab-134">下列範例會使用<xref:System.Windows.Media.LinearGradientBrush>來繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="999ab-134">The following example uses a <xref:System.Windows.Media.LinearGradientBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="999ab-135">下圖顯示繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="999ab-135">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="999ab-136">![使用 LinearGradientBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")</span><span class="sxs-lookup"><span data-stu-id="999ab-136">![A rectangle painted using a LinearGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")</span></span>  
<span data-ttu-id="999ab-137">使用 LinearGradientBrush 繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="999ab-137">A Rectangle painted using a LinearGradientBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 <span data-ttu-id="999ab-138">如需有關<xref:System.Windows.Media.LinearGradientBrush>類別，請參閱[使用單色和漸層概觀繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="999ab-138">For more information about the <xref:System.Windows.Media.LinearGradientBrush> class, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a><span data-ttu-id="999ab-139">使用放射狀漸層繪製</span><span class="sxs-lookup"><span data-stu-id="999ab-139">Paint with a Radial Gradient</span></span>  
 <span data-ttu-id="999ab-140">A<xref:System.Windows.Media.RadialGradientBrush>使用放射狀漸層繪製區域。</span><span class="sxs-lookup"><span data-stu-id="999ab-140">A <xref:System.Windows.Media.RadialGradientBrush> paints an area with a radial gradient.</span></span> <span data-ttu-id="999ab-141">放射狀漸層在圓圈混合兩個以上的色彩。</span><span class="sxs-lookup"><span data-stu-id="999ab-141">A radial gradient blends two or more colors across a circle.</span></span> <span data-ttu-id="999ab-142">如同<xref:System.Windows.Media.LinearGradientBrush>類別，您使用<xref:System.Windows.Media.GradientStop>指定的色彩漸層和它們的位置中的物件。</span><span class="sxs-lookup"><span data-stu-id="999ab-142">As with the <xref:System.Windows.Media.LinearGradientBrush> class, you use <xref:System.Windows.Media.GradientStop> objects to specify the colors in the gradient and their positions.</span></span>  
  
 <span data-ttu-id="999ab-143">下列範例會使用<xref:System.Windows.Media.RadialGradientBrush>來繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="999ab-143">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="999ab-144">下圖顯示繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="999ab-144">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="999ab-145">![使用 RadialGradientBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")</span><span class="sxs-lookup"><span data-stu-id="999ab-145">![A rectangle painted using a RadialGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")</span></span>  
<span data-ttu-id="999ab-146">使用 RadialGradientBrush 繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="999ab-146">A Rectangle painted using a RadialGradientBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 <span data-ttu-id="999ab-147">如需有關<xref:System.Windows.Media.RadialGradientBrush>類別，請參閱[使用單色和漸層概觀繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="999ab-147">For more information about the <xref:System.Windows.Media.RadialGradientBrush> class, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a><span data-ttu-id="999ab-148">使用影像繪製</span><span class="sxs-lookup"><span data-stu-id="999ab-148">Paint with an Image</span></span>  
 <span data-ttu-id="999ab-149"><xref:System.Windows.Media.ImageBrush>使用繪製區域<xref:System.Windows.Media.ImageSource>。</span><span class="sxs-lookup"><span data-stu-id="999ab-149">An <xref:System.Windows.Media.ImageBrush> paints an area with a <xref:System.Windows.Media.ImageSource>.</span></span>  
  
 <span data-ttu-id="999ab-150">下列範例會使用<xref:System.Windows.Media.ImageBrush>來繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="999ab-150">The following example uses an <xref:System.Windows.Media.ImageBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="999ab-151">下圖顯示繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="999ab-151">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="999ab-152">![ImageBrush 所繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")</span><span class="sxs-lookup"><span data-stu-id="999ab-152">![A Rectangle painted by an ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")</span></span>  
<span data-ttu-id="999ab-153">使用影像繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="999ab-153">A Rectangle painted using a Image</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 <span data-ttu-id="999ab-154">如需有關<xref:System.Windows.Media.ImageBrush>類別，請參閱[使用映像、 繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="999ab-154">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a><span data-ttu-id="999ab-155">使用繪圖繪製</span><span class="sxs-lookup"><span data-stu-id="999ab-155">Paint with a Drawing</span></span>  
 <span data-ttu-id="999ab-156">A<xref:System.Windows.Media.DrawingBrush>使用繪製區域<xref:System.Windows.Media.Drawing>。</span><span class="sxs-lookup"><span data-stu-id="999ab-156">A <xref:System.Windows.Media.DrawingBrush> paints an area with a <xref:System.Windows.Media.Drawing>.</span></span> <span data-ttu-id="999ab-157">A<xref:System.Windows.Media.Drawing>可包含圖形、 影像、 文字與媒體。</span><span class="sxs-lookup"><span data-stu-id="999ab-157">A <xref:System.Windows.Media.Drawing> can contain shapes, images, text, and media.</span></span>  
  
 <span data-ttu-id="999ab-158">下列範例會使用<xref:System.Windows.Media.DrawingBrush>來繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="999ab-158">The following example uses a <xref:System.Windows.Media.DrawingBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="999ab-159">下圖顯示繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="999ab-159">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="999ab-160">![使用 DrawingBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")</span><span class="sxs-lookup"><span data-stu-id="999ab-160">![A rectangle painted using a DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")</span></span>  
<span data-ttu-id="999ab-161">使用 DrawingBrush 繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="999ab-161">A Rectangle painted using a DrawingBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 <span data-ttu-id="999ab-162">如需有關<xref:System.Windows.Media.DrawingBrush>類別，請參閱[使用映像、 繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="999ab-162">For more information about the <xref:System.Windows.Media.DrawingBrush> class, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a><span data-ttu-id="999ab-163">使用視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="999ab-163">Paint with a Visual</span></span>  
 <span data-ttu-id="999ab-164">A<xref:System.Windows.Media.VisualBrush>使用繪製區域<xref:System.Windows.Media.Visual>物件。</span><span class="sxs-lookup"><span data-stu-id="999ab-164">A <xref:System.Windows.Media.VisualBrush> paints an area with a <xref:System.Windows.Media.Visual> object.</span></span> <span data-ttu-id="999ab-165">視覺物件的範例包括<xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.Page>，和<xref:System.Windows.Controls.MediaElement>。</span><span class="sxs-lookup"><span data-stu-id="999ab-165">Examples of Visual objects include <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>, and <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="999ab-166">A<xref:System.Windows.Media.VisualBrush>也可讓您從另一個區域，將應用程式的一個部分的專案內容建立反射效果及放大的螢幕部分很有用。</span><span class="sxs-lookup"><span data-stu-id="999ab-166">A <xref:System.Windows.Media.VisualBrush> also enables you to project content from one portion of your application into another area; it's very useful for creating reflection effects and magnifying portions of the screen.</span></span>  
  
 <span data-ttu-id="999ab-167">下列範例會使用<xref:System.Windows.Media.VisualBrush>來繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="999ab-167">The following example uses a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="999ab-168">下圖顯示繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="999ab-168">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="999ab-169">![使用 VisualBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")</span><span class="sxs-lookup"><span data-stu-id="999ab-169">![A rectangle painted using a VisualBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")</span></span>  
<span data-ttu-id="999ab-170">使用 VisualBrush 繪製的矩形</span><span class="sxs-lookup"><span data-stu-id="999ab-170">A Rectangle painted using a VisualBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 <span data-ttu-id="999ab-171">如需有關<xref:System.Windows.Media.VisualBrush>類別，請參閱[使用映像、 繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="999ab-171">For more information about the <xref:System.Windows.Media.VisualBrush> class, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a><span data-ttu-id="999ab-172">使用預先定義和系統筆刷繪製</span><span class="sxs-lookup"><span data-stu-id="999ab-172">Paint using Predefined and System Brushes</span></span>  
 <span data-ttu-id="999ab-173">為了方便起見，[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]提供一組預先定義和系統筆刷可用來繪製物件。</span><span class="sxs-lookup"><span data-stu-id="999ab-173">For convenience, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] provides a set of predefined and system brushes that you can use to paint objects.</span></span>  
  
-   <span data-ttu-id="999ab-174">如需使用預先定義的筆刷的清單，請參閱<xref:System.Windows.Media.Brushes>類別。</span><span class="sxs-lookup"><span data-stu-id="999ab-174">For a list of available predefined brushes, see the <xref:System.Windows.Media.Brushes> class.</span></span> <span data-ttu-id="999ab-175">如需示範如何使用預先定義的筆刷的範例，請參閱[使用純色繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-solid-color.md)。</span><span class="sxs-lookup"><span data-stu-id="999ab-175">For an example showing how to use a predefined brush, see [Paint an Area with a Solid Color](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-solid-color.md).</span></span>  
  
-   <span data-ttu-id="999ab-176">如需可用的系統筆刷的清單，請參閱<xref:System.Windows.SystemColors>類別。</span><span class="sxs-lookup"><span data-stu-id="999ab-176">For a list of available system brushes, see the <xref:System.Windows.SystemColors> class.</span></span> <span data-ttu-id="999ab-177">如需範例，請參閱[使用系統筆刷繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)。</span><span class="sxs-lookup"><span data-stu-id="999ab-177">For an example, see [Paint an Area with a System Brush](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md).</span></span>  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a><span data-ttu-id="999ab-178">常見的筆刷功能</span><span class="sxs-lookup"><span data-stu-id="999ab-178">Common Brush Features</span></span>  
 <span data-ttu-id="999ab-179"><xref:System.Windows.Media.Brush>物件提供<xref:System.Windows.Media.Brush.Opacity%2A>可用來做為筆刷透明或透明部分的屬性。</span><span class="sxs-lookup"><span data-stu-id="999ab-179"><xref:System.Windows.Media.Brush> objects provide an <xref:System.Windows.Media.Brush.Opacity%2A> property that can be used to make a brush transparent or partially transparent.</span></span> <span data-ttu-id="999ab-180"><xref:System.Windows.Media.Brush.Opacity%2A>為 0 的值會使筆刷完全透明，而<xref:System.Windows.Media.Brush.Opacity%2A>完全不透明的值為 1 可筆刷。</span><span class="sxs-lookup"><span data-stu-id="999ab-180">An <xref:System.Windows.Media.Brush.Opacity%2A> value of 0 makes a brush completely transparent, while an <xref:System.Windows.Media.Brush.Opacity%2A> value of 1 makes a brush completely opaque.</span></span> <span data-ttu-id="999ab-181">下列範例會使用<xref:System.Windows.Media.Brush.Opacity%2A>屬性使<xref:System.Windows.Media.SolidColorBrush>25%不透明。</span><span class="sxs-lookup"><span data-stu-id="999ab-181">The following example uses the <xref:System.Windows.Media.Brush.Opacity%2A> property to make a <xref:System.Windows.Media.SolidColorBrush> 25 percent opaque.</span></span>  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 <span data-ttu-id="999ab-182">如果筆刷包含部分透明的色彩，色彩的不透明度值會結合到筆刷的不透明度值相乘。</span><span class="sxs-lookup"><span data-stu-id="999ab-182">If the brush contains colors that are partially transparent, the opacity value of the color is combined through multiplication with the opacity value of the brush.</span></span> <span data-ttu-id="999ab-183">例如，如果筆刷的不透明度值為 0.5，而且也有使用筆刷色彩的不透明度值為 0.5，輸出色彩的不透明值 0.25。</span><span class="sxs-lookup"><span data-stu-id="999ab-183">For example, if a brush has an opacity value of 0.5 and a color used in the brush also has an opacity value of 0.5, the output color has an opacity value of 0.25.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="999ab-184">若要變更筆刷的不透明值，變更整個項目使用的不透明度比更有效率的<xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="999ab-184">It's more efficient to change the opacity value of a brush than it is to change the opacity of an entire element using its <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="999ab-185">您可以旋轉和調整其規模、 扭曲，翻譯筆刷的內容使用其<xref:System.Windows.Media.Brush.Transform%2A>或<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="999ab-185">You can rotate, scale, skew, and translate a brush's content by using its <xref:System.Windows.Media.Brush.Transform%2A> or <xref:System.Windows.Media.Brush.RelativeTransform%2A> properties.</span></span> <span data-ttu-id="999ab-186">如需詳細資訊，請參閱[筆刷轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="999ab-186">For more information, see [Brush Transformation Overview](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="999ab-187">因為它們是<xref:System.Windows.Media.Animation.Animatable>物件<xref:System.Windows.Media.Brush>可以動畫顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="999ab-187">Because they are <xref:System.Windows.Media.Animation.Animatable> objects, <xref:System.Windows.Media.Brush> objects can be animated.</span></span> <span data-ttu-id="999ab-188">如需詳細資訊，請參閱 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="999ab-188">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a><span data-ttu-id="999ab-189">Freezable 功能</span><span class="sxs-lookup"><span data-stu-id="999ab-189">Freezable Features</span></span>  
 <span data-ttu-id="999ab-190">因為它繼承自<xref:System.Windows.Freezable>類別<xref:System.Windows.Media.Brush>類別提供數個特殊功能：<xref:System.Windows.Media.Brush>物件可以宣告為[資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)、 在多個物件之間共用，以及複製。</span><span class="sxs-lookup"><span data-stu-id="999ab-190">Because it inherits from the <xref:System.Windows.Freezable> class, the <xref:System.Windows.Media.Brush> class provides several special features: <xref:System.Windows.Media.Brush> objects can be declared as [resources](../../../../docs/framework/wpf/advanced/xaml-resources.md), shared among multiple objects, and cloned.</span></span> <span data-ttu-id="999ab-191">此外，所有<xref:System.Windows.Media.Brush>類型除了<xref:System.Windows.Media.VisualBrush>可以變成唯讀，以改善效能並進行安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="999ab-191">In addition, all the <xref:System.Windows.Media.Brush> types except <xref:System.Windows.Media.VisualBrush> can be made read-only to improve performance and made thread-safe.</span></span>  
  
 <span data-ttu-id="999ab-192">如需有關所提供的不同功能<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="999ab-192">For more information about the different features provided by <xref:System.Windows.Freezable> objects, see [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
 <span data-ttu-id="999ab-193">如需有關為什麼<xref:System.Windows.Media.VisualBrush>物件不能是凍結時，請參閱<xref:System.Windows.Media.VisualBrush>類型 頁面。</span><span class="sxs-lookup"><span data-stu-id="999ab-193">For more information on why <xref:System.Windows.Media.VisualBrush> objects cannot be frozen, see the <xref:System.Windows.Media.VisualBrush> type page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="999ab-194">請參閱</span><span class="sxs-lookup"><span data-stu-id="999ab-194">See Also</span></span>  
 <xref:System.Windows.Media.Brush>  
 <xref:System.Windows.Media.Brushes>  
 [<span data-ttu-id="999ab-195">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="999ab-195">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="999ab-196">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="999ab-196">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="999ab-197">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="999ab-197">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="999ab-198">筆刷範例</span><span class="sxs-lookup"><span data-stu-id="999ab-198">Brushes Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159973)  
 [<span data-ttu-id="999ab-199">ImageBrush 範例</span><span class="sxs-lookup"><span data-stu-id="999ab-199">ImageBrush Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [<span data-ttu-id="999ab-200">VisualBrush 範例</span><span class="sxs-lookup"><span data-stu-id="999ab-200">VisualBrush Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160049)  
 [<span data-ttu-id="999ab-201">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="999ab-201">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [<span data-ttu-id="999ab-202">其他效能建議</span><span class="sxs-lookup"><span data-stu-id="999ab-202">Other Performance Recommendations</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
