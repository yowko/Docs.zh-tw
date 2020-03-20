---
title: 使用 DrawingVisual 物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
ms.openlocfilehash: 9d67fbc0d9716c9df3935232c6c7e579b50d55bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148318"
---
# <a name="using-drawingvisual-objects"></a><span data-ttu-id="6f4f4-102">使用 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="6f4f4-102">Using DrawingVisual Objects</span></span>
<span data-ttu-id="6f4f4-103">本主題概述了如何在<xref:System.Windows.Media.DrawingVisual>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]視覺化圖層中使用物件。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-103">This topic provides an overview of how to use <xref:System.Windows.Media.DrawingVisual> objects in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual layer.</span></span>  
  
<a name="drawingvisual_object"></a>
## <a name="drawingvisual-object"></a><span data-ttu-id="6f4f4-104">DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="6f4f4-104">DrawingVisual Object</span></span>  
 <span data-ttu-id="6f4f4-105">是<xref:System.Windows.Media.DrawingVisual>用於渲染形狀、圖像或文本的羽量級繪圖類。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-105">The <xref:System.Windows.Media.DrawingVisual> is a lightweight drawing class that is used to render shapes, images, or text.</span></span> <span data-ttu-id="6f4f4-106">此類別之所以被視為輕量型，是因為它不提供版面配置或事件處理，這使它有更好的效能。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-106">This class is considered lightweight because it does not provide layout or event handling, which improves its performance.</span></span> <span data-ttu-id="6f4f4-107">基於此原因，它適合用於背景或美工圖案繪圖。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-107">For this reason, drawings are ideal for backgrounds and clip art.</span></span>  
  
<a name="drawingvisual_host_container"></a>
## <a name="drawingvisual-host-container"></a><span data-ttu-id="6f4f4-108">DrawingVisual 主機容器</span><span class="sxs-lookup"><span data-stu-id="6f4f4-108">DrawingVisual Host Container</span></span>  
 <span data-ttu-id="6f4f4-109">為了使用<xref:System.Windows.Media.DrawingVisual>物件，您需要為物件創建一個宿主容器。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-109">In order to use <xref:System.Windows.Media.DrawingVisual> objects, you need to create a host container for the objects.</span></span> <span data-ttu-id="6f4f4-110">主機容器物件必須派生自<xref:System.Windows.FrameworkElement>類，該類提供類缺少的<xref:System.Windows.Media.DrawingVisual>佈局和事件處理支援。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-110">The host container object must derive from the <xref:System.Windows.FrameworkElement> class, which provides the layout and event handling support that the <xref:System.Windows.Media.DrawingVisual> class lacks.</span></span> <span data-ttu-id="6f4f4-111">主機容器物件不會顯示任何可見的屬性，因為其主要目的是要包含子物件。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-111">The host container object does not display any visible properties, since its main purpose is to contain child objects.</span></span> <span data-ttu-id="6f4f4-112">但是，<xref:System.Windows.UIElement.Visibility%2A>主機容器的屬性必須設置為<xref:System.Windows.Visibility.Visible>;否則，其子項目都不會可見。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-112">However, the <xref:System.Windows.UIElement.Visibility%2A> property of the host container must be set to <xref:System.Windows.Visibility.Visible>; otherwise, none of its child elements will be visible.</span></span>  
  
 <span data-ttu-id="6f4f4-113">為可視物件創建宿主容器物件時，需要在 中<xref:System.Windows.Media.VisualCollection>存儲可視物件引用。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-113">When you create a host container object for visual objects, you need to store the visual object references in a <xref:System.Windows.Media.VisualCollection>.</span></span> <span data-ttu-id="6f4f4-114">使用<xref:System.Windows.Media.VisualCollection.Add%2A>方法向宿主容器添加可視物件。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-114">Use the <xref:System.Windows.Media.VisualCollection.Add%2A> method to add a visual object to the host container.</span></span> <span data-ttu-id="6f4f4-115">在下面的示例中，將創建一個宿主容器物件，並將三個可視物件添加到其<xref:System.Windows.Media.VisualCollection>。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-115">In the following example, a host container object is created, and three visual objects are added to its <xref:System.Windows.Media.VisualCollection>.</span></span>  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> <span data-ttu-id="6f4f4-116">如需先前程式碼範例出處的完整程式碼範例，請參閱[使用 DrawingVisuals 進行點擊測試範例 (英文)](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-116">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).</span></span>  
  
