---
title: 自訂呈現筆墨
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
ms.openlocfilehash: 0ceb831057a9a92aa7319d2004f04d7cf5ac820e
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111825"
---
# <a name="custom-rendering-ink"></a><span data-ttu-id="84d79-102">自訂呈現筆墨</span><span class="sxs-lookup"><span data-stu-id="84d79-102">Custom Rendering Ink</span></span>
<span data-ttu-id="84d79-103">描<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>邊的屬性允許您指定描邊的外觀，例如其大小、顏色和形狀，但有時可能需要自訂超出<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>允許的外觀。</span><span class="sxs-lookup"><span data-stu-id="84d79-103">The <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property of a stroke allows you to specify the appearance of a stroke, such as its size, color, and shape, but there may be times that you want to customize the appearance beyond what <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> allow.</span></span> <span data-ttu-id="84d79-104">您可能想要自訂筆跡外觀，轉譯具噴槍、油畫及許多其他效果的外觀。</span><span class="sxs-lookup"><span data-stu-id="84d79-104">You may want to customize the appearance of ink by rendering in the appearance of an air brush, oil paint, and many other effects.</span></span> <span data-ttu-id="84d79-105">Windows 演示文稿基礎 （WPF） 允許您通過實現自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>和<xref:System.Windows.Ink.Stroke>物件來自訂渲染墨蹟。</span><span class="sxs-lookup"><span data-stu-id="84d79-105">The Windows Presentation Foundation (WPF) allows you to custom render ink by implementing a custom <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and <xref:System.Windows.Ink.Stroke> object.</span></span>  
  
 <span data-ttu-id="84d79-106">本主題包含下列子章節：</span><span class="sxs-lookup"><span data-stu-id="84d79-106">This topic contains the following subsections:</span></span>  
  
