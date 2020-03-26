---
title: 裝飾項概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b41c1f10f7e1b7c1799fd27270a3eeb9899ceeb6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111175"
---
# <a name="adorners-overview"></a><span data-ttu-id="40fd3-102">裝飾項概觀</span><span class="sxs-lookup"><span data-stu-id="40fd3-102">Adorners Overview</span></span>

<span data-ttu-id="40fd3-103">裝飾器是一種特殊的類型<xref:System.Windows.FrameworkElement>，用於向使用者提供視覺提示。</span><span class="sxs-lookup"><span data-stu-id="40fd3-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="40fd3-104">除了其他用法，裝飾項還可用來將功能控點加入項目，或提供控制項的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="40fd3-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>

## <a name="about-adorners"></a><span data-ttu-id="40fd3-105">關於裝飾項</span><span class="sxs-lookup"><span data-stu-id="40fd3-105">About Adorners</span></span>

<span data-ttu-id="40fd3-106">是<xref:System.Windows.Documents.Adorner>綁定到<xref:System.Windows.FrameworkElement>的<xref:System.Windows.UIElement>自訂項。</span><span class="sxs-lookup"><span data-stu-id="40fd3-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="40fd3-107">裝飾器以 中呈現<xref:System.Windows.Documents.AdornerLayer>，這是始終位於修飾元素或修飾元素集合之上的呈現曲面。</span><span class="sxs-lookup"><span data-stu-id="40fd3-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="40fd3-108">修飾器的渲染獨立于修飾器綁定到的<xref:System.Windows.UIElement>渲染。</span><span class="sxs-lookup"><span data-stu-id="40fd3-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="40fd3-109">裝飾器通常相對於綁定的元素進行定位，使用位於修飾元素左上角的標準 2D 座標原點。</span><span class="sxs-lookup"><span data-stu-id="40fd3-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2D coordinate origin located at the upper-left of the adorned element.</span></span>

<span data-ttu-id="40fd3-110">裝飾項的常見應用包括︰</span><span class="sxs-lookup"><span data-stu-id="40fd3-110">Common applications for adorners include:</span></span>

- <span data-ttu-id="40fd3-111">將功能控制碼添加到<xref:System.Windows.UIElement>，使使用者能夠以某種方式操作元素（調整大小、旋轉、重新置放等）。</span><span class="sxs-lookup"><span data-stu-id="40fd3-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>
- <span data-ttu-id="40fd3-112">提供視覺化回應以表示各種狀態，或回應各種事件。</span><span class="sxs-lookup"><span data-stu-id="40fd3-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>
- <span data-ttu-id="40fd3-113">在 上疊加視覺裝飾<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="40fd3-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>
- <span data-ttu-id="40fd3-114">直觀地遮罩或覆蓋 部分或 全部<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="40fd3-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="40fd3-115">提供基本的架構以便裝飾視覺項目。</span><span class="sxs-lookup"><span data-stu-id="40fd3-115">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="40fd3-116">下表列出在裝飾物件時所使用的主要類型，及其用途。</span><span class="sxs-lookup"><span data-stu-id="40fd3-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="40fd3-117">以下幾個使用示例如下：</span><span class="sxs-lookup"><span data-stu-id="40fd3-117">Several usage examples follow:</span></span>

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="40fd3-118">抽象基底類別，所有具體裝飾項實作都繼承自該類別。</span><span class="sxs-lookup"><span data-stu-id="40fd3-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="40fd3-119">代表一個或多個裝飾項目的裝飾項轉譯層的類別。</span><span class="sxs-lookup"><span data-stu-id="40fd3-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="40fd3-120">可讓裝飾項層與項目集合相關聯的類別。</span><span class="sxs-lookup"><span data-stu-id="40fd3-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|

## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="40fd3-121">實作自訂裝飾項</span><span class="sxs-lookup"><span data-stu-id="40fd3-121">Implementing a Custom Adorner</span></span>

<span data-ttu-id="40fd3-122">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]　提供的裝飾項架構主要是為了支援建立自訂裝飾項。</span><span class="sxs-lookup"><span data-stu-id="40fd3-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="40fd3-123">自訂修飾器是通過實現從抽象<xref:System.Windows.Documents.Adorner>類繼承的類創建的。</span><span class="sxs-lookup"><span data-stu-id="40fd3-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>

> [!NOTE]
> <span data-ttu-id="40fd3-124">的父<xref:System.Windows.Documents.Adorner>級是<xref:System.Windows.Documents.AdornerLayer>呈現 的<xref:System.Windows.Documents.Adorner>， 而不是正在修飾的元素。</span><span class="sxs-lookup"><span data-stu-id="40fd3-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>

<span data-ttu-id="40fd3-125">下列範例顯示一個實作簡單裝飾項的類別。</span><span class="sxs-lookup"><span data-stu-id="40fd3-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="40fd3-126">示例修飾器只是修飾帶有圓圈的角<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="40fd3-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
<span data-ttu-id="40fd3-127">下圖顯示了應用於 的<xref:System.Windows.Controls.TextBox>SimpleCircleAdorner：</span><span class="sxs-lookup"><span data-stu-id="40fd3-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>:</span></span>

