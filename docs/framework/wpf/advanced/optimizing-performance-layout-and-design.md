---
title: 最佳化效能：配置與設計
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
ms.openlocfilehash: 9c9921e664d69038480e73ee6779ca9e48b81c7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547832"
---
# <a name="optimizing-performance-layout-and-design"></a><span data-ttu-id="d82e0-102">最佳化效能：配置與設計</span><span class="sxs-lookup"><span data-stu-id="d82e0-102">Optimizing Performance: Layout and Design</span></span>
<span data-ttu-id="d82e0-103">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的設計可能會因為在計算版面配置和驗證物件參考而產生不必要的額外負荷，進而影響其效能。</span><span class="sxs-lookup"><span data-stu-id="d82e0-103">The design of your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application can impact its performance by creating unnecessary overhead in calculating layout and validating object references.</span></span> <span data-ttu-id="d82e0-104">物件的建構，特別是在執行階段，可能會影響應用程式的效能特性。</span><span class="sxs-lookup"><span data-stu-id="d82e0-104">The construction of objects, particularly at run time, can affect the performance characteristics of your application.</span></span>  
  
 <span data-ttu-id="d82e0-105">本主題提供這些區域的效能建議。</span><span class="sxs-lookup"><span data-stu-id="d82e0-105">This topic provides performance recommendations in these areas.</span></span>  
  
## <a name="layout"></a><span data-ttu-id="d82e0-106">配置</span><span class="sxs-lookup"><span data-stu-id="d82e0-106">Layout</span></span>  
 <span data-ttu-id="d82e0-107">詞彙 「 配置傳遞 」 描述的程序的測量和排列的成員<xref:System.Windows.Controls.Panel>-衍生的子系，然後將它們在螢幕上繪製物件的集合。</span><span class="sxs-lookup"><span data-stu-id="d82e0-107">The term "layout pass" describes the process of measuring and arranging the members of a <xref:System.Windows.Controls.Panel>-derived object's collection of children, and then drawing them onscreen.</span></span> <span data-ttu-id="d82e0-108">配置傳遞是數學密集的程序，在集合中的子系數目愈大，需要的計算數目愈大。</span><span class="sxs-lookup"><span data-stu-id="d82e0-108">The layout pass is a mathematically-intensive process—the larger the number of children in the collection, the greater the number of calculations required.</span></span> <span data-ttu-id="d82e0-109">例如，每次子系<xref:System.Windows.UIElement>集合中的物件變更它的位置，就有可能會觸發新的行程由配置系統。</span><span class="sxs-lookup"><span data-stu-id="d82e0-109">For example, each time a child <xref:System.Windows.UIElement> object in the collection changes its position, it has the potential to trigger a new pass by the layout system.</span></span> <span data-ttu-id="d82e0-110">由於物件特性與版面配置行為之間的密切關係，了解可以叫用版面配置系統的事件類型便很重要。</span><span class="sxs-lookup"><span data-stu-id="d82e0-110">Because of the close relationship between object characteristics and layout behavior, it's important to understand the type of events that can invoke the layout system.</span></span> <span data-ttu-id="d82e0-111">藉由盡可能減少版面配置傳遞中任何不必要的引動過程，您的應用程式效能會比較好。</span><span class="sxs-lookup"><span data-stu-id="d82e0-111">Your application will perform better by reducing as much as possible any unnecessary invocations of the layout pass.</span></span>  
  
 <span data-ttu-id="d82e0-112">版面配置系統會為集合中每個子成員完成兩個階段︰測量階段和排列階段。</span><span class="sxs-lookup"><span data-stu-id="d82e0-112">The layout system completes two passes for each child member in a collection: a measure pass, and an arrange pass.</span></span> <span data-ttu-id="d82e0-113">每一個子物件會提供自己的覆寫的實作<xref:System.Windows.UIElement.Measure%2A>和<xref:System.Windows.UIElement.Arrange%2A>方法，才能提供它自己的特定配置行為。</span><span class="sxs-lookup"><span data-stu-id="d82e0-113">Each child object provides its own overridden implementation of the <xref:System.Windows.UIElement.Measure%2A> and <xref:System.Windows.UIElement.Arrange%2A> methods in order to provide its own specific layout behavior.</span></span> <span data-ttu-id="d82e0-114">簡單來說，版面配置是導致項目調整大小、定位並在螢幕上繪製的遞迴系統。</span><span class="sxs-lookup"><span data-stu-id="d82e0-114">At its simplest, layout is a recursive system that leads to an element being sized, positioned, and drawn onscreen.</span></span>  
  
