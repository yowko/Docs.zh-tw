---
title: 最佳化效能：其他建議
ms.date: 03/30/2017
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
ms.openlocfilehash: 727331adb41251460209f157d1804ff455bcf473
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186307"
---
# <a name="optimizing-performance-other-recommendations"></a><span data-ttu-id="54bfb-102">最佳化效能：其他建議</span><span class="sxs-lookup"><span data-stu-id="54bfb-102">Optimizing Performance: Other Recommendations</span></span>
<a name="introduction"></a> <span data-ttu-id="54bfb-103">本主題提供[最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)一節中主題所涵蓋內容以外的效能建議。</span><span class="sxs-lookup"><span data-stu-id="54bfb-103">This topic provides performance recommendations in addition to the ones covered by the topics in the [Optimizing WPF Application Performance](optimizing-wpf-application-performance.md) section.</span></span>  
  
 <span data-ttu-id="54bfb-104">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="54bfb-104">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="54bfb-105">筆刷透明度與項目透明度的比較</span><span class="sxs-lookup"><span data-stu-id="54bfb-105">Opacity on Brushes Versus Opacity on Elements</span></span>](#Opacity)  
  
- [<span data-ttu-id="54bfb-106">物件瀏覽</span><span class="sxs-lookup"><span data-stu-id="54bfb-106">Navigation to Object</span></span>](#Navigation_Objects)  
  
- [<span data-ttu-id="54bfb-107">大型立體表面的點擊測試</span><span class="sxs-lookup"><span data-stu-id="54bfb-107">Hit Testing on Large 3D Surfaces</span></span>](#Hit_Testing)  
  
- [<span data-ttu-id="54bfb-108">CompositionTarget.Rendering 事件</span><span class="sxs-lookup"><span data-stu-id="54bfb-108">CompositionTarget.Rendering Event</span></span>](#CompositionTarget_Rendering_Event)  
  
- [<span data-ttu-id="54bfb-109">避免使用 ScrollBarVisibility = Auto</span><span class="sxs-lookup"><span data-stu-id="54bfb-109">Avoid Using ScrollBarVisibility=Auto</span></span>](#Avoid_Using_ScrollBarVisibility)  
  
- [<span data-ttu-id="54bfb-110">設定字型快取服務以縮短啟動時間</span><span class="sxs-lookup"><span data-stu-id="54bfb-110">Configure Font Cache Service to Reduce Start-up Time</span></span>](#FontCache)  
  
<a name="Opacity"></a>
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a><span data-ttu-id="54bfb-111">筆刷透明度與項目透明度的比較</span><span class="sxs-lookup"><span data-stu-id="54bfb-111">Opacity on Brushes Versus Opacity on Elements</span></span>  
 <span data-ttu-id="54bfb-112"><xref:System.Windows.Media.Brush>使用 設置 元素<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Shape.Stroke%2A>或 時，最好設置<xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType>值，而不是設置元素的屬性。 <xref:System.Windows.UIElement.Opacity%2A></span><span class="sxs-lookup"><span data-stu-id="54bfb-112">When you use a <xref:System.Windows.Media.Brush> to set the <xref:System.Windows.Shapes.Shape.Fill%2A> or <xref:System.Windows.Shapes.Shape.Stroke%2A> of an element, it is better to set the <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> value rather than the setting the element's <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="54bfb-113">修改元素的屬性<xref:System.Windows.UIElement.Opacity%2A>可能會導致[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]創建臨時曲面。</span><span class="sxs-lookup"><span data-stu-id="54bfb-113">Modifying an element's <xref:System.Windows.UIElement.Opacity%2A> property can cause [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to create a temporary surface.</span></span>  
  
<a name="Navigation_Objects"></a>
## <a name="navigation-to-object"></a><span data-ttu-id="54bfb-114">物件瀏覽</span><span class="sxs-lookup"><span data-stu-id="54bfb-114">Navigation to Object</span></span>  
 <span data-ttu-id="54bfb-115">物件<xref:System.Windows.Navigation.NavigationWindow>派生自<xref:System.Windows.Window>內容導航支援並擴展它，主要通過聚合<xref:System.Windows.Navigation.NavigationService>和日誌。</span><span class="sxs-lookup"><span data-stu-id="54bfb-115">The <xref:System.Windows.Navigation.NavigationWindow> object derives from <xref:System.Windows.Window> and extends it with content navigation support, primarily by aggregating <xref:System.Windows.Navigation.NavigationService> and the journal.</span></span> <span data-ttu-id="54bfb-116">可以通過指定統一的資源識別碼<xref:System.Windows.Navigation.NavigationWindow>（URI） 或物件來更新 的工作區。</span><span class="sxs-lookup"><span data-stu-id="54bfb-116">You can update the client area of <xref:System.Windows.Navigation.NavigationWindow> by specifying either a uniform resource identifier (URI) or an object.</span></span> <span data-ttu-id="54bfb-117">下列範例將顯示這兩種方法：</span><span class="sxs-lookup"><span data-stu-id="54bfb-117">The following sample shows both methods:</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 <span data-ttu-id="54bfb-118">每個<xref:System.Windows.Navigation.NavigationWindow>物件都有一個日誌，記錄使用者在該視窗中的導航歷史記錄。</span><span class="sxs-lookup"><span data-stu-id="54bfb-118">Each <xref:System.Windows.Navigation.NavigationWindow> object has a journal that records the user's navigation history in that window.</span></span> <span data-ttu-id="54bfb-119">日誌的用途之一，就是讓使用者能夠追溯其步驟。</span><span class="sxs-lookup"><span data-stu-id="54bfb-119">One of the purposes of the journal is to allow users to retrace their steps.</span></span>  
  
 <span data-ttu-id="54bfb-120">使用統一的資源識別碼 （URI） 導航時，日誌僅存儲統一的資源識別碼 （URI） 引用。</span><span class="sxs-lookup"><span data-stu-id="54bfb-120">When you navigate using a uniform resource identifier (URI), the journal stores only the uniform resource identifier (URI) reference.</span></span> <span data-ttu-id="54bfb-121">這表示您每次重新瀏覽頁面時，它都會動態重新建構，如果頁面相當複雜，就有可能耗費許多時間。</span><span class="sxs-lookup"><span data-stu-id="54bfb-121">This means that each time you revisit the page, it is dynamically reconstructed, which may be time consuming depending on the complexity of the page.</span></span> <span data-ttu-id="54bfb-122">在此情況下，日誌儲存成本雖然較低，但重新建構頁面所需的時間則可能很長。</span><span class="sxs-lookup"><span data-stu-id="54bfb-122">In this case, the journal storage cost is low, but the time to reconstitute the page is potentially high.</span></span>  
  
 <span data-ttu-id="54bfb-123">當您使用物件進行瀏覽時，日誌會儲存該物件的整個視覺化樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="54bfb-123">When you navigate using an object, the journal stores the entire visual tree of the object.</span></span> <span data-ttu-id="54bfb-124">這表示在您每次重新瀏覽頁面時，它都會立即呈現而不需重新建構。</span><span class="sxs-lookup"><span data-stu-id="54bfb-124">This means that each time you revisit the page, it renders immediately without having to be reconstructed.</span></span> <span data-ttu-id="54bfb-125">在此情況下，日誌儲存成本較高，但重新建構頁面所需的時間較短。</span><span class="sxs-lookup"><span data-stu-id="54bfb-125">In this case, the journal storage cost is high, but the time to reconstitute the page is low.</span></span>  
  
 <span data-ttu-id="54bfb-126">使用 物件時<xref:System.Windows.Navigation.NavigationWindow>，需要牢記日記支援如何影響應用程式的性能。</span><span class="sxs-lookup"><span data-stu-id="54bfb-126">When you use the <xref:System.Windows.Navigation.NavigationWindow> object, you will need to keep in mind how the journaling support impacts your application's performance.</span></span> <span data-ttu-id="54bfb-127">如需詳細資訊，請參閱[覽概觀](../app-development/navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="54bfb-127">For more information, see [Navigation Overview](../app-development/navigation-overview.md).</span></span>  
  
<a name="Hit_Testing"></a>
## <a name="hit-testing-on-large-3d-surfaces"></a><span data-ttu-id="54bfb-128">大型立體表面的點擊測試</span><span class="sxs-lookup"><span data-stu-id="54bfb-128">Hit Testing on Large 3D Surfaces</span></span>  
 <span data-ttu-id="54bfb-129">就 CPU 的耗用量而言，大型立體表面的點擊測試是一項很耗損效能的作業。</span><span class="sxs-lookup"><span data-stu-id="54bfb-129">Hit testing on large 3D surfaces is a very performance intensive operation in terms of CPU consumption.</span></span> <span data-ttu-id="54bfb-130">當立體表面為動畫形式時，更是如此。</span><span class="sxs-lookup"><span data-stu-id="54bfb-130">This is especially true when the 3D surface is animating.</span></span> <span data-ttu-id="54bfb-131">若您不需要對這些表面進行點擊測試，請停用點擊測試。</span><span class="sxs-lookup"><span data-stu-id="54bfb-131">If you do not require hit testing on these surfaces, then disable hit testing.</span></span> <span data-ttu-id="54bfb-132">派生自<xref:System.Windows.UIElement>的物件可以通過將<xref:System.Windows.UIElement.IsHitTestVisible%2A>屬性設置為`false`來禁用點擊測試。</span><span class="sxs-lookup"><span data-stu-id="54bfb-132">Objects that are derived from <xref:System.Windows.UIElement> can disable hit testing by setting the <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to `false`.</span></span>  
  
<a name="CompositionTarget_Rendering_Event"></a>
## <a name="compositiontargetrendering-event"></a><span data-ttu-id="54bfb-133">CompositionTarget.Rendering 事件</span><span class="sxs-lookup"><span data-stu-id="54bfb-133">CompositionTarget.Rendering Event</span></span>  
 <span data-ttu-id="54bfb-134">該<xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType>事件導致[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]連續設置動畫。</span><span class="sxs-lookup"><span data-stu-id="54bfb-134">The <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> event causes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to continuously animate.</span></span> <span data-ttu-id="54bfb-135">若使用此事件，請盡可能中斷其連結。</span><span class="sxs-lookup"><span data-stu-id="54bfb-135">If you use this event, detach it at every opportunity.</span></span>  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>
## <a name="avoid-using-scrollbarvisibilityauto"></a><span data-ttu-id="54bfb-136">避免使用 ScrollBarVisibility = Auto</span><span class="sxs-lookup"><span data-stu-id="54bfb-136">Avoid Using ScrollBarVisibility=Auto</span></span>  
 <span data-ttu-id="54bfb-137">盡可能避免使用 和<xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType>`HorizontalScrollBarVisibility``VerticalScrollBarVisibility`屬性的值。</span><span class="sxs-lookup"><span data-stu-id="54bfb-137">Whenever possible, avoid using the <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> value for the `HorizontalScrollBarVisibility` and `VerticalScrollBarVisibility` properties.</span></span> <span data-ttu-id="54bfb-138"><xref:System.Windows.Controls.RichTextBox>這些屬性為<xref:System.Windows.Controls.ScrollViewer>和<xref:System.Windows.Controls.TextBox>物件以及作為<xref:System.Windows.Controls.ListBox>物件的附加屬性定義。</span><span class="sxs-lookup"><span data-stu-id="54bfb-138">These properties are defined for <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer>, and <xref:System.Windows.Controls.TextBox> objects, and as an attached property for the <xref:System.Windows.Controls.ListBox> object.</span></span> <span data-ttu-id="54bfb-139"><xref:System.Windows.Controls.ScrollBarVisibility>而是設置為<xref:System.Windows.Controls.ScrollBarVisibility.Disabled>，<xref:System.Windows.Controls.ScrollBarVisibility.Hidden>或<xref:System.Windows.Controls.ScrollBarVisibility.Visible>。</span><span class="sxs-lookup"><span data-stu-id="54bfb-139">Instead, set <xref:System.Windows.Controls.ScrollBarVisibility> to <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>, or <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.</span></span>  
  
 <span data-ttu-id="54bfb-140">該<xref:System.Windows.Controls.ScrollBarVisibility.Auto>值適用于空間有限且僅在必要時顯示捲軸的情況。</span><span class="sxs-lookup"><span data-stu-id="54bfb-140">The <xref:System.Windows.Controls.ScrollBarVisibility.Auto> value is intended for cases when space is limited and scrollbars should only be displayed when necessary.</span></span> <span data-ttu-id="54bfb-141">例如，將此值<xref:System.Windows.Controls.ScrollBarVisibility>與 30 個<xref:System.Windows.Controls.ListBox>項（而不是包含數百行文本的項<xref:System.Windows.Controls.TextBox>）使用可能很有用。</span><span class="sxs-lookup"><span data-stu-id="54bfb-141">For example, it may be useful to use this <xref:System.Windows.Controls.ScrollBarVisibility> value with a <xref:System.Windows.Controls.ListBox> of 30 items as opposed to a <xref:System.Windows.Controls.TextBox> with hundreds of lines of text.</span></span>  
  
<a name="FontCache"></a>
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a><span data-ttu-id="54bfb-142">設定字型快取服務以縮短啟動時間</span><span class="sxs-lookup"><span data-stu-id="54bfb-142">Configure Font Cache Service to Reduce Start-up Time</span></span>  
 <span data-ttu-id="54bfb-143">WPF 字型快取服務在 WPF 應用程式之間共用字體資料。</span><span class="sxs-lookup"><span data-stu-id="54bfb-143">The WPF Font Cache service shares font data between WPF applications.</span></span> <span data-ttu-id="54bfb-144">如果服務尚未運行，則運行的第一個 WPF 應用程式將啟動此服務。</span><span class="sxs-lookup"><span data-stu-id="54bfb-144">The first WPF application you run starts this service if the service is not already running.</span></span> <span data-ttu-id="54bfb-145">如果使用 Windows Vista，則可以將"Windows 演示基礎 （WPF） 字體緩存 3.0.0"服務從"手動"（預設值）設置為"自動（延遲啟動）"，以減少 WPF 應用程式的初始啟動時間。</span><span class="sxs-lookup"><span data-stu-id="54bfb-145">If you are using Windows Vista, you can set the "Windows Presentation Foundation (WPF) Font Cache 3.0.0.0" service from "Manual" (the default) to "Automatic (Delayed Start)" to reduce the initial start-up time of WPF applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54bfb-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54bfb-146">See also</span></span>

- [<span data-ttu-id="54bfb-147">應用程式效能規劃</span><span class="sxs-lookup"><span data-stu-id="54bfb-147">Planning for Application Performance</span></span>](planning-for-application-performance.md)
- [<span data-ttu-id="54bfb-148">運用硬體</span><span class="sxs-lookup"><span data-stu-id="54bfb-148">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)
- [<span data-ttu-id="54bfb-149">版面配置與設計</span><span class="sxs-lookup"><span data-stu-id="54bfb-149">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)
- [<span data-ttu-id="54bfb-150">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="54bfb-150">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="54bfb-151">物件行為</span><span class="sxs-lookup"><span data-stu-id="54bfb-151">Object Behavior</span></span>](optimizing-performance-object-behavior.md)
- [<span data-ttu-id="54bfb-152">應用程式資源</span><span class="sxs-lookup"><span data-stu-id="54bfb-152">Application Resources</span></span>](optimizing-performance-application-resources.md)
- [<span data-ttu-id="54bfb-153">文本</span><span class="sxs-lookup"><span data-stu-id="54bfb-153">Text</span></span>](optimizing-performance-text.md)
- [<span data-ttu-id="54bfb-154">資料繫結</span><span class="sxs-lookup"><span data-stu-id="54bfb-154">Data Binding</span></span>](optimizing-performance-data-binding.md)
- [<span data-ttu-id="54bfb-155">動畫祕訣和訣竅</span><span class="sxs-lookup"><span data-stu-id="54bfb-155">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