![顯示修飾文字方塊的螢幕截圖。](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="40fd3-129">裝飾項的轉譯行為</span><span class="sxs-lookup"><span data-stu-id="40fd3-129">Rendering Behavior for Adorners</span></span>

<span data-ttu-id="40fd3-130">請務必注意，裝飾項並不包括任何繼承的轉譯行為。裝飾項實作者必須負責確定裝飾項轉譯器。</span><span class="sxs-lookup"><span data-stu-id="40fd3-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span> <span data-ttu-id="40fd3-131">實現呈現行為的常見方法是重寫<xref:System.Windows.UIElement.OnRender%2A>該方法，並使用一個或多個<xref:System.Windows.Media.DrawingContext>物件根據需要呈現修飾器的視覺效果（如上例所示）。</span><span class="sxs-lookup"><span data-stu-id="40fd3-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>

> [!NOTE]
> <span data-ttu-id="40fd3-132">放在裝飾項圖層中的任何項目會轉譯在您已設定的其餘任何樣式之上。</span><span class="sxs-lookup"><span data-stu-id="40fd3-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="40fd3-133">換句話說，裝飾項永遠是以視覺化方式在最上面，而且無法使用疊置順序覆寫。</span><span class="sxs-lookup"><span data-stu-id="40fd3-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>

## <a name="events-and-hit-testing"></a><span data-ttu-id="40fd3-134">事件和點擊測試</span><span class="sxs-lookup"><span data-stu-id="40fd3-134">Events and Hit Testing</span></span>

<span data-ttu-id="40fd3-135">修飾器接收輸入事件就像任何其他<xref:System.Windows.FrameworkElement>一樣。</span><span class="sxs-lookup"><span data-stu-id="40fd3-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="40fd3-136">由於修飾器的 z 順序始終高於其修飾的元素，因此修飾器接收可能用於基礎修飾元素的輸入事件（如<xref:System.Windows.UIElement.Drop><xref:System.Windows.UIElement.MouseMove>或 ）。</span><span class="sxs-lookup"><span data-stu-id="40fd3-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="40fd3-137">裝飾項可以接聽特定的輸入事件，並藉由重新引發事件將它們傳送到基礎的被裝飾項目。</span><span class="sxs-lookup"><span data-stu-id="40fd3-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>

<span data-ttu-id="40fd3-138">要啟用修飾器下元素的直通點擊測試，將點擊測試<xref:System.Windows.UIElement.IsHitTestVisible%2A>屬性設置為修飾器上的**false。**</span><span class="sxs-lookup"><span data-stu-id="40fd3-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="40fd3-139">有關點擊測試的詳細資訊，請參閱[視覺化圖層中的點擊測試](../graphics-multimedia/hit-testing-in-the-visual-layer.md)。</span><span class="sxs-lookup"><span data-stu-id="40fd3-139">For more information about hit testing, see [Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>

## <a name="adorning-a-single-uielement"></a><span data-ttu-id="40fd3-140">裝飾單一的 UIElement</span><span class="sxs-lookup"><span data-stu-id="40fd3-140">Adorning a Single UIElement</span></span>

<span data-ttu-id="40fd3-141">要將裝飾器綁定到特定<xref:System.Windows.UIElement>，請按照以下步驟操作：</span><span class="sxs-lookup"><span data-stu-id="40fd3-141">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>

1. <span data-ttu-id="40fd3-142">調用靜態方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>獲取<xref:System.Windows.Documents.AdornerLayer><xref:System.Windows.UIElement>要修飾的物件。</span><span class="sxs-lookup"><span data-stu-id="40fd3-142">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="40fd3-143"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>向上走，從指定的<xref:System.Windows.UIElement>開始，然後返回它找到的第一個修飾器圖層。</span><span class="sxs-lookup"><span data-stu-id="40fd3-143"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="40fd3-144">(如果找不到任何裝飾項圖層，方法會傳回 null。)</span><span class="sxs-lookup"><span data-stu-id="40fd3-144">(If no adorner layers are found, the method returns null.)</span></span>

2. <span data-ttu-id="40fd3-145">調用<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法將修飾器綁定到目標<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="40fd3-145">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>

 <span data-ttu-id="40fd3-146">下面的示例將 SimpleCircleAdorner（如上圖所示）綁定到<xref:System.Windows.Controls.TextBox>名為*myTextBox ：*</span><span class="sxs-lookup"><span data-stu-id="40fd3-146">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*:</span></span>

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> <span data-ttu-id="40fd3-147">使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。</span><span class="sxs-lookup"><span data-stu-id="40fd3-147">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>

## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="40fd3-148">裝飾 Panel 的子系</span><span class="sxs-lookup"><span data-stu-id="40fd3-148">Adorning the Children of a Panel</span></span>

<span data-ttu-id="40fd3-149">要將裝飾器綁定到 子級<xref:System.Windows.Controls.Panel>，請按照以下步驟操作：</span><span class="sxs-lookup"><span data-stu-id="40fd3-149">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>

1. <span data-ttu-id="40fd3-150">調用`static`方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>查找要修飾其子項目的元素的修飾器圖層。</span><span class="sxs-lookup"><span data-stu-id="40fd3-150">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>

2. <span data-ttu-id="40fd3-151">通過父元素的子項目枚舉，<xref:System.Windows.Documents.AdornerLayer.Add%2A>並調用 方法將修飾器綁定到每個子項目。</span><span class="sxs-lookup"><span data-stu-id="40fd3-151">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>

<span data-ttu-id="40fd3-152">下面的示例將 SimpleCircleAdorner（如上圖所示）綁定到<xref:System.Windows.Controls.StackPanel>名為*myStackPanel*的子級：</span><span class="sxs-lookup"><span data-stu-id="40fd3-152">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*:</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a><span data-ttu-id="40fd3-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40fd3-153">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="40fd3-154">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="40fd3-154">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="40fd3-155">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="40fd3-155">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="40fd3-156">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="40fd3-156">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="40fd3-157">如何使用主題</span><span class="sxs-lookup"><span data-stu-id="40fd3-157">How-to Topics</span></span>](adorners-how-to-topics.md)