-   <span data-ttu-id="d82e0-115">子系<xref:System.Windows.UIElement>物件開始版面配置處理序的第一個具有測量其核心屬性。</span><span class="sxs-lookup"><span data-stu-id="d82e0-115">A child <xref:System.Windows.UIElement> object begins the layout process by first having its core properties measured.</span></span>  
  
-   <span data-ttu-id="d82e0-116">物件的<xref:System.Windows.FrameworkElement>屬性與相關的大小，例如<xref:System.Windows.FrameworkElement.Width%2A>， <xref:System.Windows.FrameworkElement.Height%2A>，和<xref:System.Windows.FrameworkElement.Margin%2A>，會進行評估。</span><span class="sxs-lookup"><span data-stu-id="d82e0-116">The object's <xref:System.Windows.FrameworkElement> properties that are related to size, such as <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.Margin%2A>, are evaluated.</span></span>  
  
-   <span data-ttu-id="d82e0-117"><xref:System.Windows.Controls.Panel>-套用的特定邏輯，例如<xref:System.Windows.Controls.DockPanel.Dock%2A>屬性<xref:System.Windows.Controls.DockPanel>，或<xref:System.Windows.Controls.StackPanel.Orientation%2A>屬性<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="d82e0-117"><xref:System.Windows.Controls.Panel>-specific logic is applied, such as the <xref:System.Windows.Controls.DockPanel.Dock%2A> property of the <xref:System.Windows.Controls.DockPanel>, or the <xref:System.Windows.Controls.StackPanel.Orientation%2A> property of the <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
-   <span data-ttu-id="d82e0-118">在測量所有子物件之後，會排列 (或定位) 內容。</span><span class="sxs-lookup"><span data-stu-id="d82e0-118">Content is arranged, or positioned, after all child objects have been measured.</span></span>  
  
-   <span data-ttu-id="d82e0-119">子物件的集合會繪製到螢幕。</span><span class="sxs-lookup"><span data-stu-id="d82e0-119">The collection of child objects is drawn to the screen.</span></span>  
  
 <span data-ttu-id="d82e0-120">如果發生任何下列動作，會再次叫用配置傳遞流程︰</span><span class="sxs-lookup"><span data-stu-id="d82e0-120">The layout pass process is invoked again if any of the following actions occur:</span></span>  
  
-   <span data-ttu-id="d82e0-121">子物件新增至集合。</span><span class="sxs-lookup"><span data-stu-id="d82e0-121">A child object is added to the collection.</span></span>  
  
-   <span data-ttu-id="d82e0-122">A<xref:System.Windows.FrameworkElement.LayoutTransform%2A>套用到子物件。</span><span class="sxs-lookup"><span data-stu-id="d82e0-122">A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> is applied to the child object.</span></span>  
  
-   <span data-ttu-id="d82e0-123"><xref:System.Windows.UIElement.UpdateLayout%2A>方法呼叫的子物件。</span><span class="sxs-lookup"><span data-stu-id="d82e0-123">The <xref:System.Windows.UIElement.UpdateLayout%2A> method is called for the child object.</span></span>  
  
-   <span data-ttu-id="d82e0-124">當發生在以中繼資料標示的相依性屬性值的變更會影響測量或排列階段時。</span><span class="sxs-lookup"><span data-stu-id="d82e0-124">When a change occurs to the value of a dependency property that is marked with metadata affecting the measure or arrange passes.</span></span>  
  