<a name="creating_drawingvisual_objects"></a>
## <a name="creating-drawingvisual-objects"></a><span data-ttu-id="6f4f4-117">建立 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="6f4f4-117">Creating DrawingVisual Objects</span></span>  
 <span data-ttu-id="6f4f4-118">創建物件時<xref:System.Windows.Media.DrawingVisual>，它沒有繪圖內容。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-118">When you create a <xref:System.Windows.Media.DrawingVisual> object, it has no drawing content.</span></span> <span data-ttu-id="6f4f4-119">您可以通過檢索物件<xref:System.Windows.Media.DrawingContext>並將其繪製到其中來添加文本、圖形或圖像內容。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-119">You can add text, graphics, or image content by retrieving the object's <xref:System.Windows.Media.DrawingContext> and drawing into it.</span></span> <span data-ttu-id="6f4f4-120">通過<xref:System.Windows.Media.DrawingContext>調用<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A><xref:System.Windows.Media.DrawingVisual>物件的方法返回 。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-120">A <xref:System.Windows.Media.DrawingContext> is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span>  
  
 <span data-ttu-id="6f4f4-121">要將矩形繪製到<xref:System.Windows.Media.DrawingContext>中，請使用<xref:System.Windows.Media.DrawingContext.DrawRectangle%2A><xref:System.Windows.Media.DrawingContext>物件的方法。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-121">To draw a rectangle into the <xref:System.Windows.Media.DrawingContext>, use the <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> method of the <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="6f4f4-122">繪製其他類型的內容有類似的方法。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-122">Similar methods exist for drawing other types of content.</span></span> <span data-ttu-id="6f4f4-123">將內容繪製完到 中<xref:System.Windows.Media.DrawingContext>，調用<xref:System.Windows.Media.DrawingContext.Close%2A>方法以關閉<xref:System.Windows.Media.DrawingContext>並保留內容。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-123">When you are finished drawing content into the <xref:System.Windows.Media.DrawingContext>, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the <xref:System.Windows.Media.DrawingContext> and persist the content.</span></span>  
  
 <span data-ttu-id="6f4f4-124">在下面的示例中，將創建<xref:System.Windows.Media.DrawingVisual>一個物件，並將一個矩形繪製到其<xref:System.Windows.Media.DrawingContext>中。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-124">In the following example, a <xref:System.Windows.Media.DrawingVisual> object is created, and a rectangle is drawn into its <xref:System.Windows.Media.DrawingContext>.</span></span>  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>
## <a name="creating-overrides-for-frameworkelement-members"></a><span data-ttu-id="6f4f4-125">針對 FrameworkElement 成員建立覆寫</span><span class="sxs-lookup"><span data-stu-id="6f4f4-125">Creating Overrides for FrameworkElement Members</span></span>  
 <span data-ttu-id="6f4f4-126">主機容器物件負責管理其視覺物件的集合。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-126">The host container object is responsible for managing its collection of visual objects.</span></span> <span data-ttu-id="6f4f4-127">這要求主機容器實現成員重寫派生<xref:System.Windows.FrameworkElement>類。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-127">This requires that the host container implement member overrides for the derived <xref:System.Windows.FrameworkElement> class.</span></span>  
  
 <span data-ttu-id="6f4f4-128">下列清單說明您必須覆寫的兩個成員︰</span><span class="sxs-lookup"><span data-stu-id="6f4f4-128">The following list describes the two members you must override:</span></span>  
  
- <span data-ttu-id="6f4f4-129"><xref:System.Windows.FrameworkElement.GetVisualChild%2A>：從子項目集合中返回指定索引處的子項。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-129"><xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Returns a child at the specified index from the collection of child elements.</span></span>  
  
- <span data-ttu-id="6f4f4-130"><xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>：獲取此元素中的可視子項目的數量。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-130"><xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Gets the number of visual child elements within this element.</span></span>  
  
 <span data-ttu-id="6f4f4-131">在下面的示例中，將實現兩<xref:System.Windows.FrameworkElement>個成員的重寫。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-131">In the following example, overrides for the two <xref:System.Windows.FrameworkElement> members are implemented.</span></span>  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>
## <a name="providing-hit-testing-support"></a><span data-ttu-id="6f4f4-132">提供點擊測試支援</span><span class="sxs-lookup"><span data-stu-id="6f4f4-132">Providing Hit Testing Support</span></span>  
 <span data-ttu-id="6f4f4-133">主機容器物件可以提供事件處理，即使它不顯示任何可見屬性 ， 但是，其<xref:System.Windows.UIElement.Visibility%2A>屬性必須設置為<xref:System.Windows.Visibility.Visible>。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-133">The host container object can provide event handling even if it does not display any visible properties—however, its <xref:System.Windows.UIElement.Visibility%2A> property must be set to <xref:System.Windows.Visibility.Visible>.</span></span> <span data-ttu-id="6f4f4-134">這可讓您針對可捕捉滑鼠事件 (例如放開滑鼠左鍵) 的主機容器建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-134">This allows you to create an event handling routine for the host container that can trap mouse events, such as the release of the left mouse button.</span></span> <span data-ttu-id="6f4f4-135">然後，事件處理常式可以通過調用<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法實現點擊測試。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-135">The event handling routine can then implement hit testing by invoking the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="6f4f4-136">方法的<xref:System.Windows.Media.HitTestResultCallback>參數是指使用者定義的過程，可用於確定點擊測試的結果操作。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-136">The method's <xref:System.Windows.Media.HitTestResultCallback> parameter refers to a user-defined procedure that you can use to determine the resulting action of a hit test.</span></span>  
  
 <span data-ttu-id="6f4f4-137">在下列範例中，會針對主機容器物件和其子系實作點擊測試支援。</span><span class="sxs-lookup"><span data-stu-id="6f4f4-137">In the following example, hit testing support is implemented for the host container object and its children.</span></span>  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="6f4f4-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f4f4-138">See also</span></span>

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [<span data-ttu-id="6f4f4-139">WPF 圖形轉譯概觀</span><span class="sxs-lookup"><span data-stu-id="6f4f4-139">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="6f4f4-140">視覺分層中的點擊測試</span><span class="sxs-lookup"><span data-stu-id="6f4f4-140">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
