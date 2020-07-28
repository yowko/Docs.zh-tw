---
title: 裝飾項概觀
description: 瞭解 Windows Presentation Foundation 的裝飾項，這是一種特殊類型的 FrameworkElement，可提供提示給使用者，例如元素的功能控制碼。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 43d4af9f86c6ae72a61f86d1ca19405c2dcc6cc8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167733"
---
# <a name="adorners-overview"></a><span data-ttu-id="230e2-103">裝飾項概觀</span><span class="sxs-lookup"><span data-stu-id="230e2-103">Adorners Overview</span></span>

<span data-ttu-id="230e2-104">「裝飾項」是一種特殊類型的 <xref:System.Windows.FrameworkElement> ，可用來為使用者提供視覺提示。</span><span class="sxs-lookup"><span data-stu-id="230e2-104">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="230e2-105">除了其他用法，裝飾項還可用來將功能控點加入項目，或提供控制項的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="230e2-105">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>

## <a name="about-adorners"></a><span data-ttu-id="230e2-106">關於裝飾項</span><span class="sxs-lookup"><span data-stu-id="230e2-106">About Adorners</span></span>

<span data-ttu-id="230e2-107">是系結 <xref:System.Windows.Documents.Adorner> 至的自訂 <xref:System.Windows.FrameworkElement> <xref:System.Windows.UIElement> 。</span><span class="sxs-lookup"><span data-stu-id="230e2-107">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="230e2-108">裝飾項會在中轉譯 <xref:System.Windows.Documents.AdornerLayer> ，這是一種呈現介面，一律在裝飾專案的頂端，或是裝飾專案的集合。</span><span class="sxs-lookup"><span data-stu-id="230e2-108">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="230e2-109">轉譯裝飾項與轉譯裝飾項所系結的呈現無關 <xref:System.Windows.UIElement> 。</span><span class="sxs-lookup"><span data-stu-id="230e2-109">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="230e2-110">裝飾項的位置通常是相對於其所系結的專案，使用位於裝飾元素左上方的標準2D 座標原點。</span><span class="sxs-lookup"><span data-stu-id="230e2-110">An adorner is typically positioned relative to the element to which it is bound, using the standard 2D coordinate origin located at the upper-left of the adorned element.</span></span>

<span data-ttu-id="230e2-111">裝飾項的常見應用包括︰</span><span class="sxs-lookup"><span data-stu-id="230e2-111">Common applications for adorners include:</span></span>

- <span data-ttu-id="230e2-112">將功能控制碼加入至 <xref:System.Windows.UIElement> ，讓使用者能夠以某種方式操作專案（調整大小、旋轉、重新置放等等）。</span><span class="sxs-lookup"><span data-stu-id="230e2-112">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>
- <span data-ttu-id="230e2-113">提供視覺化回應以表示各種狀態，或回應各種事件。</span><span class="sxs-lookup"><span data-stu-id="230e2-113">Provide visual feedback to indicate various states, or in response to various events.</span></span>
- <span data-ttu-id="230e2-114">重迭上的視覺效果裝飾 <xref:System.Windows.UIElement> 。</span><span class="sxs-lookup"><span data-stu-id="230e2-114">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>
- <span data-ttu-id="230e2-115">以視覺化方式遮罩或覆寫部分或全部 <xref:System.Windows.UIElement> 。</span><span class="sxs-lookup"><span data-stu-id="230e2-115">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="230e2-116">提供基本的架構以便裝飾視覺項目。</span><span class="sxs-lookup"><span data-stu-id="230e2-116">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="230e2-117">下表列出在裝飾物件時所使用的主要類型，及其用途。</span><span class="sxs-lookup"><span data-stu-id="230e2-117">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="230e2-118">以下是幾個使用範例：</span><span class="sxs-lookup"><span data-stu-id="230e2-118">Several usage examples follow:</span></span>

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="230e2-119">抽象基底類別，所有具體裝飾項實作都繼承自該類別。</span><span class="sxs-lookup"><span data-stu-id="230e2-119">An abstract base class from which all concrete adorner implementations inherit.</span></span>|
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="230e2-120">代表一個或多個裝飾項目的裝飾項轉譯層的類別。</span><span class="sxs-lookup"><span data-stu-id="230e2-120">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="230e2-121">可讓裝飾項層與項目集合相關聯的類別。</span><span class="sxs-lookup"><span data-stu-id="230e2-121">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|

## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="230e2-122">實作自訂裝飾項</span><span class="sxs-lookup"><span data-stu-id="230e2-122">Implementing a Custom Adorner</span></span>

<span data-ttu-id="230e2-123">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]　提供的裝飾項架構主要是為了支援建立自訂裝飾項。</span><span class="sxs-lookup"><span data-stu-id="230e2-123">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="230e2-124">自訂裝飾項是藉由執行繼承自抽象類別的類別來建立 <xref:System.Windows.Documents.Adorner> 。</span><span class="sxs-lookup"><span data-stu-id="230e2-124">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>

> [!NOTE]
> <span data-ttu-id="230e2-125">的父系 <xref:System.Windows.Documents.Adorner> 是呈現的，而不是所裝飾的專案 <xref:System.Windows.Documents.AdornerLayer> <xref:System.Windows.Documents.Adorner> 。</span><span class="sxs-lookup"><span data-stu-id="230e2-125">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>

<span data-ttu-id="230e2-126">下列範例顯示一個實作簡單裝飾項的類別。</span><span class="sxs-lookup"><span data-stu-id="230e2-126">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="230e2-127">範例裝飾項只會裝飾具有圓圈的圓角 <xref:System.Windows.UIElement> 。</span><span class="sxs-lookup"><span data-stu-id="230e2-127">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
<span data-ttu-id="230e2-128">下圖顯示適用于的 SimpleCircleAdorner <xref:System.Windows.Controls.TextBox> ：</span><span class="sxs-lookup"><span data-stu-id="230e2-128">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>:</span></span>

