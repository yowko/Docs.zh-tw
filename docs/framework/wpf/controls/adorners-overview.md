---
title: "裝飾項概觀"
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
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 47b43b1b9848f91e77448d41609d8be5d60ecda5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="adorners-overview"></a><span data-ttu-id="e1ea4-102">裝飾項概觀</span><span class="sxs-lookup"><span data-stu-id="e1ea4-102">Adorners Overview</span></span>
<span data-ttu-id="e1ea4-103">裝飾項是一種特殊型別的<xref:System.Windows.FrameworkElement>，用來提供視覺提示給使用者。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="e1ea4-104">除了其他用法，裝飾項還可用來將功能控點加入項目，或提供控制項的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a><span data-ttu-id="e1ea4-105">關於裝飾項</span><span class="sxs-lookup"><span data-stu-id="e1ea4-105">About Adorners</span></span>  
 <span data-ttu-id="e1ea4-106"><xref:System.Windows.Documents.Adorner>是 custom<xref:System.Windows.FrameworkElement>繫結至<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="e1ea4-107">裝飾項會呈現在<xref:System.Windows.Documents.AdornerLayer>，這是永遠是裝飾項目或裝飾項目集合的最上方的呈現表面。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="e1ea4-108">轉譯的裝飾項無關的轉譯<xref:System.Windows.UIElement>裝飾項繫結至。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="e1ea4-109">裝飾項的位置通常會相對於它繫結到的項目，並使用標準 2D 座標，原點位於裝飾項目的左上角。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2-D coordinate origin located at the upper-left of the adorned element.</span></span>  
  
 <span data-ttu-id="e1ea4-110">裝飾項的常見應用包括︰</span><span class="sxs-lookup"><span data-stu-id="e1ea4-110">Common applications for adorners include:</span></span>  
  
-   <span data-ttu-id="e1ea4-111">新增功能的控制代碼<xref:System.Windows.UIElement>可讓使用者操作以某種方式 （重新調整大小、 旋轉、 重新定位等等） 的項目。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>  
  
-   <span data-ttu-id="e1ea4-112">提供視覺化回應以表示各種狀態，或回應各種事件。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>  
  
