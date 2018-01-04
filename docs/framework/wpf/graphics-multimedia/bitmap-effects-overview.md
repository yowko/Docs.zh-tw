---
title: "點陣圖效果概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f642c699a0ecf3e3cce328363f90110766002e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="bitmap-effects-overview"></a><span data-ttu-id="c7ff3-102">點陣圖效果概觀</span><span class="sxs-lookup"><span data-stu-id="c7ff3-102">Bitmap Effects Overview</span></span>
<span data-ttu-id="c7ff3-103">點陣圖效果可讓設計人員與開發人員對轉譯的 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 內容套用視覺效果。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-103">Bitmap effects enable designers and developers to apply visual effects to rendered [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="c7ff3-104">例如，點陣圖效果可讓您輕鬆地套用<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>效果或模糊效果的影像或按鈕。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-104">For example, bitmap effects allow you to easily apply a <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> effect or a blur effect to an image or a button.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7ff3-105">在[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]或更新版本，<xref:System.Windows.Media.Effects.BitmapEffect>類別已經過時。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-105">In the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] or later, the <xref:System.Windows.Media.Effects.BitmapEffect> class is obsolete.</span></span> <span data-ttu-id="c7ff3-106">如果您嘗試使用<xref:System.Windows.Media.Effects.BitmapEffect>類別，就會過時的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-106">If you try to use the <xref:System.Windows.Media.Effects.BitmapEffect> class, you will get an obsolete exception.</span></span> <span data-ttu-id="c7ff3-107">非過時的替代方式，來<xref:System.Windows.Media.Effects.BitmapEffect>類別是<xref:System.Windows.Media.Effects.Effect>類別。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-107">The non-obsolete alternative to the <xref:System.Windows.Media.Effects.BitmapEffect> class is the <xref:System.Windows.Media.Effects.Effect> class.</span></span> <span data-ttu-id="c7ff3-108">在大部分情況下，<xref:System.Windows.Media.Effects.Effect>類別會更快。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-108">In most situations, the <xref:System.Windows.Media.Effects.Effect> class is significantly faster.</span></span>  
  
  
  
<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a><span data-ttu-id="c7ff3-109">WPF 點陣圖效果</span><span class="sxs-lookup"><span data-stu-id="c7ff3-109">WPF Bitmap Effects</span></span>  
 <span data-ttu-id="c7ff3-110">點陣圖效果 (<xref:System.Windows.Media.Effects.BitmapEffect>物件) 是簡單的像素的處理作業。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-110">Bitmap effects (<xref:System.Windows.Media.Effects.BitmapEffect> object) are simple pixel processing operations.</span></span> <span data-ttu-id="c7ff3-111">點陣圖效果<xref:System.Windows.Media.Imaging.BitmapSource>做為輸入並產生新<xref:System.Windows.Media.Imaging.BitmapSource>之後套用效果，例如柔邊或 drop 陰影。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-111">A bitmap effect takes a <xref:System.Windows.Media.Imaging.BitmapSource> as an input and produces a new <xref:System.Windows.Media.Imaging.BitmapSource> after applying the effect, such as a blur or drop shadow.</span></span> <span data-ttu-id="c7ff3-112">每個點陣圖效果公開屬性，可以控制篩選的屬性，例如<xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A>的<xref:System.Windows.Media.Effects.BlurBitmapEffect>。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-112">Each bitmap effect exposes properties that can control the filtering properties, such as <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> of <xref:System.Windows.Media.Effects.BlurBitmapEffect>.</span></span>  
  
 <span data-ttu-id="c7ff3-113">做為特殊案例，在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，效果可以做為屬性上設定即時<xref:System.Windows.Media.Visual>物件，例如<xref:System.Windows.Controls.Button>或<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-113">As a special case, in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], effects can be set as properties on live <xref:System.Windows.Media.Visual> objects, such as a <xref:System.Windows.Controls.Button> or <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="c7ff3-114">像素處理會在執行階段套用並進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-114">The pixel processing is applied and rendered at run-time.</span></span> <span data-ttu-id="c7ff3-115">在此情況下，在轉譯時<xref:System.Windows.Media.Visual>自動轉換為其<xref:System.Windows.Media.Imaging.BitmapSource>相等和 fed 做為輸入<xref:System.Windows.Media.Effects.BitmapEffect>。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-115">In this case, at the time of rendering, a <xref:System.Windows.Media.Visual> is automatically converted to its <xref:System.Windows.Media.Imaging.BitmapSource> equivalent and is fed as input to the <xref:System.Windows.Media.Effects.BitmapEffect>.</span></span> <span data-ttu-id="c7ff3-116">輸出會取代<xref:System.Windows.Media.Visual>物件的預設轉譯行為。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-116">The output replaces the <xref:System.Windows.Media.Visual> object's default rendering behavior.</span></span> <span data-ttu-id="c7ff3-117">這就是為什麼<xref:System.Windows.Media.Effects.BitmapEffect>物件強制呈現在軟體中只有也就是沒有視覺效果的硬體加速效果套用時的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-117">This is why <xref:System.Windows.Media.Effects.BitmapEffect> objects force visuals to render in software only i.e. no hardware acceleration on visuals when effects are applied.</span></span>  
  