![顯示已裝飾文字方塊的螢幕擷取畫面。](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="230e2-130">裝飾項的轉譯行為</span><span class="sxs-lookup"><span data-stu-id="230e2-130">Rendering Behavior for Adorners</span></span>

<span data-ttu-id="230e2-131">請務必注意，裝飾項並不包括任何繼承的轉譯行為。裝飾項實作者必須負責確定裝飾項轉譯器。</span><span class="sxs-lookup"><span data-stu-id="230e2-131">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span> <span data-ttu-id="230e2-132">執行轉譯行為的常見方式是覆寫 <xref:System.Windows.UIElement.OnRender%2A> 方法，並視需要使用一或多個 <xref:System.Windows.Media.DrawingContext> 物件來呈現裝飾項的視覺效果（如上述範例所示）。</span><span class="sxs-lookup"><span data-stu-id="230e2-132">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>

> [!NOTE]
> <span data-ttu-id="230e2-133">放在裝飾項圖層中的任何項目會轉譯在您已設定的其餘任何樣式之上。</span><span class="sxs-lookup"><span data-stu-id="230e2-133">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="230e2-134">換句話說，裝飾項永遠是以視覺化方式在最上面，而且無法使用疊置順序覆寫。</span><span class="sxs-lookup"><span data-stu-id="230e2-134">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>

## <a name="events-and-hit-testing"></a><span data-ttu-id="230e2-135">事件和點擊測試</span><span class="sxs-lookup"><span data-stu-id="230e2-135">Events and Hit Testing</span></span>

<span data-ttu-id="230e2-136">裝飾項會接收輸入事件，就像任何其他一樣 <xref:System.Windows.FrameworkElement> 。</span><span class="sxs-lookup"><span data-stu-id="230e2-136">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="230e2-137">由於裝飾項的迭置順序一律會高於它所裝飾的元素，因此，裝飾項 <xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.MouseMove> 會接收可能適用于基礎裝飾元素的輸入事件（例如或）。</span><span class="sxs-lookup"><span data-stu-id="230e2-137">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="230e2-138">裝飾項可以接聽特定的輸入事件，並藉由重新引發事件將它們傳送到基礎的被裝飾項目。</span><span class="sxs-lookup"><span data-stu-id="230e2-138">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>

<span data-ttu-id="230e2-139">若要在裝飾項下啟用專案的傳遞點擊測試，請將 <xref:System.Windows.UIElement.IsHitTestVisible%2A> 裝飾項上的點擊測試屬性設定為**false** 。</span><span class="sxs-lookup"><span data-stu-id="230e2-139">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="230e2-140">如需點擊測試的詳細資訊，請參閱[視覺分層中的點擊測試](../graphics-multimedia/hit-testing-in-the-visual-layer.md)。</span><span class="sxs-lookup"><span data-stu-id="230e2-140">For more information about hit testing, see [Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>

## <a name="adorning-a-single-uielement"></a><span data-ttu-id="230e2-141">裝飾單一的 UIElement</span><span class="sxs-lookup"><span data-stu-id="230e2-141">Adorning a Single UIElement</span></span>

<span data-ttu-id="230e2-142">若要將裝飾項系結至特定 <xref:System.Windows.UIElement> ，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="230e2-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>

1. <span data-ttu-id="230e2-143">呼叫靜態方法 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> ，取得 <xref:System.Windows.Documents.AdornerLayer> <xref:System.Windows.UIElement> 要裝飾之的物件。</span><span class="sxs-lookup"><span data-stu-id="230e2-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="230e2-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>從指定的開始逐步解說視覺化樹狀結構， <xref:System.Windows.UIElement> 並傳回它找到的第一個裝飾項層。</span><span class="sxs-lookup"><span data-stu-id="230e2-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="230e2-145">(如果找不到任何裝飾項圖層，方法會傳回 null。)</span><span class="sxs-lookup"><span data-stu-id="230e2-145">(If no adorner layers are found, the method returns null.)</span></span>

2. <span data-ttu-id="230e2-146">呼叫 <xref:System.Windows.Documents.AdornerLayer.Add%2A> 方法，將裝飾項系結至目標 <xref:System.Windows.UIElement> 。</span><span class="sxs-lookup"><span data-stu-id="230e2-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>

 <span data-ttu-id="230e2-147">下列範例會將 SimpleCircleAdorner （如上所示）系結至 <xref:System.Windows.Controls.TextBox> 名為的*myTextBox*：</span><span class="sxs-lookup"><span data-stu-id="230e2-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*:</span></span>

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> <span data-ttu-id="230e2-148">使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。</span><span class="sxs-lookup"><span data-stu-id="230e2-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>

## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="230e2-149">裝飾 Panel 的子系</span><span class="sxs-lookup"><span data-stu-id="230e2-149">Adorning the Children of a Panel</span></span>

<span data-ttu-id="230e2-150">若要將裝飾項系結至的子系 <xref:System.Windows.Controls.Panel> ，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="230e2-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>

1. <span data-ttu-id="230e2-151">呼叫 `static` 方法 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> ，尋找要裝飾其子系之元素的裝飾項層。</span><span class="sxs-lookup"><span data-stu-id="230e2-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>

2. <span data-ttu-id="230e2-152">列舉父元素的子系，並呼叫方法， <xref:System.Windows.Documents.AdornerLayer.Add%2A> 將裝飾項系結至每個子專案。</span><span class="sxs-lookup"><span data-stu-id="230e2-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>

<span data-ttu-id="230e2-153">下列範例會將 SimpleCircleAdorner （如上所示）系結至 <xref:System.Windows.Controls.StackPanel> 名為*myStackPanel*的子系：</span><span class="sxs-lookup"><span data-stu-id="230e2-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*:</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a><span data-ttu-id="230e2-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="230e2-154">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="230e2-155">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="230e2-155">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="230e2-156">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="230e2-156">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="230e2-157">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="230e2-157">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="230e2-158">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="230e2-158">How-to Topics</span></span>](adorners-how-to-topics.md)