-   <span data-ttu-id="e1ea4-113">上重疊 visual 裝飾<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="e1ea4-114">以視覺化方式加上遮罩或覆寫的部分或全部<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="e1ea4-115"> 提供基本的架構以便裝飾視覺項目。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-115"> provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="e1ea4-116">下表列出在裝飾物件時所使用的主要類型，及其用途。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="e1ea4-117">以下是幾個使用方式的範例。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-117">Several usage examples follow.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="e1ea4-118">抽象基底類別，所有具體裝飾項實作都繼承自該類別。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|  
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="e1ea4-119">代表一個或多個裝飾項目的裝飾項轉譯層的類別。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|  
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="e1ea4-120">可讓裝飾項層與項目集合相關聯的類別。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="e1ea4-121">實作自訂裝飾項</span><span class="sxs-lookup"><span data-stu-id="e1ea4-121">Implementing a Custom Adorner</span></span>  
 <span data-ttu-id="e1ea4-122">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]　提供的裝飾項架構主要是為了支援建立自訂裝飾項。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="e1ea4-123">藉由實作繼承自抽象類別建立的自訂裝飾項<xref:System.Windows.Documents.Adorner>類別。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1ea4-124">父代<xref:System.Windows.Documents.Adorner>是<xref:System.Windows.Documents.AdornerLayer>呈現<xref:System.Windows.Documents.Adorner>不所裝飾的項目。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>  
  
 <span data-ttu-id="e1ea4-125">下列範例顯示一個實作簡單裝飾項的類別。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="e1ea4-126">範例裝飾項只 adorns 角落<xref:System.Windows.UIElement>使用圓形。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 <span data-ttu-id="e1ea4-127">下圖顯示套用至 SimpleCircleAdorner <xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="e1ea4-128">![裝飾項範例：已裝飾的文字方塊](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span><span class="sxs-lookup"><span data-stu-id="e1ea4-128">![Adorners Example: An adorned TextBox](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span></span>  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="e1ea4-129">裝飾項的轉譯行為</span><span class="sxs-lookup"><span data-stu-id="e1ea4-129">Rendering Behavior for Adorners</span></span>  
 <span data-ttu-id="e1ea4-130">請務必注意，裝飾項並不包括任何繼承的轉譯行為。裝飾項實作者必須負責確定裝飾項轉譯器。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="e1ea4-131">實作轉譯行為的常見方式是覆寫<xref:System.Windows.UIElement.OnRender%2A>方法並使用一或多個<xref:System.Windows.Media.DrawingContext>物件來呈現裝飾項的視覺效果視 （如上述範例所示）。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1ea4-132">放在裝飾項圖層中的任何項目會轉譯在您已設定的其餘任何樣式之上。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="e1ea4-133">換句話說，裝飾項永遠是以視覺化方式在最上面，而且無法使用疊置順序覆寫。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a><span data-ttu-id="e1ea4-134">事件和點擊測試</span><span class="sxs-lookup"><span data-stu-id="e1ea4-134">Events and Hit Testing</span></span>  
 <span data-ttu-id="e1ea4-135">裝飾項接收就像任何其他的輸入的事件<xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="e1ea4-136">裝飾項裝飾項一律具有較高疊置順序比它 adorns 的項目，因為接收輸入的事件 (例如<xref:System.Windows.UIElement.Drop>或<xref:System.Windows.UIElement.MouseMove>)，可能為了提供給基礎裝飾項目。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="e1ea4-137">裝飾項可以接聽特定的輸入事件，並藉由重新引發事件將它們傳送到基礎的被裝飾項目。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>  
  
 <span data-ttu-id="e1ea4-138">若要啟用的裝飾項下的項目傳遞點擊測試，設定的點擊的測試<xref:System.Windows.UIElement.IsHitTestVisible%2A>屬性**false**上裝飾項。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="e1ea4-139">如需點擊測試的詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="e1ea4-139">For more information about hit testing, see</span></span>  
  
 <span data-ttu-id="e1ea4-140">[視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-140">[Hit Testing in the Visual Layer](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a><span data-ttu-id="e1ea4-141">裝飾單一的 UIElement</span><span class="sxs-lookup"><span data-stu-id="e1ea4-141">Adorning a Single UIElement</span></span>  
 <span data-ttu-id="e1ea4-142">若要將裝飾項繫結至特定<xref:System.Windows.UIElement>，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e1ea4-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e1ea4-143">呼叫靜態方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>取得<xref:System.Windows.Documents.AdornerLayer>物件<xref:System.Windows.UIElement>至會裝飾。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="e1ea4-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>開始於指定的視覺化樹狀結構會進入<xref:System.Windows.UIElement>，並傳回它發現的第一個裝飾項層。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="e1ea4-145">(如果找不到任何裝飾項圖層，方法會傳回 null。)</span><span class="sxs-lookup"><span data-stu-id="e1ea4-145">(If no adorner layers are found, the method returns null.)</span></span>  
  
2.  <span data-ttu-id="e1ea4-146">呼叫<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法，以將裝飾項繫結至目標<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>  
  
 <span data-ttu-id="e1ea4-147">下列範例會將繫結 （如上所示） 以 SimpleCircleAdorner<xref:System.Windows.Controls.TextBox>名為*myTextBox*。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="e1ea4-148">使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="e1ea4-149">裝飾 Panel 的子系</span><span class="sxs-lookup"><span data-stu-id="e1ea4-149">Adorning the Children of a Panel</span></span>  
 <span data-ttu-id="e1ea4-150">若要繫結的項目子系的裝飾項<xref:System.Windows.Controls.Panel>，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e1ea4-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e1ea4-151">呼叫`static`方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>找不到裝飾項層，其子系要被裝飾項目。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="e1ea4-152">列舉的子系的父項目並呼叫<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法，以將裝飾項繫結至每個子項目。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="e1ea4-153">下列範例會將繫結 （如上所示） 的項目子系 SimpleCircleAdorner<xref:System.Windows.Controls.StackPanel>名為*myStackPanel*。</span><span class="sxs-lookup"><span data-stu-id="e1ea4-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a><span data-ttu-id="e1ea4-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="e1ea4-154">See Also</span></span>  
 <xref:System.Windows.Media.AdornerHitTestResult>  
 [<span data-ttu-id="e1ea4-155">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="e1ea4-155">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="e1ea4-156">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="e1ea4-156">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="e1ea4-157">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="e1ea4-157">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="e1ea4-158">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="e1ea4-158">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)