-   <span data-ttu-id="c7ff3-118"><xref:System.Windows.Media.Effects.BlurBitmapEffect>模擬會出現失焦的物件。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-118"><xref:System.Windows.Media.Effects.BlurBitmapEffect> simulates an object that appears out-of-focus.</span></span>  
  
-   <span data-ttu-id="c7ff3-119"><xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>建立物件周圍的色彩的光暈。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-119"><xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> creates a halo of color around the perimeter of an object.</span></span>  
  
-   <span data-ttu-id="c7ff3-120"><xref:System.Windows.Media.Effects.DropShadowBitmapEffect>建立物件後的陰影。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-120"><xref:System.Windows.Media.Effects.DropShadowBitmapEffect> creates a shadow behind an object.</span></span>  
  
-   <span data-ttu-id="c7ff3-121"><xref:System.Windows.Media.Effects.BevelBitmapEffect>建立斜面，它會根據指定的曲線影像表面。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-121"><xref:System.Windows.Media.Effects.BevelBitmapEffect> creates a bevel which raises the surface of an image according to a specified curve.</span></span>  
  
-   <span data-ttu-id="c7ff3-122"><xref:System.Windows.Media.Effects.EmbossBitmapEffect>建立的凹凸貼圖<xref:System.Windows.Media.Visual>的深度和紋理從人工光源。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-122"><xref:System.Windows.Media.Effects.EmbossBitmapEffect> creates a bump mapping of a <xref:System.Windows.Media.Visual> to give the impression of depth and texture from an artificial light source.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="c7ff3-123"> 點陣圖效果是在軟體模式中轉譯。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-123"> bitmap effects are rendered in software mode.</span></span> <span data-ttu-id="c7ff3-124">套用效果的任何物件也會在軟體中轉譯。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-124">Any object that applies an effect will also be rendered in software.</span></span> <span data-ttu-id="c7ff3-125">對大型視覺物件使用點陣圖效果或為點陣圖效果的屬性建立動畫時，效能會降低最多。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-125">Performance is degraded the most when using Bitmap effects on large visuals or animating properties of a Bitmap effect.</span></span> <span data-ttu-id="c7ff3-126">這並不是說您不應該以此種方式使用點陣圖效果，而是您應特別小心並徹底測試，以確保使用者能得到預期的體驗。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-126">This is not to say that you should not use Bitmap effects in this way at all, but you should use caution and test thoroughly to ensure that your users are getting the experience you expect.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="c7ff3-127"> 點陣圖效果不支援部分信任執行。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-127"> bitmap effects do not support partial trust execution.</span></span> <span data-ttu-id="c7ff3-128">應用程式必須有完全信任權限才能使用點陣圖效果。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-128">An application must have full trust permissions to use bitmap effects.</span></span>  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a><span data-ttu-id="c7ff3-129">如何套用效果</span><span class="sxs-lookup"><span data-stu-id="c7ff3-129">How to Apply an Effect</span></span>  
 <span data-ttu-id="c7ff3-130"><xref:System.Windows.Media.Effects.BitmapEffect>是一個屬性上<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-130"><xref:System.Windows.Media.Effects.BitmapEffect> is a property on <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="c7ff3-131">因此這類將效果套用至視覺效果、 <xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.Image>， <xref:System.Windows.Media.DrawingVisual>，或<xref:System.Windows.UIElement>，只要設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-131">Therefore applying effects to Visuals, such as a <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>, or <xref:System.Windows.UIElement>, is as easy as setting a property.</span></span> <span data-ttu-id="c7ff3-132"><xref:System.Windows.UIElement.BitmapEffect%2A>可以設為單一<xref:System.Windows.Media.Effects.BitmapEffect>物件或多個效果可以鏈結在使用<xref:System.Windows.Media.Effects.BitmapEffectGroup>物件。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-132"><xref:System.Windows.UIElement.BitmapEffect%2A> can be set to a single <xref:System.Windows.Media.Effects.BitmapEffect> object or multiple effects can be chained by using the <xref:System.Windows.Media.Effects.BitmapEffectGroup> object.</span></span>  
  
 <span data-ttu-id="c7ff3-133">下列範例示範如何套用<xref:System.Windows.Media.Effects.BitmapEffect>中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-133">The following example demonstrates how to apply a <xref:System.Windows.Media.Effects.BitmapEffect> in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 <span data-ttu-id="c7ff3-134">下列範例示範如何套用<xref:System.Windows.Media.Effects.BitmapEffect>程式碼中。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-134">The following example demonstrates how to apply a <xref:System.Windows.Media.Effects.BitmapEffect> in code.</span></span>  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  <span data-ttu-id="c7ff3-135">當<xref:System.Windows.Media.Effects.BitmapEffect>套用至版面配置容器，例如<xref:System.Windows.Controls.DockPanel>或<xref:System.Windows.Controls.Canvas>，則套用效果的視覺化樹狀結構項目或視覺效果，包括所有其子項目。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-135">When a <xref:System.Windows.Media.Effects.BitmapEffect> is applied to a layout container, such as <xref:System.Windows.Controls.DockPanel> or <xref:System.Windows.Controls.Canvas>, the effect is applied to the visual tree of the element or visual, including all of its child elements.</span></span>  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a><span data-ttu-id="c7ff3-136">建立自訂效果</span><span class="sxs-lookup"><span data-stu-id="c7ff3-136">Creating Custom Effects</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="c7ff3-137"> 也提供 Unmanaged 介面以建立可在 Managed [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式中使用的自訂效果。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-137"> also provides unmanaged interfaces to create custom effects that can be used in managed [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications.</span></span> <span data-ttu-id="c7ff3-138">如需建立自訂點陣圖效果的其他參考資料，請參閱 [Unmanaged WPF 點陣圖效果 (英文)](https://msdn.microsoft.com/library/ms735092.aspx) 文件。</span><span class="sxs-lookup"><span data-stu-id="c7ff3-138">For additional reference material for creating custom bitmap effects, see the [Unmanaged WPF Bitmap Effect](https://msdn.microsoft.com/library/ms735092.aspx) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7ff3-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="c7ff3-139">See Also</span></span>  
 <xref:System.Windows.Media.Effects.BitmapEffectGroup>  
 <xref:System.Windows.Media.Effects.BitmapEffectInput>  
 <xref:System.Windows.Media.Effects.BitmapEffectCollection>  
 [<span data-ttu-id="c7ff3-140">Unmanaged 的 WPF 點陣圖效果</span><span class="sxs-lookup"><span data-stu-id="c7ff3-140">Unmanaged WPF Bitmap Effect</span></span>](https://msdn.microsoft.com/library/ms735092.aspx)  
 [<span data-ttu-id="c7ff3-141">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="c7ff3-141">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [<span data-ttu-id="c7ff3-142">安全性</span><span class="sxs-lookup"><span data-stu-id="c7ff3-142">Security</span></span>](../../../../docs/framework/wpf/security-wpf.md)  
 [<span data-ttu-id="c7ff3-143">WPF 圖形轉譯概觀</span><span class="sxs-lookup"><span data-stu-id="c7ff3-143">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [<span data-ttu-id="c7ff3-144">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="c7ff3-144">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
