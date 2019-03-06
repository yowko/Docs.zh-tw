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
ms.openlocfilehash: d15662958c6967d8bbb157c1af99b4666cebecc2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375047"
---
# <a name="using-drawingvisual-objects"></a><span data-ttu-id="c3561-102">使用 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="c3561-102">Using DrawingVisual Objects</span></span>
<span data-ttu-id="c3561-103">本主題提供使用方式的概觀<xref:System.Windows.Media.DrawingVisual>中的物件[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]視覺圖層。</span><span class="sxs-lookup"><span data-stu-id="c3561-103">This topic provides an overview of how to use <xref:System.Windows.Media.DrawingVisual> objects in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual layer.</span></span>  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a><span data-ttu-id="c3561-104">DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="c3561-104">DrawingVisual Object</span></span>  
 <span data-ttu-id="c3561-105"><xref:System.Windows.Media.DrawingVisual>的輕量型繪圖類別，用來呈現圖形、 影像或文字。</span><span class="sxs-lookup"><span data-stu-id="c3561-105">The <xref:System.Windows.Media.DrawingVisual> is a lightweight drawing class that is used to render shapes, images, or text.</span></span> <span data-ttu-id="c3561-106">此類別之所以被視為輕量型，是因為它不提供版面配置或事件處理，這使它有更好的效能。</span><span class="sxs-lookup"><span data-stu-id="c3561-106">This class is considered lightweight because it does not provide layout or event handling, which improves its performance.</span></span> <span data-ttu-id="c3561-107">基於此原因，繪圖適合背景或美工圖案。</span><span class="sxs-lookup"><span data-stu-id="c3561-107">For this reason, drawings are ideal for backgrounds and clip art.</span></span>  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a><span data-ttu-id="c3561-108">DrawingVisual 主機容器</span><span class="sxs-lookup"><span data-stu-id="c3561-108">DrawingVisual Host Container</span></span>  
 <span data-ttu-id="c3561-109">若要使用<xref:System.Windows.Media.DrawingVisual>物件時，您需要建立主機容器物件。</span><span class="sxs-lookup"><span data-stu-id="c3561-109">In order to use <xref:System.Windows.Media.DrawingVisual> objects, you need to create a host container for the objects.</span></span> <span data-ttu-id="c3561-110">主機容器物件必須衍生自<xref:System.Windows.FrameworkElement>類別，可提供的配置和事件處理支援<xref:System.Windows.Media.DrawingVisual>類別缺少。</span><span class="sxs-lookup"><span data-stu-id="c3561-110">The host container object must derive from the <xref:System.Windows.FrameworkElement> class, which provides the layout and event handling support that the <xref:System.Windows.Media.DrawingVisual> class lacks.</span></span> <span data-ttu-id="c3561-111">主機容器物件不會顯示任何可見的屬性，因為其主要目的是要包含子物件。</span><span class="sxs-lookup"><span data-stu-id="c3561-111">The host container object does not display any visible properties, since its main purpose is to contain child objects.</span></span> <span data-ttu-id="c3561-112">不過，<xref:System.Windows.UIElement.Visibility%2A>在裝載容器的屬性必須設為<xref:System.Windows.Visibility.Visible>; 否則它的所有子元素將會顯示。</span><span class="sxs-lookup"><span data-stu-id="c3561-112">However, the <xref:System.Windows.UIElement.Visibility%2A> property of the host container must be set to <xref:System.Windows.Visibility.Visible>; otherwise, none of its child elements will be visible.</span></span>  
  
 <span data-ttu-id="c3561-113">當您建立主機容器物件的視覺物件時，您需要儲存中的視覺物件參考<xref:System.Windows.Media.VisualCollection>。</span><span class="sxs-lookup"><span data-stu-id="c3561-113">When you create a host container object for visual objects, you need to store the visual object references in a <xref:System.Windows.Media.VisualCollection>.</span></span> <span data-ttu-id="c3561-114">使用<xref:System.Windows.Media.VisualCollection.Add%2A>方法，將視覺物件加入至主機容器。</span><span class="sxs-lookup"><span data-stu-id="c3561-114">Use the <xref:System.Windows.Media.VisualCollection.Add%2A> method to add a visual object to the host container.</span></span> <span data-ttu-id="c3561-115">在下列範例中，建立主機容器物件，並將三個視覺物件會加入其<xref:System.Windows.Media.VisualCollection>。</span><span class="sxs-lookup"><span data-stu-id="c3561-115">In the following example, a host container object is created, and three visual objects are added to its <xref:System.Windows.Media.VisualCollection>.</span></span>  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  <span data-ttu-id="c3561-116">如需先前程式碼範例出處的完整程式碼範例，請參閱[使用 DrawingVisuals 進行點擊測試範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159994)。</span><span class="sxs-lookup"><span data-stu-id="c3561-116">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994).</span></span>  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a><span data-ttu-id="c3561-117">建立 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="c3561-117">Creating DrawingVisual Objects</span></span>  
 <span data-ttu-id="c3561-118">當您建立<xref:System.Windows.Media.DrawingVisual>物件，它沒有任何繪圖內容。</span><span class="sxs-lookup"><span data-stu-id="c3561-118">When you create a <xref:System.Windows.Media.DrawingVisual> object, it has no drawing content.</span></span> <span data-ttu-id="c3561-119">您可以藉由擷取的物件加入文字、 圖形或影像內容<xref:System.Windows.Media.DrawingContext>和繪製到它。</span><span class="sxs-lookup"><span data-stu-id="c3561-119">You can add text, graphics, or image content by retrieving the object's <xref:System.Windows.Media.DrawingContext> and drawing into it.</span></span> <span data-ttu-id="c3561-120">A<xref:System.Windows.Media.DrawingContext>藉由呼叫會傳回<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A>方法<xref:System.Windows.Media.DrawingVisual>物件。</span><span class="sxs-lookup"><span data-stu-id="c3561-120">A <xref:System.Windows.Media.DrawingContext> is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span>  
  
 <span data-ttu-id="c3561-121">若要繪製到矩形<xref:System.Windows.Media.DrawingContext>，使用<xref:System.Windows.Media.DrawingContext.DrawRectangle%2A>方法<xref:System.Windows.Media.DrawingContext>物件。</span><span class="sxs-lookup"><span data-stu-id="c3561-121">To draw a rectangle into the <xref:System.Windows.Media.DrawingContext>, use the <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> method of the <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="c3561-122">繪製其他類型的內容有類似的方法。</span><span class="sxs-lookup"><span data-stu-id="c3561-122">Similar methods exist for drawing other types of content.</span></span> <span data-ttu-id="c3561-123">當您完成繪圖內容載入<xref:System.Windows.Media.DrawingContext>，呼叫<xref:System.Windows.Media.DrawingContext.Close%2A>方法以關閉<xref:System.Windows.Media.DrawingContext>並保存內容。</span><span class="sxs-lookup"><span data-stu-id="c3561-123">When you are finished drawing content into the <xref:System.Windows.Media.DrawingContext>, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the <xref:System.Windows.Media.DrawingContext> and persist the content.</span></span>  
  
 <span data-ttu-id="c3561-124">在下列範例中，<xref:System.Windows.Media.DrawingVisual>建立物件，並繪製矩形到其<xref:System.Windows.Media.DrawingContext>。</span><span class="sxs-lookup"><span data-stu-id="c3561-124">In the following example, a <xref:System.Windows.Media.DrawingVisual> object is created, and a rectangle is drawn into its <xref:System.Windows.Media.DrawingContext>.</span></span>  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a><span data-ttu-id="c3561-125">針對 FrameworkElement 成員建立覆寫</span><span class="sxs-lookup"><span data-stu-id="c3561-125">Creating Overrides for FrameworkElement Members</span></span>  
 <span data-ttu-id="c3561-126">主機容器物件負責管理其視覺物件的集合。</span><span class="sxs-lookup"><span data-stu-id="c3561-126">The host container object is responsible for managing its collection of visual objects.</span></span> <span data-ttu-id="c3561-127">這需要主機容器實作成員覆寫衍生的<xref:System.Windows.FrameworkElement>類別。</span><span class="sxs-lookup"><span data-stu-id="c3561-127">This requires that the host container implement member overrides for the derived <xref:System.Windows.FrameworkElement> class.</span></span>  
  
 <span data-ttu-id="c3561-128">下列清單說明您必須覆寫的兩個成員︰</span><span class="sxs-lookup"><span data-stu-id="c3561-128">The following list describes the two members you must override:</span></span>  
  
