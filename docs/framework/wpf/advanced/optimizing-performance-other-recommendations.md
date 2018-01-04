---
title: "最佳化效能：其他建議"
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
- Terminal Services rendering [WPF]
- opacity [WPF]
- hit-test objects [WPF]
- ScrollBarVisibility enumeration [WPF]
- brushes [WPF], performance
ms.assetid: d028cc65-7e97-4a4f-9859-929734eaf40d
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e45296befd51af5e4b03f123241efba030fd3754
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-performance-other-recommendations"></a><span data-ttu-id="4e5b6-102">最佳化效能：其他建議</span><span class="sxs-lookup"><span data-stu-id="4e5b6-102">Optimizing Performance: Other Recommendations</span></span>
<a name="introduction"></a> <span data-ttu-id="4e5b6-103">本主題提供[最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)一節中主題所涵蓋內容以外的效能建議。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-103">This topic provides performance recommendations in addition to the ones covered by the topics in the [Optimizing WPF Application Performance](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md) section.</span></span>  
  
 <span data-ttu-id="4e5b6-104">此主題包括下列章節：</span><span class="sxs-lookup"><span data-stu-id="4e5b6-104">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="4e5b6-105">筆刷透明度與項目透明度的比較</span><span class="sxs-lookup"><span data-stu-id="4e5b6-105">Opacity on Brushes Versus Opacity on Elements</span></span>](#Opacity)  
  
-   [<span data-ttu-id="4e5b6-106">物件瀏1覽</span><span class="sxs-lookup"><span data-stu-id="4e5b6-106">Navigation to Object</span></span>](#Navigation_Objects)  
  
-   [<span data-ttu-id="4e5b6-107">大型立體表面的點擊測試</span><span class="sxs-lookup"><span data-stu-id="4e5b6-107">Hit Testing on Large 3D Surfaces</span></span>](#Hit_Testing)  
  
-   [<span data-ttu-id="4e5b6-108">CompositionTarget.Rendering 事件</span><span class="sxs-lookup"><span data-stu-id="4e5b6-108">CompositionTarget.Rendering Event</span></span>](#CompositionTarget_Rendering_Event)  
  
-   [<span data-ttu-id="4e5b6-109">避免使用 ScrollBarVisibility = Auto</span><span class="sxs-lookup"><span data-stu-id="4e5b6-109">Avoid Using ScrollBarVisibility=Auto</span></span>](#Avoid_Using_ScrollBarVisibility)  
  
-   [<span data-ttu-id="4e5b6-110">設定字型快取服務以縮短啟動時間</span><span class="sxs-lookup"><span data-stu-id="4e5b6-110">Configure Font Cache Service to Reduce Start-up Time</span></span>](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a><span data-ttu-id="4e5b6-111">筆刷透明度與項目透明度的比較</span><span class="sxs-lookup"><span data-stu-id="4e5b6-111">Opacity on Brushes Versus Opacity on Elements</span></span>  
 <span data-ttu-id="4e5b6-112">當您使用<xref:System.Windows.Media.Brush>設定<xref:System.Windows.Shapes.Shape.Fill%2A>或<xref:System.Windows.Shapes.Shape.Stroke%2A>的項目，最好是在設定<xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType>值而非設定的項目<xref:System.Windows.UIElement.Opacity%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-112">When you use a <xref:System.Windows.Media.Brush> to set the <xref:System.Windows.Shapes.Shape.Fill%2A> or <xref:System.Windows.Shapes.Shape.Stroke%2A> of an element, it is better to set the <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> value rather than the setting the element's <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="4e5b6-113">修改的項目<xref:System.Windows.UIElement.Opacity%2A>屬性可能會導致[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]建立暫存的介面。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-113">Modifying an element's <xref:System.Windows.UIElement.Opacity%2A> property can cause [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to create a temporary surface.</span></span>  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a><span data-ttu-id="4e5b6-114">物件瀏覽</span><span class="sxs-lookup"><span data-stu-id="4e5b6-114">Navigation to Object</span></span>  
 <span data-ttu-id="4e5b6-115"><xref:System.Windows.Navigation.NavigationWindow>物件衍生自<xref:System.Windows.Window>，並擴充內容巡覽的支援，主要是彙總<xref:System.Windows.Navigation.NavigationService>和日誌。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-115">The <xref:System.Windows.Navigation.NavigationWindow> object derives from <xref:System.Windows.Window> and extends it with content navigation support, primarily by aggregating <xref:System.Windows.Navigation.NavigationService> and the journal.</span></span> <span data-ttu-id="4e5b6-116">您可以更新的用戶端區域<xref:System.Windows.Navigation.NavigationWindow>藉由指定[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]或物件。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-116">You can update the client area of <xref:System.Windows.Navigation.NavigationWindow> by specifying either a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] or an object.</span></span> <span data-ttu-id="4e5b6-117">下列範例將顯示這兩種方法：</span><span class="sxs-lookup"><span data-stu-id="4e5b6-117">The following sample shows both methods:</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 <span data-ttu-id="4e5b6-118">每個<xref:System.Windows.Navigation.NavigationWindow>物件具有該視窗中會記錄使用者的瀏覽歷程記錄的日誌。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-118">Each <xref:System.Windows.Navigation.NavigationWindow> object has a journal that records the user's navigation history in that window.</span></span> <span data-ttu-id="4e5b6-119">日誌的用途之一，就是讓使用者能夠追溯其步驟。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-119">One of the purposes of the journal is to allow users to retrace their steps.</span></span>  
  
 <span data-ttu-id="4e5b6-120">當您使用 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 進行巡覽時，日誌只會儲存 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 參考。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-120">When you navigate using a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], the journal stores only the [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] reference.</span></span> <span data-ttu-id="4e5b6-121">這表示您每次重新瀏覽頁面時，它都會動態重新建構，如果頁面相當複雜，就有可能耗費許多時間。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-121">This means that each time you revisit the page, it is dynamically reconstructed, which may be time consuming depending on the complexity of the page.</span></span> <span data-ttu-id="4e5b6-122">在此情況下，日誌儲存成本雖然較低，但重新建構頁面所需的時間則可能很長。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-122">In this case, the journal storage cost is low, but the time to reconstitute the page is potentially high.</span></span>  
  
 <span data-ttu-id="4e5b6-123">當您使用物件進行瀏覽時，日誌會儲存該物件的整個視覺化樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-123">When you navigate using an object, the journal stores the entire visual tree of the object.</span></span> <span data-ttu-id="4e5b6-124">這表示在您每次重新瀏覽頁面時，它都會立即呈現而不需重新建構。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-124">This means that each time you revisit the page, it renders immediately without having to be reconstructed.</span></span> <span data-ttu-id="4e5b6-125">在此情況下，日誌儲存成本較高，但重新建構頁面所需的時間較短。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-125">In this case, the journal storage cost is high, but the time to reconstitute the page is low.</span></span>  
  
 <span data-ttu-id="4e5b6-126">當您使用<xref:System.Windows.Navigation.NavigationWindow>物件，您必須謹記在心的日誌支援如何影響您的應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-126">When you use the <xref:System.Windows.Navigation.NavigationWindow> object, you will need to keep in mind how the journaling support impacts your application's performance.</span></span> <span data-ttu-id="4e5b6-127">如需詳細資訊，請參閱[覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-127">For more information, see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span>  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a><span data-ttu-id="4e5b6-128">大型立體表面的點擊測試</span><span class="sxs-lookup"><span data-stu-id="4e5b6-128">Hit Testing on Large 3D Surfaces</span></span>  
 <span data-ttu-id="4e5b6-129">就 CPU 的耗用量而言，大型立體表面的點擊測試是一項很耗損效能的作業。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-129">Hit testing on large 3D surfaces is a very performance intensive operation in terms of CPU consumption.</span></span> <span data-ttu-id="4e5b6-130">當立體表面為動畫形式時，更是如此。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-130">This is especially true when the 3D surface is animating.</span></span> <span data-ttu-id="4e5b6-131">若您不需要對這些表面進行點擊測試，請停用點擊測試。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-131">If you do not require hit testing on these surfaces, then disable hit testing.</span></span> <span data-ttu-id="4e5b6-132">物件，衍生自<xref:System.Windows.UIElement>可以停用的點擊測試設定<xref:System.Windows.UIElement.IsHitTestVisible%2A>屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-132">Objects that are derived from <xref:System.Windows.UIElement> can disable hit testing by setting the <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to `false`.</span></span>  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a><span data-ttu-id="4e5b6-133">CompositionTarget.Rendering 事件</span><span class="sxs-lookup"><span data-stu-id="4e5b6-133">CompositionTarget.Rendering Event</span></span>  
 <span data-ttu-id="4e5b6-134"><xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType>事件導致[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]持續動畫。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-134">The <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> event causes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to continuously animate.</span></span> <span data-ttu-id="4e5b6-135">若使用此事件，請盡可能中斷其連結。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-135">If you use this event, detach it at every opportunity.</span></span>  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a><span data-ttu-id="4e5b6-136">避免使用 ScrollBarVisibility = Auto</span><span class="sxs-lookup"><span data-stu-id="4e5b6-136">Avoid Using ScrollBarVisibility=Auto</span></span>  
 <span data-ttu-id="4e5b6-137">可能的話，請避免使用<xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType>值`HorizontalScrollBarVisibility`和`VerticalScrollBarVisibility`屬性。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-137">Whenever possible, avoid using the <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> value for the `HorizontalScrollBarVisibility` and `VerticalScrollBarVisibility` properties.</span></span> <span data-ttu-id="4e5b6-138">這些屬性定義為<xref:System.Windows.Controls.RichTextBox>， <xref:System.Windows.Controls.ScrollViewer>，和<xref:System.Windows.Controls.TextBox>物件，並為附加屬性的<xref:System.Windows.Controls.ListBox>物件。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-138">These properties are defined for <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer>, and <xref:System.Windows.Controls.TextBox> objects, and as an attached property for the <xref:System.Windows.Controls.ListBox> object.</span></span> <span data-ttu-id="4e5b6-139">相反地，設定<xref:System.Windows.Controls.ScrollBarVisibility>至<xref:System.Windows.Controls.ScrollBarVisibility.Disabled>， <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>，或<xref:System.Windows.Controls.ScrollBarVisibility.Visible>。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-139">Instead, set <xref:System.Windows.Controls.ScrollBarVisibility> to <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>, or <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.</span></span>  
  
 <span data-ttu-id="4e5b6-140"><xref:System.Windows.Controls.ScrollBarVisibility.Auto>值適合的情況下，當空間被限制，並在必要時，應該只會顯示捲軸。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-140">The <xref:System.Windows.Controls.ScrollBarVisibility.Auto> value is intended for cases when space is limited and scrollbars should only be displayed when necessary.</span></span> <span data-ttu-id="4e5b6-141">例如，可能很有用使用這個<xref:System.Windows.Controls.ScrollBarVisibility>值與<xref:System.Windows.Controls.ListBox>30 個項目與<xref:System.Windows.Controls.TextBox>含有上百個行文字。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-141">For example, it may be useful to use this <xref:System.Windows.Controls.ScrollBarVisibility> value with a <xref:System.Windows.Controls.ListBox> of 30 items as opposed to a <xref:System.Windows.Controls.TextBox> with hundreds of lines of text.</span></span>  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a><span data-ttu-id="4e5b6-142">設定字型快取服務以縮短啟動時間</span><span class="sxs-lookup"><span data-stu-id="4e5b6-142">Configure Font Cache Service to Reduce Start-up Time</span></span>  
 <span data-ttu-id="4e5b6-143">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 字型快取服務可在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式之間共用字型資料。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-143">The [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Font Cache service shares font data between [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications.</span></span> <span data-ttu-id="4e5b6-144">您所執行的第一個 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式會啟動此服務 (若尚未執行)。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-144">The first [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application you run starts this service if the service is not already running.</span></span> <span data-ttu-id="4e5b6-145">若您使用 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]，即可將 "[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Font Cache 3.0.0.0" 服務從「手動」(預設值) 設定為「自動 (延遲開始)」，以縮短 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式的初始啟動時間。</span><span class="sxs-lookup"><span data-stu-id="4e5b6-145">If you are using [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], you can set the "[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Font Cache 3.0.0.0" service from "Manual" (the default) to "Automatic (Delayed Start)" to reduce the initial start-up time of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e5b6-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e5b6-146">See Also</span></span>  
 [<span data-ttu-id="4e5b6-147">應用程式效能規劃</span><span class="sxs-lookup"><span data-stu-id="4e5b6-147">Planning for Application Performance</span></span>](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [<span data-ttu-id="4e5b6-148">運用硬體</span><span class="sxs-lookup"><span data-stu-id="4e5b6-148">Taking Advantage of Hardware</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [<span data-ttu-id="4e5b6-149">版面配置與設計</span><span class="sxs-lookup"><span data-stu-id="4e5b6-149">Layout and Design</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [<span data-ttu-id="4e5b6-150">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="4e5b6-150">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [<span data-ttu-id="4e5b6-151">物件行為</span><span class="sxs-lookup"><span data-stu-id="4e5b6-151">Object Behavior</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [<span data-ttu-id="4e5b6-152">應用程式資源</span><span class="sxs-lookup"><span data-stu-id="4e5b6-152">Application Resources</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [<span data-ttu-id="4e5b6-153">Text</span><span class="sxs-lookup"><span data-stu-id="4e5b6-153">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [<span data-ttu-id="4e5b6-154">資料繫結</span><span class="sxs-lookup"><span data-stu-id="4e5b6-154">Data Binding</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [<span data-ttu-id="4e5b6-155">動畫祕訣和訣竅</span><span class="sxs-lookup"><span data-stu-id="4e5b6-155">Animation Tips and Tricks</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