- [<span data-ttu-id="84d79-107">建築</span><span class="sxs-lookup"><span data-stu-id="84d79-107">Architecture</span></span>](#Architecture)  
  
- [<span data-ttu-id="84d79-108">實作動態轉譯器</span><span class="sxs-lookup"><span data-stu-id="84d79-108">Implementing a Dynamic Renderer</span></span>](#ImplementingADynamicRenderer)  
  
- [<span data-ttu-id="84d79-109">實作自訂筆劃</span><span class="sxs-lookup"><span data-stu-id="84d79-109">Implementing Custom Strokes</span></span>](#ImplementingCustomStrokes)  
  
- [<span data-ttu-id="84d79-110">實作自訂 InkCanvas</span><span class="sxs-lookup"><span data-stu-id="84d79-110">Implementing a Custom InkCanvas</span></span>](#ImplementingACustomInkCanvas)  
  
- [<span data-ttu-id="84d79-111">結論</span><span class="sxs-lookup"><span data-stu-id="84d79-111">Conclusion</span></span>](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a><span data-ttu-id="84d79-112">架構</span><span class="sxs-lookup"><span data-stu-id="84d79-112">Architecture</span></span>  
 <span data-ttu-id="84d79-113">當使用者在筆跡介面寫入筆跡，且在筆劃再次新增至啟用手寫功能的介面之後，筆跡轉譯出現兩次。</span><span class="sxs-lookup"><span data-stu-id="84d79-113">Ink rendering occurs two times; when a user writes ink to an inking surface, and again after the stroke is added to the ink-enabled surface.</span></span> <span data-ttu-id="84d79-114">當使用者<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>在數位化器上移動 Tablet 筆時，渲<xref:System.Windows.Ink.Stroke>染墨蹟，並在將 Tablet 筆添加到元素後渲染。</span><span class="sxs-lookup"><span data-stu-id="84d79-114">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renders the ink when the user moves the tablet pen on the digitizer, and the <xref:System.Windows.Ink.Stroke> renders itself once it is added to an element.</span></span>  
  
 <span data-ttu-id="84d79-115">動態轉譯筆跡時有三個類別要實作。</span><span class="sxs-lookup"><span data-stu-id="84d79-115">There are three classes to implement when dynamically rendering ink.</span></span>  
  
1. <span data-ttu-id="84d79-116">**動態呈現器**：實現派生自<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>的類。</span><span class="sxs-lookup"><span data-stu-id="84d79-116">**DynamicRenderer**: Implement a class that derives from <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span></span> <span data-ttu-id="84d79-117">此類是專門<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>化的，用於在繪製描邊時呈現筆劃。</span><span class="sxs-lookup"><span data-stu-id="84d79-117">This class is a specialized <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> that renders the stroke as it is drawn.</span></span> <span data-ttu-id="84d79-118">在<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>單獨的執行緒上執行渲染，因此，即使應用程式使用者介面 （UI） 執行緒被阻止，墨蹟表面也會顯示收集墨蹟。</span><span class="sxs-lookup"><span data-stu-id="84d79-118">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> does the rendering on a separate thread, so the inking surface appears to collect ink even when the application user interface (UI) thread is blocked.</span></span> <span data-ttu-id="84d79-119">如需執行緒模型的詳細資訊，請參閱[筆跡執行緒模型](the-ink-threading-model.md)。</span><span class="sxs-lookup"><span data-stu-id="84d79-119">For more information about the threading model, see [The Ink Threading Model](the-ink-threading-model.md).</span></span> <span data-ttu-id="84d79-120">要自訂動態渲染描邊，請重寫<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="84d79-120">To customize dynamically rendering a stroke, override the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> method.</span></span>  
  
2. <span data-ttu-id="84d79-121">**描邊**：實現派生自<xref:System.Windows.Ink.Stroke>的類。</span><span class="sxs-lookup"><span data-stu-id="84d79-121">**Stroke**: Implement a class that derives from <xref:System.Windows.Ink.Stroke>.</span></span> <span data-ttu-id="84d79-122">此類負責<xref:System.Windows.Input.StylusPoint>將資料轉換為<xref:System.Windows.Ink.Stroke>物件後靜態呈現資料。</span><span class="sxs-lookup"><span data-stu-id="84d79-122">This class is responsible for static rendering of the <xref:System.Windows.Input.StylusPoint> data after it has been converted into a <xref:System.Windows.Ink.Stroke> object.</span></span> <span data-ttu-id="84d79-123">重寫<xref:System.Windows.Ink.Stroke.DrawCore%2A>方法以確保描邊的靜態呈現與動態渲染一致。</span><span class="sxs-lookup"><span data-stu-id="84d79-123">Override the <xref:System.Windows.Ink.Stroke.DrawCore%2A> method to ensure that static rendering of the stroke is consistent with dynamic rendering.</span></span>  
  
3. <span data-ttu-id="84d79-124">**墨水畫布：** 實現派生自<xref:System.Windows.Controls.InkCanvas>的類。</span><span class="sxs-lookup"><span data-stu-id="84d79-124">**InkCanvas:** Implement a class that derives from <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="84d79-125">將自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>屬性分配給<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="84d79-125">Assign the customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> property.</span></span> <span data-ttu-id="84d79-126">重寫<xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A>方法並將自訂描邊添加到<xref:System.Windows.Controls.InkCanvas.Strokes%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="84d79-126">Override the <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> method and add a custom stroke to the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property.</span></span> <span data-ttu-id="84d79-127">這可確保筆跡外觀的一致。</span><span class="sxs-lookup"><span data-stu-id="84d79-127">This ensures that the appearance of the ink is consistent.</span></span>  
  
<a name="ImplementingADynamicRenderer"></a>
## <a name="implementing-a-dynamic-renderer"></a><span data-ttu-id="84d79-128">實作動態轉譯器</span><span class="sxs-lookup"><span data-stu-id="84d79-128">Implementing a Dynamic Renderer</span></span>  
 <span data-ttu-id="84d79-129">儘管<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>類是 的標準部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，但要執行更專用的渲染，則必須創建從 派生<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>並重寫<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>方法的自訂動態渲染器。</span><span class="sxs-lookup"><span data-stu-id="84d79-129">Although the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> class is a standard part of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], to perform more specialized rendering, you must create a customized dynamic renderer that derives from the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and override the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> method.</span></span>  
  
 <span data-ttu-id="84d79-130">下面的示例演示了使用線性<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>漸層筆刷效果繪製墨蹟的自訂。</span><span class="sxs-lookup"><span data-stu-id="84d79-130">The following example demonstrates a customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> that draws ink with a linear gradient brush effect.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>
## <a name="implementing-custom-strokes"></a><span data-ttu-id="84d79-131">實作自訂筆劃</span><span class="sxs-lookup"><span data-stu-id="84d79-131">Implementing Custom Strokes</span></span>  
 <span data-ttu-id="84d79-132">實作衍生自 <xref:System.Windows.Ink.Stroke> 的類別。</span><span class="sxs-lookup"><span data-stu-id="84d79-132">Implement a class that derives from <xref:System.Windows.Ink.Stroke>.</span></span> <span data-ttu-id="84d79-133">此類負責將資料轉換為<xref:System.Windows.Input.StylusPoint><xref:System.Windows.Ink.Stroke>物件後呈現資料。</span><span class="sxs-lookup"><span data-stu-id="84d79-133">This class is responsible for rendering <xref:System.Windows.Input.StylusPoint> data after it has been converted into a <xref:System.Windows.Ink.Stroke> object.</span></span> <span data-ttu-id="84d79-134">重寫類<xref:System.Windows.Ink.Stroke.DrawCore%2A>以執行實際繪圖。</span><span class="sxs-lookup"><span data-stu-id="84d79-134">Override the <xref:System.Windows.Ink.Stroke.DrawCore%2A> class to do the actual drawing.</span></span>  
  
 <span data-ttu-id="84d79-135">筆劃類還可以使用 方法<xref:System.Windows.Ink.Stroke.AddPropertyData%2A>存儲自訂資料。</span><span class="sxs-lookup"><span data-stu-id="84d79-135">Your Stroke class can also store custom data by using the <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> method.</span></span> <span data-ttu-id="84d79-136">保存此資料時會與筆劃資料一起儲存。</span><span class="sxs-lookup"><span data-stu-id="84d79-136">This data is stored with the stroke data when persisted.</span></span>  
  
 <span data-ttu-id="84d79-137">該<xref:System.Windows.Ink.Stroke>類還可以執行點擊測試。</span><span class="sxs-lookup"><span data-stu-id="84d79-137">The <xref:System.Windows.Ink.Stroke> class can also perform hit testing.</span></span> <span data-ttu-id="84d79-138">您還可以通過重寫當前類中<xref:System.Windows.Ink.Stroke.HitTest%2A>的方法來實現您自己的點擊測試演算法。</span><span class="sxs-lookup"><span data-stu-id="84d79-138">You can also implement your own hit testing algorithm by overriding the <xref:System.Windows.Ink.Stroke.HitTest%2A> method in the current class.</span></span>  
  
 <span data-ttu-id="84d79-139">以下 C# 代碼演示了<xref:System.Windows.Ink.Stroke>將<xref:System.Windows.Input.StylusPoint>資料呈現為 3D 描邊的自訂類。</span><span class="sxs-lookup"><span data-stu-id="84d79-139">The following C# code demonstrates a custom <xref:System.Windows.Ink.Stroke> class that renders <xref:System.Windows.Input.StylusPoint> data as a 3D stroke.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>
## <a name="implementing-a-custom-inkcanvas"></a><span data-ttu-id="84d79-140">實作自訂 InkCanvas</span><span class="sxs-lookup"><span data-stu-id="84d79-140">Implementing a Custom InkCanvas</span></span>  
 <span data-ttu-id="84d79-141">使用自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>和描邊的最簡單方法是實現派生並<xref:System.Windows.Controls.InkCanvas>使用這些類的類。</span><span class="sxs-lookup"><span data-stu-id="84d79-141">The easiest way to use your customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and stroke is to implement a class that derives from <xref:System.Windows.Controls.InkCanvas> and uses these classes.</span></span> <span data-ttu-id="84d79-142">具有<xref:System.Windows.Controls.InkCanvas>一個<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>屬性，用於指定在使用者繪製描邊時如何呈現筆劃。</span><span class="sxs-lookup"><span data-stu-id="84d79-142">The <xref:System.Windows.Controls.InkCanvas> has a <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> property that specifies how the stroke is rendered when the user is drawing it.</span></span>  
  
 <span data-ttu-id="84d79-143">要在 操作<xref:System.Windows.Controls.InkCanvas>上自訂渲染描邊，可以執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="84d79-143">To custom render strokes on an <xref:System.Windows.Controls.InkCanvas> do the following:</span></span>  
  
- <span data-ttu-id="84d79-144">創建派生自 的<xref:System.Windows.Controls.InkCanvas>類。</span><span class="sxs-lookup"><span data-stu-id="84d79-144">Create a class that derives from the <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
- <span data-ttu-id="84d79-145">將自訂屬性<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>分配給屬性<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="84d79-145">Assign your customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="84d79-146">覆寫 <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="84d79-146">Override the <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> method.</span></span> <span data-ttu-id="84d79-147">在此方法中，移除已新增至 InkCanvas 的原始筆劃。</span><span class="sxs-lookup"><span data-stu-id="84d79-147">In this method, remove the original stroke that was added to the InkCanvas.</span></span> <span data-ttu-id="84d79-148">然後創建自訂描邊，將其添加到屬性，<xref:System.Windows.Controls.InkCanvas.Strokes%2A>然後用包含自訂描邊的新項<xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs>調用基類。</span><span class="sxs-lookup"><span data-stu-id="84d79-148">Then create a custom stroke, add it to the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property, and call the base class with a new <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> that contains the custom stroke.</span></span>  
  
 <span data-ttu-id="84d79-149">以下 C# 代碼演示了<xref:System.Windows.Controls.InkCanvas>使用自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>和收集自訂描邊的自訂類。</span><span class="sxs-lookup"><span data-stu-id="84d79-149">The following C# code demonstrates a custom <xref:System.Windows.Controls.InkCanvas> class that uses a customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and collects custom strokes.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <span data-ttu-id="84d79-150">可以<xref:System.Windows.Controls.InkCanvas>有多個<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。</span><span class="sxs-lookup"><span data-stu-id="84d79-150">An <xref:System.Windows.Controls.InkCanvas> can have more than one <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span></span> <span data-ttu-id="84d79-151">通過將多個物件添加到<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer><xref:System.Windows.UIElement.StylusPlugIns%2A>屬性，<xref:System.Windows.Controls.InkCanvas>可以向 添加多個物件。</span><span class="sxs-lookup"><span data-stu-id="84d79-151">You can add multiple <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objects to the <xref:System.Windows.Controls.InkCanvas> by adding them to the <xref:System.Windows.UIElement.StylusPlugIns%2A> property.</span></span>  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a><span data-ttu-id="84d79-152">結論</span><span class="sxs-lookup"><span data-stu-id="84d79-152">Conclusion</span></span>  
 <span data-ttu-id="84d79-153">您可以通過派生自己的<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>和<xref:System.Windows.Ink.Stroke><xref:System.Windows.Controls.InkCanvas>類來自訂墨蹟的外觀。</span><span class="sxs-lookup"><span data-stu-id="84d79-153">You can customize the appearance of ink by deriving your own <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>, and <xref:System.Windows.Controls.InkCanvas> classes.</span></span> <span data-ttu-id="84d79-154">當使用者繪製並收集筆劃後，這些類別可合力確保筆劃外觀的一致。</span><span class="sxs-lookup"><span data-stu-id="84d79-154">Together, these classes ensure that the appearance of the stroke is consistent when the user draws the stroke and after it is collected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84d79-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84d79-155">See also</span></span>

- [<span data-ttu-id="84d79-156">筆墨進階處理</span><span class="sxs-lookup"><span data-stu-id="84d79-156">Advanced Ink Handling</span></span>](advanced-ink-handling.md)