-   <span data-ttu-id="c3561-129"><xref:System.Windows.FrameworkElement.GetVisualChild%2A>：傳回指定之索引處的子系集合中的項目子系。</span><span class="sxs-lookup"><span data-stu-id="c3561-129"><xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Returns a child at the specified index from the collection of child elements.</span></span>  
  
-   <span data-ttu-id="c3561-130"><xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>：取得這個項目內的視覺化子項目數。</span><span class="sxs-lookup"><span data-stu-id="c3561-130"><xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Gets the number of visual child elements within this element.</span></span>  
  
 <span data-ttu-id="c3561-131">在下列範例中，覆寫這兩個<xref:System.Windows.FrameworkElement>成員實作。</span><span class="sxs-lookup"><span data-stu-id="c3561-131">In the following example, overrides for the two <xref:System.Windows.FrameworkElement> members are implemented.</span></span>  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a><span data-ttu-id="c3561-132">提供點擊測試支援</span><span class="sxs-lookup"><span data-stu-id="c3561-132">Providing Hit Testing Support</span></span>  
 <span data-ttu-id="c3561-133">主機容器物件可以提供事件處理，即使它不會顯示任何可見的屬性，不過，其<xref:System.Windows.UIElement.Visibility%2A>屬性必須設為<xref:System.Windows.Visibility.Visible>。</span><span class="sxs-lookup"><span data-stu-id="c3561-133">The host container object can provide event handling even if it does not display any visible properties—however, its <xref:System.Windows.UIElement.Visibility%2A> property must be set to <xref:System.Windows.Visibility.Visible>.</span></span> <span data-ttu-id="c3561-134">這可讓您針對可捕捉滑鼠事件 (例如放開滑鼠左鍵) 的主機容器建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c3561-134">This allows you to create an event handling routine for the host container that can trap mouse events, such as the release of the left mouse button.</span></span> <span data-ttu-id="c3561-135">事件處理常式可以實作點擊測試，藉由叫用<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c3561-135">The event handling routine can then implement hit testing by invoking the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="c3561-136">方法的<xref:System.Windows.Media.HitTestResultCallback>參數會參考使用者定義的程序，您可以使用它來判斷產生的點擊測試的動作。</span><span class="sxs-lookup"><span data-stu-id="c3561-136">The method's <xref:System.Windows.Media.HitTestResultCallback> parameter refers to a user-defined procedure that you can use to determine the resulting action of a hit test.</span></span>  
  
 <span data-ttu-id="c3561-137">在下列範例中，會針對主機容器物件和其子系實作點擊測試支援。</span><span class="sxs-lookup"><span data-stu-id="c3561-137">In the following example, hit testing support is implemented for the host container object and its children.</span></span>  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="c3561-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3561-138">See also</span></span>
- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [<span data-ttu-id="c3561-139">WPF 圖形轉譯概觀</span><span class="sxs-lookup"><span data-stu-id="c3561-139">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="c3561-140">視覺分層中的點擊測試</span><span class="sxs-lookup"><span data-stu-id="c3561-140">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