### <a name="use-the-most-efficient-panel-where-possible"></a><span data-ttu-id="d82e0-125">請盡可能使用最有效率的面板</span><span class="sxs-lookup"><span data-stu-id="d82e0-125">Use the Most Efficient Panel where Possible</span></span>  
 <span data-ttu-id="d82e0-126">版面配置處理序的複雜度直接根據配置行為<xref:System.Windows.Controls.Panel>-衍生您使用的項目。</span><span class="sxs-lookup"><span data-stu-id="d82e0-126">The complexity of the layout process is directly based on the layout behavior of the <xref:System.Windows.Controls.Panel>-derived elements you use.</span></span> <span data-ttu-id="d82e0-127">例如，<xref:System.Windows.Controls.Grid>或<xref:System.Windows.Controls.StackPanel>控制項提供更多的功能比<xref:System.Windows.Controls.Canvas>控制項。</span><span class="sxs-lookup"><span data-stu-id="d82e0-127">For example, a <xref:System.Windows.Controls.Grid> or <xref:System.Windows.Controls.StackPanel> control provides much more functionality than a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="d82e0-128">這種功能增加的代價是較高的效能成本。</span><span class="sxs-lookup"><span data-stu-id="d82e0-128">The price for this greater increase in functionality is a greater increase in performance costs.</span></span> <span data-ttu-id="d82e0-129">不過，如果您不需要的功能，<xref:System.Windows.Controls.Grid>提供控制項，您應該使用成本較低的替代項目，例如<xref:System.Windows.Controls.Canvas>或自訂的面板。</span><span class="sxs-lookup"><span data-stu-id="d82e0-129">However, if you do not require the functionality that a <xref:System.Windows.Controls.Grid> control provides, you should use the less costly alternatives, such as a <xref:System.Windows.Controls.Canvas> or a custom panel.</span></span>  
  
 <span data-ttu-id="d82e0-130">如需詳細資訊，請參閱[面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d82e0-130">For more information, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span>  
  
### <a name="update-rather-than-replace-a-rendertransform"></a><span data-ttu-id="d82e0-131">更新，而不是取代 RenderTransform</span><span class="sxs-lookup"><span data-stu-id="d82e0-131">Update Rather than Replace a RenderTransform</span></span>  
 <span data-ttu-id="d82e0-132">您可以更新<xref:System.Windows.Media.Transform>而不是取代的值為<xref:System.Windows.UIElement.RenderTransform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d82e0-132">You may be able to update a <xref:System.Windows.Media.Transform> rather than replacing it as the value of a <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span> <span data-ttu-id="d82e0-133">特別是在包含動畫的案例。</span><span class="sxs-lookup"><span data-stu-id="d82e0-133">This is particularly true in scenarios that involve animation.</span></span> <span data-ttu-id="d82e0-134">藉由更新現有<xref:System.Windows.Media.Transform>，避免 起始不必要的版面配置計算。</span><span class="sxs-lookup"><span data-stu-id="d82e0-134">By updating an existing <xref:System.Windows.Media.Transform>, you avoid initiating an unnecessary layout calculation.</span></span>  
  
### <a name="build-your-tree-top-down"></a><span data-ttu-id="d82e0-135">由上而下建置您的樹狀結構</span><span class="sxs-lookup"><span data-stu-id="d82e0-135">Build Your Tree Top-Down</span></span>  
 <span data-ttu-id="d82e0-136">在邏輯樹狀結構節點新增或移除節點時，會對節點之父代及其所有子系引發屬性失效。</span><span class="sxs-lookup"><span data-stu-id="d82e0-136">When a node is added or removed from the logical tree, property invalidations are raised on the node's parent and all its children.</span></span> <span data-ttu-id="d82e0-137">因此，應該一律遵循由上而下的建構模式，以避免在已驗證的節點上發生不必要的失效成本。</span><span class="sxs-lookup"><span data-stu-id="d82e0-137">As a result, a top-down construction pattern should always be followed to avoid the cost of unnecessary invalidations on nodes that have already been validated.</span></span> <span data-ttu-id="d82e0-138">下表顯示在之間建立樹狀結構由上而下和由下往上，其中的樹狀結構是 150 層與單一的執行速度<xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Controls.DockPanel>每個層級。</span><span class="sxs-lookup"><span data-stu-id="d82e0-138">The following table shows the difference in execution speed between building a tree top-down versus bottom-up, where the tree is 150 levels deep with a single <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Controls.DockPanel> at each level.</span></span>  
  
|<span data-ttu-id="d82e0-139">**動作**</span><span class="sxs-lookup"><span data-stu-id="d82e0-139">**Action**</span></span>|<span data-ttu-id="d82e0-140">**樹狀結構建置 (毫秒)**</span><span class="sxs-lookup"><span data-stu-id="d82e0-140">**Tree building (in ms)**</span></span>|<span data-ttu-id="d82e0-141">**轉譯 — 包括樹狀結構建置 (毫秒)**</span><span class="sxs-lookup"><span data-stu-id="d82e0-141">**Render—includes tree building (in ms)**</span></span>|  
|----------------|---------------------------------|-------------------------------------------------|  
|<span data-ttu-id="d82e0-142">由下而上</span><span class="sxs-lookup"><span data-stu-id="d82e0-142">Bottom-up</span></span>|<span data-ttu-id="d82e0-143">366</span><span class="sxs-lookup"><span data-stu-id="d82e0-143">366</span></span>|<span data-ttu-id="d82e0-144">454</span><span class="sxs-lookup"><span data-stu-id="d82e0-144">454</span></span>|  
|<span data-ttu-id="d82e0-145">由上而下</span><span class="sxs-lookup"><span data-stu-id="d82e0-145">Top-down</span></span>|<span data-ttu-id="d82e0-146">11</span><span class="sxs-lookup"><span data-stu-id="d82e0-146">11</span></span>|<span data-ttu-id="d82e0-147">96</span><span class="sxs-lookup"><span data-stu-id="d82e0-147">96</span></span>|  
  
 <span data-ttu-id="d82e0-148">下列程式碼範例示範如何由上而下建立樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="d82e0-148">The following code example demonstrates how to create a tree top down.</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 <span data-ttu-id="d82e0-149">如需有關邏輯樹狀結構的詳細資訊，請參閱 [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="d82e0-149">For more information on the logical tree, see [Trees in WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82e0-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d82e0-150">See Also</span></span>  
 [<span data-ttu-id="d82e0-151">最佳化 WPF 應用程式效能</span><span class="sxs-lookup"><span data-stu-id="d82e0-151">Optimizing WPF Application Performance</span></span>](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [<span data-ttu-id="d82e0-152">應用程式效能規劃</span><span class="sxs-lookup"><span data-stu-id="d82e0-152">Planning for Application Performance</span></span>](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [<span data-ttu-id="d82e0-153">運用硬體</span><span class="sxs-lookup"><span data-stu-id="d82e0-153">Taking Advantage of Hardware</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [<span data-ttu-id="d82e0-154">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="d82e0-154">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [<span data-ttu-id="d82e0-155">物件行為</span><span class="sxs-lookup"><span data-stu-id="d82e0-155">Object Behavior</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [<span data-ttu-id="d82e0-156">應用程式資源</span><span class="sxs-lookup"><span data-stu-id="d82e0-156">Application Resources</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [<span data-ttu-id="d82e0-157">Text</span><span class="sxs-lookup"><span data-stu-id="d82e0-157">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [<span data-ttu-id="d82e0-158">資料繫結</span><span class="sxs-lookup"><span data-stu-id="d82e0-158">Data Binding</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [<span data-ttu-id="d82e0-159">其他效能建議</span><span class="sxs-lookup"><span data-stu-id="d82e0-159">Other Performance Recommendations</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [<span data-ttu-id="d82e0-160">版面配置</span><span class="sxs-lookup"><span data-stu-id="d82e0-160">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)
